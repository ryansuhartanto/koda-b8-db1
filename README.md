# Library ERD

Database exercise implementing an ERD for library.

```mermaid
---
title: Library
---

erDiagram

CATEGORY ||--o{ BOOK : "classifies"

CATEGORY ||--o{ BOOK_LOCATION : "occupies"
BOOKCASE ||--o{ BOOK_LOCATION : "provides"

BOOKKEEPER ||--o{ SHIFT : "is rostered for"

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

BOOKKEEPER {
    int id PK
    string name
    string phone
    string address

    string gender
    date birthdate
}

SHIFT {
    int id PK

    int id_bookkeeper FK

    date shift_date
    time start_time
    time end_time
}

PATRON {
    int id PK
    string name
    string phone
    string address

    date? birthdate
}
```

## License

[MIT](LICENSE)
