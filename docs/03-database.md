# Database Design

## Purpose

This document defines the initial database design for Takumi Farm Operations.

The database is designed around the business workflow rather than the user interface. Each table represents a real-world entity involved in the farm's daily operations.

The primary design goal is to keep the schema simple, maintainable, and flexible enough to support future enhancements without requiring significant structural changes.

---

## Design Principles

The database follows these principles:

- Each table represents a real business entity.
- Relationships should be simple and intuitive.
- Avoid premature optimization.
- Support both real-time and end-of-day activity logging.
- Allow future modules to build upon existing entities rather than replacing them.

The **Activity** table is the central entity within the system.

---

# Entity Relationship Overview

```text
User
 │
 │ 1
 │
 └──────────────┐
                │
                │ *
            Activity
                │
      ┌─────────┴─────────┐
      │                   │
      │                   │
      ▼                   ▼
 Vehicle              Expense
      │
      │
      ▼
 Vehicle Issue
```

An Activity belongs to one Driver and one Vehicle.

Each Activity may have multiple Expenses.

Each Activity may have multiple Vehicle Issues.

---

# Tables

## Users

Represents people who can access the system.

### Purpose

Authentication and ownership of activities.

### Fields

| Field        | Type           | Required | Notes                   |
| ------------ | -------------- | -------- | ----------------------- |
| id           | UUID / Integer | Yes      | Primary Key             |
| first_name   | String         | Yes      |                         |
| last_name    | String         | Yes      |                         |
| email        | String         | Yes      | Unique                  |
| phone_number | String         | No       |                         |
| role         | Choice         | Yes      | Driver or Administrator |
| is_active    | Boolean        | Yes      |                         |
| created_at   | DateTime       | Yes      |                         |
| updated_at   | DateTime       | Yes      |                         |

### Relationships

One User can create many Activities.

---

## Vehicles

Represents farm vehicles.

### Purpose

Stores all vehicles that may be used for operational activities.

### Fields

| Field               | Type           | Required | Notes                  |
| ------------------- | -------------- | -------- | ---------------------- |
| id                  | UUID / Integer | Yes      | Primary Key            |
| registration_number | String         | Yes      | Unique                 |
| nickname            | String         | No       | Example: Mercedes Vito |
| make                | String         | No       | Mercedes-Benz          |
| model               | String         | No       | Vito                   |
| is_active           | Boolean        | Yes      |                        |
| created_at          | DateTime       | Yes      |                        |
| updated_at          | DateTime       | Yes      |                        |

### Relationships

One Vehicle can have many Activities.

---

## Activities

The central business record.

Each Activity represents work carried out using a vehicle.

### Purpose

Capture daily operational activity.

### Fields

| Field         | Type           | Required | Notes                                                     |
| ------------- | -------------- | -------- | --------------------------------------------------------- |
| id            | UUID / Integer | Yes      | Primary Key                                               |
| driver_id     | Foreign Key    | Yes      | Users                                                     |
| vehicle_id    | Foreign Key    | Yes      | Vehicles                                                  |
| activity_type | Choice         | Yes      | Delivery, Collection, Purchase, Farm Work, Service, Other |
| destination   | String         | Yes      |                                                           |
| description   | Text           | No       |                                                           |
| notes         | Text           | No       |                                                           |
| activity_date | Date           | Yes      | Date the work occurred                                    |
| created_at    | DateTime       | Yes      | Record creation time                                      |
| updated_at    | DateTime       | Yes      |                                                           |

### Relationships

Belongs to one Driver.

Belongs to one Vehicle.

Can contain many Expenses.

Can contain many Vehicle Issues.

---

## Expenses

Operational expenses associated with an Activity.

### Purpose

Record costs incurred while carrying out an activity.

### Fields

| Field        | Type           | Required | Notes                                  |
| ------------ | -------------- | -------- | -------------------------------------- |
| id           | UUID / Integer | Yes      | Primary Key                            |
| activity_id  | Foreign Key    | Yes      | Activities                             |
| expense_type | Choice         | Yes      | Fuel, Parking, Repair, Car Wash, Other |
| amount       | Decimal        | Yes      |                                        |
| description  | Text           | No       |                                        |
| created_at   | DateTime       | Yes      |                                        |

### Relationships

Each Expense belongs to one Activity.

---

## Vehicle Issues

Vehicle observations reported during an Activity.

### Purpose

Record problems noticed while using a vehicle.

The table records observations only. It is not intended to manage maintenance or repairs.

### Fields

| Field       | Type           | Required | Notes             |
| ----------- | -------------- | -------- | ----------------- |
| id          | UUID / Integer | Yes      | Primary Key       |
| activity_id | Foreign Key    | Yes      | Activities        |
| title       | String         | Yes      | Short description |
| description | Text           | No       |                   |
| created_at  | DateTime       | Yes      |                   |

### Relationships

Each Vehicle Issue belongs to one Activity.

---

# Future Expansion

The current schema intentionally leaves room for future modules without changing existing relationships.

Potential future entities include:

- Deliveries
- Customers
- Inventory
- Maintenance
- Purchase Orders
- Suppliers
- POS Transactions

These modules should reference existing entities where appropriate rather than duplicating data.

---

# Design Decisions

### Activities are the central entity.

The system records operational work rather than managing tasks or schedules.

---

### Expenses belong to Activities.

Expenses exist because an Activity occurred and should therefore remain attached to that operational record.

---

### Vehicle Issues belong to Activities.

Issues represent observations made during a specific activity.

Future maintenance workflows should reference these observations rather than replacing them.

---

### Drivers do not create Vehicles.

Vehicles are managed administratively.

Drivers simply select an existing vehicle when recording an activity.

---

### Authentication is separated from business records.

Users authenticate once and are then able to create or view activities according to their assigned role.

---

**Document Version:** 0.1

**Last Updated:** 09 July 2026

**Change Log**

- v0.1 – Initial database design drafted.
