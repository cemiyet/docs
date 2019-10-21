## Project Structure

The main idea behind the project structure is the separation of concerns.

Main principles to follow;

- API controllers are only responsible for specifying processing steps. They should not contain or depend any implementation details about database or models.
- Database-related operations should be abstracted from the rest of the system. That way database changing costs could be minimal.
- Model related data structures should be separated.

With these principles in mind there will be 6 seperate projects;

| Project | Contents | References |
|--|--|--|
| Core [Class Library] | Models, Exceptions, Interfaces | - |
| Persistence [Class Library] | Database-related operations for both api and external services | Domain |
| Infrastructure [Class Library] | External services (like notification, stmp, logging etc.) | Domain, Persistence |
| Application [Class Library] | Application logic | Domain, Persistence, Infrastructure |
| Api [Web Api Project] | Controllers (get request and return response) | Application |
| Tests [Class Library] | Unit tests, integration tests etc. | Api |

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

Default page size is 30 items. (This can be changed in the implementation.)

Example;

    GET /books?sortDescending=PrintDate&page=2

Will return 2nd latest 30 books.

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

**Dimensions**

dimension_id : uuid  
page : int  
dimension_ids: uuid array

| Method | Endpoint |
|--|--|
| POST | /dimensions |
| GET | /dimensions |
| GET | /dimensions?page={{page}} |
| GET | /dimensions/{{dimension_id}} |
| PUT | /dimensions/{{dimension_id}} |
| PATCH | /dimensions/{{dimension_id}} |
| DELETE | /dimensions/{{dimension_id}} |
| DELETE | /dimensions/{{dimension_ids}} |

**Genres**

genre_id : uuid  
page : int  
genre_ids: uuid array

| Method | Endpoint |
|--|--|
| POST | /genres |
| GET | /genres |
| GET | /genres?page={{page}} |
| GET | /genres/{{genre_id}} |
| PUT | /genres/{{genre_id}} |
| PATCH | /genres/{{genre_id}} |
| DELETE | /genres/{{genre_id}} |
| DELETE | /genres/{{genre_ids}} |

**Authors**

author_id : uuid  
page : int  
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
| DELETE | /authors/{{author_ids}} |

**Publishers**

publisher_id : uuid  
page : int  
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
| DELETE | /publishers/{{publisher_ids}} |

**EditorsPublishers**

publisher_id : uuid  
editor_id : uuid (user id)  
editor_ids: uuid array (user ids)  

| Method | Endpoint |
|--|--|
| POST | /publishers/{{publisher_id}}/editors |
| GET | /publishers/{{publisher_id}}/editors |
| DELETE | /publishers/{{publisher_id}}/editors/{{editor_id}} |
| DELETE | /publishers/{{publisher_id}}/editors/{{editor_ids}} |

**EditorsAuthors**

author_id : uuid  
editor_id : uuid (user id)  
editor_ids: uuid array (user ids)  

| Method | Endpoint |
|--|--|
| POST | /authors/{{author_id}}/editors |
| GET | /authors/{{author_id}}/editors |
| DELETE | /authors/{{author_id}}/editors/{{editor_id}} |
| DELETE | /authors/{{author_id}}/editors/{{editor_ids}} |

**EditorsGenres**

genre_id : uuid  
editor_id : uuid (user id)  
editor_ids: uuid array (user ids)  

| Method | Endpoint |
|--|--|
| POST | /genres/{{genre_id}}/editors |
| GET | /genres/{{genre_id}}/editors |
| DELETE | /genres/{{genre_id}}/editors/{{editor_id}} |
| DELETE | /genres/{{genre_id}}/editors/{{editor_ids}} |
