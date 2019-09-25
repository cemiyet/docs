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

Status: Feature frozen until v0.6. New iteration will be held after the *Ratings & Lists* update.

![Entity-Relationship Diagram v0.5](img/ERD.png "Entity-Relationship Diagram v0.5")

Books>CreatorType;

0 : Admin  
1 : GenreEditor  
2 : AuthorEditor  
3 : PublisherEditor  
4 : Publisher  
5 : Author
