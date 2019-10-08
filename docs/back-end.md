## Project Structure

The main idea behind the project structure is the separation of concerns.

Main principles to follow;

- Routers should be clean and version friendly. They call handlers from corresponding API version.
- Handlers are only responsible for specifying processing steps. They should not contain / depend any implementation details about database or models (if possible).
- Database operations should be abstract to the rest of the system except handlers. That way database changing costs could be minimal.
- Model related data structures should be separated.

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

    GET /users?IsPublic=true

Will return only users with public profile.

---

**Sorting**

For any sortable resource there will be query for sorting.

For example;

    GET /books?sortDescending=PrintDate

Will return latest (30) printed books.

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
