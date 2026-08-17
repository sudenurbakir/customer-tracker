# Customer Tracker - ER Diyagramı (Mermaid)

**Proje:** customer-tracker  
**Versiyon:** 1.0 (MVP)

---

## Varlık İlişki Diyagramı

```mermaid
erDiagram
    CUSTOMER ||--o{ PROJECT : has
    PROJECT ||--o{ CONTRACT : has
    PROJECT ||--o{ INVOICE : has
    PROJECT ||--o{ NOTE : has
    INVOICE ||--o{ PAYMENT : has

    CUSTOMER {
        uuid id PK
        string name
        string contact_person
        string phone
        string email
        string address
        text notes
        datetime created_at
        datetime updated_at
    }

    PROJECT {
        uuid id PK
        uuid customer_id FK
        string name
        string status
        date start_date
        date end_date
        text description
        datetime created_at
        datetime updated_at
    }

    CONTRACT {
        uuid id PK
        uuid project_id FK
        string title
        date start_date
        date end_date
        decimal amount
        string currency
        string file_link
        text notes
        datetime created_at
    }

    INVOICE {
        uuid id PK
        uuid project_id FK
        string invoice_number
        date invoice_date
        decimal amount
        string currency
        string status
        text description
        datetime created_at
    }

    PAYMENT {
        uuid id PK
        uuid invoice_id FK
        date payment_date
        decimal amount
        string payment_method
        text notes
        datetime created_at
    }

    NOTE {
        uuid id PK
        uuid project_id FK
        text content
        datetime created_at
    }
