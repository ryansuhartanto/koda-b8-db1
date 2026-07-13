# Library ERD

Database exercise implementing an ERD for library.

```mermaid
---
title: Library
---
erDiagram

CATEGORY ||--o{ BOOK : "classifies"

CATEGORY ||--o{ BOOKCASE_CATEGORY : "occupies"
BOOKCASE ||--o{ BOOKCASE_CATEGORY : "provides"

PERSON ||--o| PATRON     : "may be"
PERSON ||--o| BOOKKEEPER : "may be"

BOOKKEEPER ||--o{ SHIFT : "is rostered for"

PATRON     ||--o{ LOAN : "borrows"
BOOK       ||--o{ LOAN : "is lent in"
BOOKKEEPER ||--o{ LOAN : "processes"

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
    int aisle
}

BOOKCASE_CATEGORY {
    int id_category FK
    int id_bookcase FK
}

PERSON {
    int id PK
    string name
    string phone
    string address

    string? gender
    date? birthdate
}

BOOKKEEPER {
    int id PK
    int id_person FK
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
    int id_person FK
}

LOAN {
    int id PK

    int id_book FK
    int id_patron FK
    int id_bookkeeper FK

    date borrowed_at
    date due_at
    date? returned_at
}
```

## License

[MIT](LICENSE)
