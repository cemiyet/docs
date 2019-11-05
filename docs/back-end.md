## Project Structure

The main idea behind the project structure is the separation of concerns.

Main principles to follow;

- API controllers are only responsible for specifying processing steps. They should not contain or depend any implementation details about database or models.
- Database-related operations should be abstracted from the rest of the system. That way database changing costs could be minimal.
- Model related data structures should be separated.

With these principles in mind there will be 10 seperate projects;

| Project | Contents | References |
|--|--|--|
| Core [Class Library] | Models, Exceptions, Interfaces | - |
| Core.Tests [xUnit Test Project] | Tests for Core library | Core |
| Persistence [Class Library] | Database-related operations for both api and external services | Domain |
| Persistence.Tests [xUnit Test Project] | Tests for Persistence library | Persistence |
| Infrastructure [Class Library] | External services (like notification, stmp, logging etc.) | Domain, Persistence |
| Infrastructure.Tests [xUnit Test Project] | Tests for Infrastructure library | Infrastructure |
| Application [Class Library] | Application logic | Domain, Persistence, Infrastructure |
| Application.Tests [xUnit Test Project] | Tests for Application library | Application |
| Api [Web Api Project] | Controllers (get request and return response) | Application |
| Api.Tests [xUnit Test Project] | Tests for Api project | Api |

---

## Versioning

Project will follow rolling release concept.

---

## Response Codes

| Code | Use Cases |
|--|--|
| 200 OK | Response to a successful GET, PUT, PATCH or DELETE requests. |
| 201 Created | Response to a successful POST request which results in a creation. |
| 204 No Content | Response to a successful request which doesn't have body. |
| 304 Not Modified ❓ | Useful when HTTP caching is present. (Not yet planned.) |
| 400 Bad Request | Response to an unsuccessful request with bad data. |
| 401 Unauthorized | Response to an unsuccessful request with invalid authentication. |
| 403 Forbidden | Response to an unsuccessful request with valid authentication but with invalid authorization. |
| 404 Not Found | Response to an unsuccessful request made to unknown endpoint. |
| 405 Method Not Allowed | Response to an unsuccessful request which isn't allowed for authenticated user. |
| 410 Gone | Response to an unsuccessful request made to endpoint that no longer available. |
| 415 Unsupported Media Type | Response to an unsuccessful request with incorrect content type. |
| 429 Too Many Requests ❓ | Useful when the request rejected due to rate limiting. (Not yet planned.) |

---

## Endpoint Naming Strategy

Endpoints will follow this main structure;

    /resource/:id/:subResource/:subResourceID

For example;

| Resource | POST | GET | PUT (replacing) | PATCH (partial update) | DELETE |
|--|--|--|--|--|--|
| /users | Creates new user. | Returns user list. | Method not allowed. (405) | Method not allowed. (405) | Method not allowed. (405) |
| /books/1 | Method not allowed. (405) | Returns book info. | Replaces book info. | Updates book info. | Removes book. |

---

**Filtering**

For any filterable resource there will be filter query.

For example;

    GET /users?is_public=true

Will return only users with public profile.

---

**Paging**

Default page is 1 and page size is 30 items.

Example;

    GET /genres?page=2&pageSize=5

Will skip first 5 genres and return 2nd 5 genres.

---

Detailed endpoint list can be found in [Endpoints](#endpoints) section.

---

## Authentication

When the user successfully logs in using their credentials, a JSON Web Token will be returned.

Then authenticated requests should feature Authorization header using the Bearer schema;

    Authorization: Bearer <token>

---

## Authorization

Main authorization model is role based using JWT claims until MVP.

After MVP more complex authorization system should be a way to go.

---

## Database

PostgreSQL 12 will be main choice until MVP.

---

## Endpoints

This section will be replaced eventually by API documentation.

Cemiyet and event related endpoints will be added prior to their update.

**Update:** Implemented endpoints: [API Docs](/cemiyet/api-docs).

---

**Work In Progress**

**Genres**

genre_id: uuid  
page: int  
pageSize: int

| Method | Endpoint |
|--|--|
| GET | /genres/{{genre_id}}/books |
| GET | /genres/{{genre_id}}/books?page={{page}}&pageSize={{pageSize}} |

**Authors**

author_id: uuid  
page: int  
author_ids: uuid array

| Method | Endpoint |
|--|--|
| POST | /authors |
| GET | /authors |
| GET | /authors?page={{page}} |
| GET | /authors/{{author_id}} |
| PUT | /authors/{{author_id}} |
| PATCH | /authors/{{author_id}} |
| DELETE | /authors/{{author_id}} |
| DELETE | /authors?author_ids={{author_ids}} |
| GET | /authors/{{author_id}}/books |
| GET | /authors/{{author_id}}/books?page={{page}} |
| GET | /authors/{{author_id}}/series |
| GET | /authors/{{author_id}}/series?page={{page}} |

**Publishers**

publisher_id: uuid  
page: int  
publisher_ids: uuid array

| Method | Endpoint |
|--|--|
| POST | /publishers |
| GET | /publishers |
| GET | /publishers?page={{page}} |
| GET | /publishers/{{publisher_id}} |
| PUT | /publishers/{{publisher_id}} |
| PATCH | /publishers/{{publisher_id}} |
| DELETE | /publishers/{{publisher_id}} |
| DELETE | /publishers?publisher_ids={{publisher_ids}} |
| GET | /publishers/{{publisher_id}}/books |
| GET | /publishers/{{publisher_id}}/books?page={{page}} |

**Books**

book_id: uuid  
page: int  
book_isbn: char(13)  
book_ids: uuid array  
book_isbns: char(13) array

| Method | Endpoint |
|--|--|
| POST | /books |
| GET | /books |
| GET | /books?page={{page}} |
| GET | /books/{{book_id}} |
| PUT | /books/{{book_id}} |
| PATCH | /books/{{book_id}} |
| DELETE | /books/{{book_id}} |
| DELETE | /books?book_ids={{book_ids}} |
| POST | /books/{{book_id}}/editions |
| GET | /books/{{book_id}}/editions |
| GET | /books/{{book_id}}/editions?page={{page}} |
| GET | /books/{{book_id}}/editions/{{book_isbn}} |
| PUT | /books/{{book_id}}/editions/{{book_isbn}} |
| PATCH | /books/{{book_id}}/editions/{{book_isbn}} |
| DELETE | /books/{{book_id}}/editions/{{book_isbn}} |
| DELETE | /books/{{book_id}}/editions?book_isbns={{book_isbns}} |

**Series**

serie_id: uuid  
page: int  
book_id: uuid  
book_ids: uuid array

| Method | Endpoint |
|--|--|
| POST | /series |
| GET | /series |
| GET | /series?page={{page}} |
| GET | /series/{{serie_id}} |
| PUT | /series/{{serie_id}} |
| PATCH | /series/{{serie_id}} |
| DELETE | /series/{{serie_id}} |
| DELETE | /series?serie_ids={{serie_ids}} |
| POST | /series/{{serie_id}}/books |
| GET | /series/{{serie_id}}/books |
| GET | /series/{{serie_id}}/books?page={{page}} |
| GET | /series/{{serie_id}}/books/{{book_id}} |
| DELETE | /series/{{serie_id}}/books/{{book_id}} |
| DELETE | /series/{{serie_id}}/books?book_ids={{book_ids}} |

**Users**

user_id: uuid  
page: int  
user_ids: uuid array  

| Method | Endpoint |
|--|--|
| POST | /register |
| POST | /login |
| POST | /logout |
| POST | /users |
| GET | /users |
| GET | /users?page={{page}} |
| GET | /users/{{user_id}} |
| PUT | /users/{{user_id}} |
| PATCH | /users/{{user_id}} |
| DELETE | /users/{{user_id}} |
| DELETE | /users?user_ids={{user_ids}} |
| GET | /me |
| PUT | /me |
| PATCH | /me |
| DELETE | /me |

**UsersBooks**

user_id: uuid  
page: int  
book_isbn: char(13)  
book_isbns: char(13) array

| Method | Endpoint |
|--|--|
| POST | /me/books |
| GET | /me/books |
| GET | /me/books?page={{page}} |
| PUT | /me/books |
| DELETE | /me/books/{{book_isbn}} |
| DELETE | /me/books?book_isbns={{book_isbns}} |
| POST | /users/{{user_id}}/books |
| GET | /users/{{user_id}}/books |
| GET | /users/{{user_id}}/books?page={{page}} |
| PUT | /users/{{user_id}}/books |
| DELETE | /users/{{user_id}}/books/{{book_isbn}} |
| DELETE | /users/{{user_id}}/books?book_isbns={{book_isbns}} |

**UsersBooksTags**

user_id: uuid  
page: int  
book_id: char(13)  
tag_ids: char(13) array

| Method | Endpoint |
|--|--|
| POST | /me/books/{{book_id}}/tags |
| GET | /me/books/{{book_id}}/tags |
| PUT | /me/books/{{book_id}}/tags |
| DELETE | /me/books/{{book_id}}/tags |
| DELETE | /me/books/{{book_id}}/tags?tag_ids={{tag_ids}} |
| POST | /users/{{user_id}}/books/{{book_id}}/tags |
| GET | /users/{{user_id}}/books/{{book_id}}/tags |
| PUT | /users/{{user_id}}/books/{{book_id}}/tags |
| DELETE | /users/{{user_id}}/books/{{book_id}}/tags |
| DELETE | /users/{{user_id}}/books/{{book_id}}/tags?tag_ids={{tag_ids}} |

**UsersLists**

user_id: uuid  
page: int  
list_id: uuid  
list_ids: uuid array

| Method | Endpoint |
|--|--|
| POST | /me/lists |
| GET | /me/lists |
| GET | /me/lists?page={{page}} |
| GET | /me/lists/{{list_id}} |
| PUT | /me/lists/{{list_id}} |
| DELETE | /me/lists/{{list_id}} |
| DELETE | /me/lists?list_ids={{list_ids}} |
| POST | /users/{{user_id}}/lists |
| GET | /users/{{user_id}}/lists |
| GET | /users/{{user_id}}/lists?page={{page}} |
| GET | /users/{{user_id}}/lists/{{list_id}} |
| PUT | /users/{{user_id}}/lists/{{list_id}} |
| DELETE | /users/{{user_id}}/lists/{{list_id}} |
| DELETE | /users/{{user_id}}/lists?list_ids={{list_ids}} |

**UsersListsBooks**

user_id: uuid  
page: int  
list_id: uuid  
book_isbn: char(13)  
book_isbns: char(13) array

| Method | Endpoint |
|--|--|
| POST | /me/lists/{{list_id}}/books |
| GET | /me/lists/{{list_id}}/books |
| GET | /me/lists/{{list_id}}/books?page={{page}} |
| GET | /me/lists/{{list_id}}/books/{{book_isbn}} |
| DELETE | /me/lists/{{list_id}}/books/{{book_isbn}} |
| DELETE | /me/lists/{{list_id}}/books?book_isbns={{book_isbns}} |
| POST | /users/{{user_id}}/lists/{{list_id}}/books |
| GET | /users/{{user_id}}/lists/{{list_id}}/books |
| GET | /users/{{user_id}}/lists/{{list_id}}/books?page={{page}} |
| GET | /users/{{user_id}}/lists/{{list_id}}/books/{{book_isbn}} |
| DELETE | /users/{{user_id}}/lists/{{list_id}}/books/{{book_isbn}} |
| DELETE | /users/{{user_id}}/lists/{{list_id}}/books?book_isbns={{book_isbns}} |

**UsersTags**

user_id: uuid  
page: int  
tag_id: uuid  
tag_ids: uuid array

| Method | Endpoint |
|--|--|
| POST | /me/tags |
| GET | /me/tags |
| GET | /me/tags?page={{page}} |
| GET | /me/tags/{{tag_id}} |
| PUT | /me/tags/{{tag_id}} |
| DELETE | /me/tags/{{tag_id}} |
| DELETE | /me/tags?tag_ids={{tag_ids}} |
| POST | /users/{{user_id}}/tags |
| GET | /users/{{user_id}}/tags |
| GET | /users/{{user_id}}/tags?page={{page}} |
| GET | /users/{{user_id}}/tags/{{tag_id}} |
| PUT | /users/{{user_id}}/tags/{{tag_id}} |
| DELETE | /users/{{user_id}}/tags/{{tag_id}} |
| DELETE | /users/{{user_id}}/tags?tag_ids={{tag_ids}} |

**UsersTagsBooks**

user_id: uuid  
page: int  
tag_id: uuid  
book_id: char(13)  
book_ids: char(13) array

| Method | Endpoint |
|--|--|
| POST | /me/tags/{{tag_id}}/books |
| GET | /me/tags/{{tag_id}}/books |
| GET | /me/tags/{{tag_id}}/books?page={{page}} |
| GET | /me/tags/{{tag_id}}/books/{{book_id}} |
| DELETE | /me/tags/{{tag_id}}/books/{{book_id}} |
| DELETE | /me/tags/{{tag_id}}/books?book_ids={{book_ids}} |
| POST | /users/{{user_id}}/tags/{{tag_id}}/books |
| GET | /users/{{user_id}}/tags/{{tag_id}}/books |
| GET | /users/{{user_id}}/tags/{{tag_id}}/books?page={{page}} |
| GET | /users/{{user_id}}/tags/{{tag_id}}/books/{{book_id}} |
| DELETE | /users/{{user_id}}/tags/{{tag_id}}/books/{{book_id}} |
| DELETE | /users/{{user_id}}/tags/{{tag_id}}/books?book_ids={{book_ids}} |

**EditorsPublishers**

publisher_id: uuid  
editor_id: uuid (user id)  
editor_ids: uuid array (user ids)

| Method | Endpoint |
|--|--|
| POST | /publishers/{{publisher_id}}/editors |
| GET | /publishers/{{publisher_id}}/editors |
| DELETE | /publishers/{{publisher_id}}/editors/{{editor_id}} |
| DELETE | /publishers/{{publisher_id}}/editors?editor_ids={{editor_ids}} |

**EditorsAuthors**

author_id : uuid  
editor_id : uuid (user id)  
editor_ids: uuid array (user ids)

| Method | Endpoint |
|--|--|
| POST | /authors/{{author_id}}/editors |
| GET | /authors/{{author_id}}/editors |
| DELETE | /authors/{{author_id}}/editors/{{editor_id}} |
| DELETE | /authors/{{author_id}}/editors?editor_ids={{editor_ids}} |

**EditorsGenres**

genre_id : uuid  
editor_id : uuid (user id)  
editor_ids: uuid array (user ids)

| Method | Endpoint |
|--|--|
| POST | /genres/{{genre_id}}/editors |
| GET | /genres/{{genre_id}}/editors |
| DELETE | /genres/{{genre_id}}/editors/{{editor_id}} |
| DELETE | /genres/{{genre_id}}/editors?editor_ids={{editor_ids}} |
