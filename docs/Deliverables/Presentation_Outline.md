# AUK Campus Parking Management System

## Project Part 1 — Presentation Outline

**Team:** Enisi me Bijat  
**Members:** Marigona, Enis, Anese, Fjolla  
**Presentation date:** October 29, 2026  
**Duration:** 5 minutes  
**Report:** [SWEN383_P1_EnisiMeBijat.pdf](./SWEN383_P1_EnisiMeBijat.pdf)
---

## 1. Project Overview

**Duration: 45 seconds**

- Introduce the AUK Campus Parking Management System.
- Explain the problem: finding available parking spaces and avoiding booking conflicts.
- Introduce the four main user roles:
  - Students
  - Staff members
  - Security personnel
  - Administrators
- Explain the goal of making campus parking more organized and convenient.

## 2. Project Scope and Business Rules

**Duration: 55 seconds**

### In Scope

- User access and role-based permissions.
- Viewing parking availability and status.
- Creating, viewing, and cancelling eligible reservations.
- Booking validation and double-booking prevention.
- Security check-in and check-out.
- Simulated €1 deposits, refunds, and deposit retention.
- Administrative management of users, parking spaces, reservations, and operating hours.

### Out of Scope

- Real payment processing.
- Physical parking sensors and automated parking gates.
- Camera-based license plate recognition.
- GPS navigation and AI-based predictions.
- Integration with existing university systems.
- Separate native Android and iOS applications.

### Key Business Rules

- A reservation cannot exceed six hours.
- Bookings can be made up to 24 hours in advance.
- Each user can have only one open reservation at a time.
- The same parking space cannot have overlapping reservations.
- Reservations must fall within configured operating hours.
- The virtual €1 deposit is refunded or retained according to cancellation and attendance rules.

## 3. UML Class Diagram

**Duration: 65 seconds**

The class diagram represents the system's structure, including classes, attributes, methods, and relationships.

### Main Classes

- **User:** Stores common user information.
- **Student:** Represents a student using the system.
- **StaffMember:** Represents a staff member using the system.
- **SecurityPersonnel:** Confirms vehicle arrivals and departures.
- **Administrator:** Manages users, parking spaces, reservations, and operating hours.
- **Vehicle:** Stores registered vehicle information.
- **ParkingSpace:** Represents a parking space and manages availability.
- **Reservation:** Stores reservation details, times, status, and operations.
- **DepositRecord:** Tracks the simulated deposit and its status.
- **OperatingHours:** Defines permitted parking hours.
- **Enumerations:** Define valid user categories and parking, reservation, and deposit statuses.

### Design Decisions

- Inheritance allows specialized user classes to share common information and behavior.
- Associations represent relationships between users, vehicles, reservations, parking spaces, and deposit records.
- Separate classes help organize responsibilities and improve maintainability.
- Multiplicity indicates how many objects can participate in a relationship.

## 4. Sequence Diagrams

**Duration: 65 seconds**

### A. Reserve a Parking Space

1. The student requests available parking spaces for a selected time interval.
2. The system checks booking rules and parking-space availability.
3. The reservation is validated.
4. If valid, the system creates the reservation and records the simulated €1 deposit.
5. The student receives confirmation.
6. If the rules are invalid or the space is unavailable, the system displays an appropriate message.

### B. Cancel a Reservation

1. The student requests cancellation.
2. The system finds the reservation and checks cancellation eligibility.
3. If the reservation does not exist or cancellation is not allowed, the request is rejected.
4. Cancellation before the scheduled start time results in a virtual deposit refund.
5. Cancellation after the scheduled start time but before check-in results in deposit retention.
6. The system confirms the cancellation outcome.

### C. Administrator Manages Parking Availability

1. The administrator requests a parking-availability update.
2. The system verifies administrator permissions.
3. The system checks whether the parking space exists.
4. The proposed status is validated.
5. The system checks for affected reservations.
6. If existing reservations are affected, the administrator is asked to review them.
7. If the update is valid and there are no unresolved conflicts, the parking status is updated.

## 5. Design Risks and Proposed Design Patterns

**Duration: 50 seconds**

### Risk 1: Double Booking of Parking Spaces

**Proposed Pattern: Repository Pattern**

- Separates reservation data operations from booking business logic.
- Supports the Single Responsibility Principle and GRASP Low Coupling.
- Requires additional database transactions and conflict checks to prevent simultaneous overlapping bookings.

### Risk 2: Incorrect Reservation and Deposit Statuses

**Proposed Pattern: State Pattern**

- Organizes behavior according to the current reservation state.
- Helps ensure that only permitted actions and status transitions occur.
- Connects to the Single Responsibility Principle and GRASP Polymorphism.

**Note:** These patterns are proposed design choices for addressing anticipated risks.

## 6. Conclusion

- Summarize how the system aims to make campus parking more organized.
- Highlight the project scope, business rules, class responsibilities, and interaction workflows.
- Explain how the proposed patterns address reliability and maintainability concerns.
- Thank the audience and invite questions.

---

## Presentation Timing

| Section | Duration |
|---|---:|
| Project overview | 45 seconds |
| Scope and business rules | 55 seconds |
| UML class diagram | 65 seconds |
| Sequence diagrams | 65 seconds |
| Design risks, patterns, and conclusion | 50 seconds |
| **Total** | **5 minutes** |

## Repository

[AUK Campus Parking Management System — GitHub](https://github.com/fjollabeha/AUK-Campus-Parking-Management-System)