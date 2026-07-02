# Database Design

# Database Name

`task_manager_db`

---

# Overview

The Task Manager application uses a relational database with two main tables:

1. Users
2. Tasks

Each user can have multiple tasks, creating a **One-to-Many** relationship.

---

# Entity Relationship

```
Users (1)
   │
   │
   └──────────< Tasks (Many)
```

---

# Users Table

| Column     | Data Type    | Constraints                 |
| ---------- | ------------ | --------------------------- |
| id         | INTEGER      | Primary Key, Auto Increment |
| name       | VARCHAR(100) | NOT NULL                    |
| email      | VARCHAR(150) | UNIQUE, NOT NULL            |
| password   | VARCHAR(255) | NOT NULL                    |
| created_at | TIMESTAMP    | Default Current Timestamp   |
| updated_at | TIMESTAMP    | Default Current Timestamp   |

---

# Tasks Table

| Column      | Data Type    | Constraints                 |
| ----------- | ------------ | --------------------------- |
| id          | INTEGER      | Primary Key, Auto Increment |
| user_id     | INTEGER      | Foreign Key                 |
| title       | VARCHAR(200) | NOT NULL                    |
| description | TEXT         | NULL                        |
| category    | VARCHAR(50)  | NOT NULL                    |
| priority    | VARCHAR(20)  | NOT NULL                    |
| status      | VARCHAR(20)  | Default 'Pending'           |
| due_date    | DATE         | NOT NULL                    |
| created_at  | TIMESTAMP    | Default Current Timestamp   |
| updated_at  | TIMESTAMP    | Default Current Timestamp   |

---

# Relationship

* One user can create multiple tasks.
* Each task belongs to only one user.
* `user_id` in the `Tasks` table references `id` in the `Users` table.

---

# Constraints

## Users

* Email must be unique.
* Name is required.
* Password must be encrypted before storing.

## Tasks

* Title is required.
* Due date is required.
* Status can be:

  * Pending
  * Completed
* Priority can be:

  * Low
  * Medium
  * High
* Category examples:

  * Personal
  * Work
  * Study
  * Health
  * Shopping

---

# Indexes

Create indexes on:

* email
* user_id
* status
* priority
* due_date

These indexes improve query performance.

---

# Future Database Enhancements

Additional tables for future versions:

* Notifications
* Attachments
* Comments
* Tags
* Activity Logs
* Team Members
* Projects

These are outside the scope of Version 1 but can be added later without redesigning the database.
