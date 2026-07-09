# Takumi Farm Operations

## Project Overview

### Vision

Takumi Farm Operations is a lightweight web-based operations management platform designed to digitize the farm's day-to-day vehicle operations.

The goal is not to build a traditional fleet management system, but rather to create a simple operational record that helps both drivers and management understand how farm vehicles are being used throughout the day.

The system is intentionally designed to be small, practical, and easy to use. It will evolve incrementally as the business grows and new operational requirements emerge.

---

## Background

Takumi Farm is a premium meat business based in Nairobi, Kenya.

Daily operations involve multiple vehicles performing tasks such as:

- Collecting livestock
- Delivering premium meat
- Purchasing supplies
- Farm visits
- Vehicle servicing
- General operational errands

Currently, much of this information is communicated verbally or through phone calls and messaging applications. As a result, there is no consistent operational record of:

- Which vehicles were used
- Who drove them
- What work they performed
- Any expenses incurred
- Vehicle issues identified during the day

This project aims to replace those informal processes with a simple digital system.

---

## Problem Statement

Drivers are usually occupied throughout the day and often receive new instructions while already working.

They rarely have time to complete lengthy forms or interact with complex software.

Management, on the other hand, requires a clear picture of daily vehicle operations without needing to contact individual drivers.

The challenge is therefore to design software that balances two competing needs:

- Extremely simple data entry for drivers.
- Meaningful operational visibility for management.

---

## Product Philosophy

The system is guided by the following principles:

- Simplicity over complexity.
- Record only information that provides operational value.
- Minimize typing and repetitive work.
- Support both real-time and end-of-day activity logging.
- Allow the product to grow through small iterations rather than large redesigns.
- Design around real business workflows instead of forcing users to adapt to the software.

---

## Primary Users

### Drivers

Drivers use the application to record vehicle activities.

Typical responsibilities include:

- Selecting the vehicle used.
- Recording the purpose of the trip.
- Recording the destination.
- Recording optional expenses.
- Reporting vehicle issues.
- Reviewing previous activities.

The interface is designed to be mobile-first and usable by drivers with minimal technical experience.

---

### Operations Manager / Administrator

Management uses the system to gain visibility into daily operations.

The primary objective is to answer operational questions such as:

- Which vehicles were used today?
- Who drove each vehicle?
- What activities were completed?
- Were any vehicle issues reported?
- Were any operational expenses incurred?

The initial administrative interface will focus on visibility rather than advanced reporting.

---

## MVP Objective

Version 1 of the system is considered successful if it enables drivers to quickly record vehicle activities and allows management to review those activities at the end of each day.

The application should answer the following five questions:

1. Which vehicles moved today?
2. Who drove them?
3. What were they used for?
4. Were any vehicle issues reported?
5. Were any expenses incurred?

If these questions can be answered reliably, the MVP has achieved its purpose.

---

## Long-Term Vision

Takumi Farm Operations is intended to become the operational platform for the business.

Future modules may include:

- Delivery Management
- Customer Management
- Inventory Tracking
- Vehicle Maintenance
- Driver Assignment
- Reporting and Analytics
- POS Integration
- Notifications
- Route Planning

These features are intentionally excluded from the MVP and will only be introduced when supported by real operational requirements.

---

## Technology Strategy

The project follows a modern web architecture consisting of:

**Frontend**

- React
- TypeScript
- Tailwind CSS
- shadcn/ui

**Backend**

- Django
- Django REST Framework

**Database**

- PostgreSQL

**Deployment**

- Ubuntu Linux
- Nginx
- Gunicorn
- HostAfrica VPS

This architecture provides a clean separation between the user interface and business logic while remaining straightforward to deploy and maintain.

---

## Success Criteria

The project will be considered successful when:

- Drivers can comfortably use the application during normal work without disrupting their workflow.
- Management can monitor daily vehicle operations without relying on phone calls or messaging applications.
- The software reduces the need for manual record keeping.
- The application provides a stable foundation for future operational modules without requiring major architectural changes.

Version: 0.1
Status: Draft
Last Updated: 2026-07-09
Owner: Kelvin Ngigi
