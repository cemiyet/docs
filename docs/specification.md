## Glossary

| Symbol | Meaning |
|:-:|--|
| ❓ | it's not accepted yet |
| 💶 | potential income model |
| 🆘 | help needed |
| 🎞️ | back-end related |
| 🖼️ | front-end related |

---

## Actors

| Actor | Assets |
|--|--|
| 👻 **Guest** | nothing. |
| 👤 **Member** | *book lists* |
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

| As a/an | I want to... | So that... | Notes | Priority | Status |
|--|--|--|--|--|--|
| 👻 **Guest** |   |   |   |   | TODO |
|   |   |   |   |   |   |
| 👤 **Member** |   |   |   |   | TODO |
|   |   |   |   |   |   |
| 👥 **Editor** |   |   |   |   | TODO |
|   |   |   |   |   |   |
| 👥 **Admin** |   |   |   |   | TODO |
|   |   |   |   |   |   |
| 👤 **Author** |   |   |   |   | TODO |
|   |   |   |   |   |   |
| 👥 **Publisher** |   |   |   |   | TODO |
|   |   |   |   |   |   |
| 👥 **Dealer** |   |   |   |   | TODO |
|   |   |   |   |   | TODO |

---

## Models

- **1st Generation:**
    - Books
    - Genres
    - Dimensions
    - Authors
    - Publishers
    - Translators ❓
    - Members
    - Dealers ❓
- **2nd Generation (Depends on 1st Generation):**
    - Series
    - Admins
    - Editors
    - Tags ❓
    - Cemiyets ❓
    - Ratings ❓
    - Languages ❓
- **3rd Generation (Depends on 1st & 2nd Generations):**
    - Events ❓

## Entity-Relationship Diagram

Status: Feature frozen until v0.6. New iteration will be held after *Ratings & Lists* update.

![Entity-Relationship Diagram v0.5](img/ERD.png "Entity-Relationship Diagram v0.5")

---

## Feature Roadmap

Before starting development for every version, initial backlog should be present for *itself and next version*.

- **v0.1 - Genres & Dimensions Update:**
    - CRUD operations for Genre & Dimension models.
- **v0.2 - Authors & Publishers Update:**
    - CRUD operations for Author & Publisher models.
- **v0.3 - Books Update:**
    - CRUD operations for Book & Serie models.
    - Basic relations between books and related models. (authors, publishers etc.)
- **v0.4 - Members Update:**
    - CRUD operations for Member model.
    - Complete Authentication system.
- **v0.5 - Ratings & Lists Update:**
    - CRUD operations for Rating & List related models.
    - Basic rating system.
    - Basic relations between ratings, members and books.
    - CRUD operations for Book List models.
    - Advanced relationships between books and users/authors/publishers via custom lists.
- **v0.6 - Tags Update:** ❓
    - CRUD operations for User/Book Tag models.
- **v0.7 - Admins & Editors Update:**
    - CRUD operations for Admin & Editor models.
    - Complete Authorization system.
    - Complete CMS for Admins/Editors.
- **v0.8 - Authors & Publishers Enhancement Update:**
    - Advanced relationships and interactions between authors, publishers and books, members.
- **v0.9 - Dealers Update:**
    - CRUD operations for Dealer model.
- **v1.0 - Ötüken (MVP):**
    - Complete Authentication/Authorization system.
    - Future-proof book centered model system.
    - Complete management panels for Admins & Editors.
    - Special actors and interaction microsystems that could lead to potential income models.
