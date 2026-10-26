# AUK Campus Parking Management System

## Project Description & Scope

**Course:** SWEN-383 - Software Design Principles and Patterns  
**Project:** AUK Campus Parking Management System  
**Prepared by:** Enis Popovic - Project Description & Scope

---

## 1. Project Overview

The AUK Campus Parking Management System is a proposed software application designed to improve how parking spaces are reserved, monitored, and managed at the AUK campus.

Students and staff often need convenient access to parking when arriving at university. Without a centralized reservation and management system, users may have difficulty knowing whether parking spaces are available, while campus personnel may struggle to maintain accurate information about reservations and occupied spaces.

The proposed system will provide a centralized platform where students and staff can view parking availability, reserve spaces for specific periods, and manage their reservations. Security personnel will verify vehicle arrivals and departures, while administrators will manage parking spaces, user accounts, reservations, and operating hours.

The system will also introduce a simulated refundable €1 reservation deposit to discourage unnecessary bookings and no-shows. All financial transactions will be virtual, meaning no real payments or banking integrations are required.

The main purpose of the project is to create an organized, transparent, and efficient parking management process while demonstrating software design principles, object-oriented modelling, and appropriate design patterns.

## 2. Problem Statement

The project aims to address several common challenges in campus parking management:

- **Limited visibility:** Students and staff may not know which parking spaces are available before arriving.
- **Unorganized reservations:** Without centralized scheduling, parking spaces may be overbooked or reserved inefficiently.
- **Unused reservations:** Users may reserve spaces but fail to arrive, preventing others from using them.
- **Manual administration:** Managing reservations, user access, and parking availability can become difficult without a centralized system.
- **Inaccurate occupancy information:** A reservation does not necessarily mean that a vehicle has arrived, and a reservation's scheduled ending does not prove that a vehicle has departed.

By addressing these challenges, the system aims to make campus parking more predictable for users and easier to manage for authorized personnel.

## 3. Project Objectives

The primary objectives of the system are to:

1. Provide students and staff with a simple way to view and reserve available parking spaces.
2. Prevent overlapping reservations and reduce inefficient use of parking resources.
3. Display reliable system-recorded information about available, reserved, occupied, and unavailable spaces.
4. Enable authorized security personnel to confirm vehicle arrivals and departures.
5. Encourage responsible reservation behavior through cancellation rules and simulated deposit penalties.
6. Allow administrators to manage users, parking spaces, reservations, and configurable operating hours.
7. Maintain clear separation between user responsibilities and administrative permissions.
8. Establish a manageable software design that can be extended and improved in future development stages.

## 4. Intended Users and Their Responsibilities

The system will support four user roles with different permissions.

| User Role | Description and Responsibilities |
| --- | --- |
| **Student** | Views parking availability, reserves an available space, cancels personal reservations, and checks personal reservation status and history. |
| **Staff Member** | Uses the same core reservation functionality as students, through an authorized staff account. |
| **Security Personnel** | Views relevant reservations, verifies vehicle arrivals, confirms check-in and check-out, and updates recorded parking occupancy. |
| **Administrator** | Manages user accounts, parking spaces, operating hours, space availability, reservations, and exceptional administrative situations. |

Each user will have access only to functions permitted by their assigned role. Students and staff cannot alter another person's reservation or manually mark a parking space as occupied.

Students and staff will be identified using their university-issued IDs. A secure sign-in mechanism is required; the specific authentication implementation remains subject to team approval.

## 5. Main System Features and Functional Requirements

### 5.1 User Authentication and Access Control

**FR-01 — User Login:** The system shall provide a login mechanism for authorized students, staff, security personnel, and administrators.

**FR-02 — Role-Based Permissions:** The system shall restrict available operations according to each user's assigned role.

**FR-03 — Personal Account Information:** Students and staff shall be able to view their own reservation status and history without accessing other users' private records.

### 5.2 Parking Availability Management

**FR-04 — Parking Dashboard:** The system shall display the total number of managed parking spaces and their recorded availability.

**FR-05 — Parking Space Identification:** Each managed parking space shall have a unique identifier, such as A01, A02, or A12.

**FR-06 — Availability Status:** The system shall distinguish between available, reserved, occupied, and administratively unavailable parking spaces.

**FR-07 — Time-Based Availability:** When a user selects a reservation period, the system shall identify spaces that can be booked for the entire requested time range.

A space may be empty at the current moment but unavailable for a requested period because another reservation overlaps it. Availability must therefore consider both physical occupancy records and reservation schedules.

### 5.3 Parking Reservations

**FR-08 — Create Reservation:** Students and staff shall be able to select an available parking space and specify their intended arrival and departure times.

**FR-09 — Reservation Duration:** The system shall restrict each reservation to a maximum duration of six hours.

**FR-10 — Advance Booking:** Users shall be able to reserve a space up to 24 hours before the scheduled start time.

**FR-11 — Reservation Limit:** The system shall permit each user to hold only one open reservation at a time, including reservations that have already been checked in.

**FR-12 — Conflict Prevention:** The system shall reject a reservation if the selected parking space is already reserved for an overlapping period, recorded as occupied, or unavailable for administrative reasons.

**FR-13 — Reservation Confirmation:** When a valid reservation is created, the system shall record its details, associate it with the user and parking space, and display confirmation.

### 5.4 Simulated Deposit Management

**FR-14 — Virtual Deposit:** Every successfully created reservation shall record a simulated refundable deposit of €1.

**FR-15 — Deposit Refund:** The system shall record a virtual refund when security confirms arrival within the permitted grace period or when the user cancels before the scheduled start.

**FR-16 — Deposit Retention:** The system shall record the simulated deposit as retained when a user cancels late or fails to arrive within the allowed grace period.

The system will not process real money. Deposits, refunds, and penalties will be represented through stored application records.

### 5.5 Cancellation and No-Show Management

**FR-17 — User Cancellation:** Students and staff shall be able to cancel their own reservations before check-in.

**FR-18 — Early Cancellation:** If a reservation is cancelled before its scheduled start time, the system shall release the reservation and virtually refund the €1 deposit.

**FR-19 — Late Cancellation:** If a reservation is cancelled after its scheduled start time but before check-in, the system shall release it and retain the simulated deposit.

**FR-20 — Automatic No-Show:** If security has not confirmed the user's arrival within the ten-minute grace period, the system shall mark the reservation as a no-show, retain the simulated deposit, and release the reservation.

No-show handling must check the latest reservation status before updating the reservation to avoid incorrectly expiring an arrival that has already been verified.

### 5.6 Security Check-In and Check-Out

**FR-21 — Arrival Verification:** Authorized security personnel shall verify the arriving user's reservation and record check-in.

**FR-22 — Occupancy Update:** After a successful check-in, the parking space shall be marked as occupied, and the actual arrival time shall be recorded.

**FR-23 — Departure Verification:** Authorized security personnel shall confirm vehicle departure and record check-out.

**FR-24 — Space Release:** After check-out, the system shall end the occupied reservation and update availability while respecting any other scheduled reservations or administrative restrictions.

An occupied parking space shall never become available solely because the scheduled reservation end time has passed.

### 5.7 Administrator Management

**FR-25 — User Management:** Administrators shall be able to add, manage, and remove or deactivate user access.

**FR-26 — Parking Space Management:** Administrators shall be able to register and manage parking spaces and their availability.

**FR-27 — Configurable Operating Hours:** Administrators shall be able to configure the days and times during which parking reservations are permitted. The system shall reject bookings outside the permitted schedule.

**FR-28 — Reservation Administration:** Administrators shall be able to view and cancel reservations when necessary.

**FR-29 — Availability Control:** Administrators shall be able to make parking spaces temporarily unavailable, such as when a space is closed for maintenance.

**FR-30 — Operational Records:** The system shall maintain reservation and occupancy records so authorized personnel can review relevant parking activity.

## 6. Business Rules and Constraints

The following rules define how reservations and parking availability will operate.

| Rule | Description |
| --- | --- |
| **BR-01** | A reservation must have a valid start time earlier than its end time. |
| **BR-02** | A reservation cannot exceed six hours. |
| **BR-03** | The scheduled start time cannot be more than 24 hours in the future. |
| **BR-04** | A user may have only one open reservation at a time. |
| **BR-05** | The same space cannot have overlapping reservations. |
| **BR-06** | A reservation must fall within the configured parking operating schedule. |
| **BR-07** | A simulated €1 deposit is recorded for each confirmed reservation. |
| **BR-08** | Cancellation before the scheduled start results in a virtual refund. |
| **BR-09** | Cancellation after the scheduled start, before check-in, results in deposit retention. |
| **BR-10** | Users have ten minutes after their scheduled start time to complete arrival verification. |
| **BR-11** | A reservation without confirmed arrival after the grace period becomes a no-show. |
| **BR-12** | Security personnel confirm normal arrivals and departures. |
| **BR-13** | An occupied space remains unavailable until departure is confirmed. |
| **BR-14** | Completed, cancelled, and no-show reservations do not count toward the one-open-reservation limit. |
| **BR-15** | Simulated deposits must not be refunded or retained more than once. |

### Reservation Statuses

For consistent design, the system should distinguish these reservation states:

- **Reserved:** A valid reservation has been created and is awaiting arrival.
- **Checked In:** Security has verified arrival and the vehicle is recorded as occupying the space.
- **Completed:** Security has confirmed departure.
- **Cancelled:** The reservation was cancelled before check-in.
- **No-Show:** The reservation expired without confirmed arrival.

These reservation states are separate from the parking space's availability status.

For example, a completed reservation may leave a space physically empty, but another upcoming reservation may still prevent it from being booked for a particular time range.

## 7. Main System Workflows

### 7.1 Creating a Reservation

1. A student or staff member logs in.
2. The user selects an intended parking period.
3. The system validates the duration, booking window, user limit, operating hours, and space availability.
4. The user selects a suitable parking space.
5. The system confirms the reservation and records the simulated €1 deposit.
6. The user receives reservation confirmation, and availability records are updated.

If a validation rule fails, the reservation is rejected without recording a deposit.

### 7.2 Checking In and Checking Out

1. The user arrives during the permitted check-in period.
2. Security locates and verifies the reservation.
3. Security confirms arrival.
4. The system records check-in, marks the space Occupied, and virtually refunds the deposit.
5. When the user leaves, security confirms departure.
6. The system closes the reservation and updates availability.

### 7.3 Cancelling a Reservation

1. The user selects an open reservation.
2. The system checks whether cancellation is permitted.
3. The system compares the cancellation time with the scheduled start time.
4. If cancellation is early, it records a virtual refund.
5. If cancellation is late, it records deposit retention.
6. The reservation is marked Cancelled and the space is released from that reservation.

### 7.4 Handling a No-Show

1. The system identifies a reservation whose check-in grace period has expired.
2. It verifies that no valid check-in has been recorded.
3. The reservation is marked No-Show.
4. The simulated deposit is retained.
5. The space becomes available for other eligible reservations, provided no other restriction prevents booking.

## 8. Project Scope

### 8.1 In Scope

The first version of the AUK Campus Parking Management System will include:

- A software interface for authorized campus users.
- Login and role-based access permissions.
- Student and staff reservation functionality.
- A parking dashboard showing recorded parking availability.
- Individually identifiable parking spaces.
- Custom reservation start and end times.
- Six-hour maximum reservation duration.
- Booking up to 24 hours in advance.
- One open reservation per user.
- Prevention of conflicting parking reservations.
- Simulated €1 deposits, refunds, and no-show retention.
- User reservation cancellation.
- Automatic no-show processing after a ten-minute grace period.
- Security-confirmed vehicle check-in and check-out.
- Administrator management of users, spaces, and reservations.
- Administrator configuration of parking operating hours.
- Administrator control of temporarily unavailable spaces.
- Basic reservation history and operational records.

### 8.2 Out of Scope

The initial project will not include:

- Real online payments, bank transfers, or payment gateway integrations.
- Physical parking sensors or automated vehicle detection.
- License plate recognition or camera-based identification.
- Automated parking gates or barriers.
- GPS vehicle tracking or automated navigation to a space.
- Integration with the university's existing student information or authentication infrastructure.
- Advanced parking demand forecasting or AI-based space allocation.
- Real financial fines or automated collection of penalties.
- Separate native Android and iOS applications.

These features may be considered in future versions but are not necessary to demonstrate the primary parking reservation and management processes.

## 9. Assumptions and Limitations

**Application Platform:** A responsive web application is recommended for the initial prototype. This would allow users to access the system through desktop and mobile browsers without developing separate native applications.

**Parking Data:** The system will manage a predefined collection of identifiable parking spaces. The actual number and configuration of spaces will be determined during implementation.

**Authentication:** Users will have authorized accounts associated with their university identities. The specific login method must be approved by the team. Entering a university ID alone will not be treated as sufficient authentication.

**Availability Accuracy:** Recorded availability depends on security personnel confirming arrivals and departures. The prototype will not independently detect vehicles.

**Payment Simulation:** No money will be charged or refunded. The application will only simulate deposit transactions and record their outcomes.

**Operating Hours:** Parking reservation hours will be configurable by administrators rather than permanently fixed in the program.

**Software Quality:** Reservation operations should preserve consistent data, enforce authorization, and avoid double booking even if two users attempt to reserve the same space at nearly the same time.

## 10. Proposed Operational Policies for Team Approval

The following recommendations complete the intended behavior of the system but still require group confirmation.

| Area | Recommended Policy |
| --- | --- |
| **Overstays** | If a vehicle remains parked after its scheduled end, the space remains Occupied. Security or an administrator handles the situation manually. No additional financial penalty is applied in the prototype. |
| **Maintenance** | An administrator may make a space temporarily unavailable. Existing affected reservations must be reviewed or cancelled rather than silently ignored. |
| **Administrative Cancellation** | If an administrator cancels an uncompleted reservation for operational reasons, the virtual deposit should be refunded if it has not already been refunded. |
| **Administrative Corrections** | Administrators may correct erroneous reservation or occupancy records, with the action recorded for accountability. |
| **Operating Hours Changes** | Changes to parking hours should not automatically invalidate occupied spaces or existing bookings without administrative review. |
| **Reservation Time Boundaries** | Bookings should remain within the configured operating hours and should not cross a closed period. |
| **Authentication Method** | A basic account login with university ID and password is recommended for the prototype, without relying on a live university login service. |

**These policies should be approved before Members 2 and 3 finalize their UML models.**

## 11. Expected Project Outcome

The expected result is a working software prototype that demonstrates a complete parking reservation lifecycle: finding an available space, creating a reservation, recording a simulated deposit, verifying arrival, recording departure, and updating parking availability.

The system should also support cancellations, no-show handling, and administrative operations while preventing conflicting reservations and unauthorized actions.

The project is intended to demonstrate how sound software design can produce an organized and maintainable application. Its design should allow future extensions without requiring the core reservation functionality to be rewritten.

## 12. Shared Design Baseline for the Team

This Project Description & Scope document establishes the functional boundaries that the remaining team members should use.

**End of Member 1 — Project Description & Scope**

**Member 2 — UML Class Diagram:** The class model should support users and roles, parking spaces, reservations, simulated deposit records, and the functionality required to manage them. Classes and relationships should be chosen based on responsibilities, not assumed directly from this document's headings.

**Member 3 — UML Sequence Diagrams:** The sequence diagrams should represent reservation creation, reservation cancellation, and administrator management of parking availability. Their success paths and alternative flows must follow the business rules, including conflicts, timing limits, and refund behavior.

**Member 4 — Design Risks & Design Patterns:** The design analysis should consider risks such as simultaneous bookings, inconsistent occupancy data, authorization errors, missed no-show processing, and simulated deposit inconsistency. Any proposed patterns should support the agreed scope rather than introduce unrelated functionality.

**Final Team Review:** Before submission, all members should confirm that the UML diagrams, design risk analysis, project description, and presentation use the same terminology, business rules, and assumptions.
