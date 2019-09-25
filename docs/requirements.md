## Actors

| Actor | Assets |
|--|--|
| 👻 **Guest** | nothing. |
| 👤 **User** | *book lists* |
| 👤 **Author** | *books*, *followers*, *events* ❓, *publishers* ❓ |
| 👥 **Publisher** 💶 | *books*, *authors*, *followers*, *events* ❓ |
| 👥 **Dealer** 💶❓ | *book links* |
| 👥 **Editor** | *change records* ❓ |
| 👥 **Admin** | *change records* ❓ |

**Actor Authorities**

| Actor | Authorities |
|--|--|
| 👥 **Dealer** 💶❓ | edit links to books |
| 👥 **Publisher** 💶 | edit books, book series, authors, events ❓ |
| 👥 **Editor** | edit particular books (by genre, by author) |
| 👥 **Admin** | edit all kind of data and manage editors |

---

## Requirements

Below are fundamental requirements per actor.

Their purpose is to create a reference material for features.

Status: Feature frozen until v0.6. New iteration will be held after the *Ratings & Lists* update.

---

As a 👻 **Guest**:

| I want to... | Notes | Status |
|--|--|--|
| Sign-up with my username, date of birth, email and password. |   | TO DO |
| Search a book by it's title. |   | TO DO |
| Search an author by name. |   | TO DO |
| Search a publisher by it's name.  |   | TO DO |
| Search an user by it's username.  |   | TO DO |
| See user profile.  | User profile must be public. | TO DO |
| See book detail page.  |   | TO DO |
| See author detail page.  |   | TO DO |
| See publisher detail page.  |   | TO DO |

---

As an 👤 **User**:

Same as <u>*Guest*</u>, plus;

| I want to... | Notes | Status |
|--|--|--|
| Sign-in with my username/email and password. |   | TO DO |
| Search a book by it's isbn/barcode. |   | TO DO |
| Filter search results. |   | TO DO |
| Create book lists. |   | TO DO |
| Edit my book lists. |   | TO DO |
| Add any unread book to read list. | Book must be unread. | TO DO |
| Mark any book as read. |   | TO DO |
| Rate any read book out of 10. | Book must be marked as read. | TO DO |
| See user's book lists on their profile page.  | User profile and list must be public. | TO DO |
| See publisher's book lists and book series on detail page.  |   | TO DO |

---

As an 👤 **Author**:

Same as <u>*User*</u>, plus;

| I want to... | Notes | Status |
|--|--|--|
| List my books. |   | TO DO |
| Update the information of my books. |   | TO DO |
| Add new book to my books. |   | TO DO |
| Send request to publisher to remove book. | The book must have been added by the author or the publisher. Otherwise, author can send a request to the their editor. | TO DO |

---

As a 👥 **Publisher**:

Same as <u>*User*</u>, plus;

| I want to... | Notes | Status |
|--|--|--|
| List books published by us. |   |  TO DO |
| Update the information of our books. |   | TO DO |
| Add new book to our books. |   | TO DO |
| Delete book from our books. | The book must have been added by the publisher. Otherwise, publisher should send a request to the their editor. | TO DO |

---

As an 👥 **Editor**:

Same as <u>*User*</u>, plus;

| I want to... | Notes | Status |
|--|--|--|
|   |   |   |

---

As an 👥 **Admin**:

Same as <u>*User*</u>, plus;

| I want to... | Notes | Status |
|--|--|--|
|   |   |   |

---

As a 👥 **Dealer**:

Same as <u>*User*</u>, plus;

| I want to... | Notes | Status |
|--|--|--|
|   |   |   |
