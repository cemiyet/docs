## Models

- **1st Generation:**
    - Books
    - Genres
    - Dimensions
    - Authors
    - Publishers
    - Translators ❓
    - Members
    - Dealers
- **2nd Generation (Depends on 1st Generation):**
    - Series
    - Admins
    - Editors
    - UsersLists
    - Tags
    - Cemiyets
    - Languages ❓
- **3rd Generation (Depends on 1st & 2nd Generations):**
    - Events

## Entity-Relationship Diagram

Status: Feature frozen until v0.6. New iteration will be held after the *Ratings & Lists* update.

![Entity-Relationship Diagram v0.6](img/ERD.png "Entity-Relationship Diagram v0.5")

**CreatorType**;

0 : admin  
1 : genre_editor  
2 : author_editor  
3 : publisher_editor  
4 : publisher  
5 : author

**UsersBooksStatusType**;

0 : want_to_read  
1 : reading  
2 : read  
