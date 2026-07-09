# MVP Specification

## Purpose

This document defines the scope of Version 1 (MVP) of Takumi Farm Operations.

The objective is to deliver the smallest useful product that solves the farm's current operational challenges while providing a stable foundation for future improvements.

Any feature not listed in this document is considered **out of scope** for Version 1.

---

## MVP Goal

The MVP should enable drivers to quickly record vehicle activities and allow management to review those activities at the end of each day.

The system should answer the following operational questions:

- Which vehicles moved today?
- Who drove them?
- What activities were carried out?
- Were any vehicle issues reported?
- Were any expenses incurred?

If these questions can be answered reliably, the MVP has achieved its purpose.

---

# Users

## Driver

Drivers can:

- Log in.
- View today's activities.
- Create a new vehicle activity.
- Edit their own activity.
- View previous activities.
- View activity details.
- Log out.

---

## Administrator

Administrators can:

- Log in.
- View all recorded activities.
- Filter activities by date.
- Filter activities by vehicle.
- Filter activities by driver.
- View activity details.

The administrative interface is intended for operational visibility only.

No reporting dashboards or analytics are included in the MVP.

---

# Vehicle Activities

Each activity should record:

Required

- Vehicle
- Driver
- Activity Type
- Destination
- Activity Date

Optional

- Description
- Expenses
- Vehicle Issues
- Notes

Drivers may record activities either:

- During the day.
- At the end of the working day.

Both workflows should be equally supported.

---

# Expenses

An activity may contain zero or more expenses.

Each expense records:

- Expense Type
- Amount
- Optional Description

Receipt uploads are excluded from Version 1.

---

# Vehicle Issues

An activity may contain zero or more vehicle issues.

Each issue records:

- Short Title
- Description

Issue tracking, maintenance workflows, and repair scheduling are excluded from Version 1.

---

# Authentication

The system supports two user roles:

- Driver
- Administrator

Authentication is required before accessing the application.

---

# Mobile Experience

The driver interface is mobile-first.

The application should be fully usable on a smartphone.

The target time to create a vehicle activity is less than one minute.

---

# Out of Scope

The following features are intentionally excluded from Version 1:

- Delivery management
- Customer management
- Inventory
- Vehicle maintenance scheduling
- Reports and analytics
- Notifications
- GPS tracking
- Live driver tracking
- Route optimisation
- POS integration
- File uploads
- Receipt images
- Push notifications
- Offline support

These may be considered in future releases.

---

# Definition of Done

Version 1 is complete when:

- Drivers can authenticate.
- Drivers can create vehicle activities.
- Drivers can edit their own activities.
- Drivers can view activity history.
- Drivers can record expenses.
- Drivers can report vehicle issues.
- Administrators can view all activities.
- Administrators can filter activities.
- The application is deployed to production.
- The application is being used during normal farm operations.

---

# Success Criteria

The MVP will be considered successful if:

- Drivers consistently use it instead of paper notes or messaging applications.
- Management can determine daily vehicle usage without contacting drivers.
- Vehicle issues are captured consistently.
- Operational expenses are recorded alongside activities.
- The application is simple enough that little or no training is required.
