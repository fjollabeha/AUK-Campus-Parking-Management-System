# UML Class Diagram Explanation

## AUK Campus Parking Management System

The UML class diagram shows the main classes of the AUK Campus Parking Management System, their attributes, methods, and relationships.

### Main Classes

- **User:** Stores common information about system users.
- **Student, StaffMember, SecurityPersonnel, and Administrator:** Represent different user roles.
- **Vehicle:** Represents a registered vehicle.
- **ParkingSpace:** Manages parking spaces and their availability.
- **Reservation:** Stores reservation details and status.
- **DepositRecord:** Tracks the virtual deposit for a reservation.
- **OperatingHours:** Defines parking operating hours.

### Relationships and Enumerations

The system uses **inheritance** to share common information between 'User' and its specialized user classes. **Associations** connect users, vehicles, reservations, parking spaces, and deposit records.

Enumerations such as 'SpaceStatus', 'ReservationStatus', 'DepositStatus', and 'UserType' define the possible statuses and user categories.

### Purpose

The diagram provides an overview of the systems structure and shows how its classes work together to manage parking reservations, availability, check-in/check-out, and virtual deposits.