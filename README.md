# Library ERD

Database exercise implementing an ERD for library.

```mermaid
---
title: Library
---

erDiagram

BOOK }o--|| CATEGORY : "belongs to"

CATEGORY ||--o{ BOOK_LOCATION : "occupies"
BOOKCASE ||--o{ BOOK_LOCATION : "provides"

BOOK {
    int id PK
    string isbn
    string name
    string author

    int id_category FK
}

CATEGORY {
    int id PK
    string name
}

BOOKCASE {
    int id PK
    int floor
    int aile
}

BOOK_LOCATION {
    int id_category FK
    int id_bookcase FK
}
```

## License

[MIT](LICENSE)
