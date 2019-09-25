## Project Structure

---

## Versioning

---

## Response Codes

---

## Endpoint Naming Strategy

REST URLs will follow this main structure;

    /apiVersion/resource/:id/:subResource/:subResourceID

For example;

| Resource | POST | GET | PUT | DELETE |
|--|--|--|--|--|
| v1/users | Creates new user. | Returns user list. | Method not allowed. (405) | Method not allowed. (405) |
| v1/books/1 | Method not allowed. (405) | Returns book info. | Updates book info. | Removes book. |

---

**Filtering**

For any filterable resource there will be filter query.

For example;

    GET v1/users?IsPublic=true

Will return only users with public profile.

---

**Sorting**

For any sortable resource there will be query for sorting.

For example;

    GET v1/books?sortDescending=PrintDate

Will return latest (30) printed books.

---

**Paging**

Default page size is 30 items. (This can be changed in the implementation.)

Example;

    GET v1/books?sortDescending=PrintDate&page=2

Will return 2nd latest 30 books.

---

Detailed URL list can be found in [Endpoints](#endpoints) section.

---

## Authentication

---

## Authorization

---

## Database

---

## Endpoints
