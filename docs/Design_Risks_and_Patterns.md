# Member 4 – Design Risks & Design Patterns

## AUK Campus Parking Management System

### Introduction

For our parking management system, we identified two possible design risks that could cause problems when the system is being used. We also chose design patterns that could help us avoid these problems and make the system easier to maintain.

### Risk 1: Double Booking of Parking Spaces

**Problem:**

One possible problem is that two students might try to reserve the same parking space at the same time. If the system doesn't handle this correctly, both reservations could be accepted even though only one parking space is available.

**Design Pattern: Repository Pattern**

We chose the Repository Pattern because it helps separate database operations from the reservation logic. For example, we could use a `ReservationRepository` to handle saving and retrieving reservations instead of having these operations mixed with the booking logic.

However, the Repository Pattern alone doesn't prevent double booking. We would also need database transactions and proper checks to make sure two users cannot successfully reserve the same space for overlapping times.

**Connection to SOLID and GRASP:**

- **Single Responsibility Principle (SRP):** Each part has its own responsibility. The reservation logic handles the booking rules, while the repository handles database operations.
- **GRASP Low Coupling:** The reservation logic doesn't need to depend directly on how the data is stored, making the system easier to change and maintain.

This risk is related to the `Reservation` and `ParkingSpace` classes in our UML diagram.

### Risk 2: Incorrect Reservation and Deposit Statuses

**Problem:**

Another possible problem is handling the different reservation statuses and virtual deposits correctly. Our system has statuses like Reserved, Checked In, Completed, Cancelled, and No-Show.

For example, a student shouldn't be able to cancel a reservation after checking in. Another issue could be refunding the virtual €1 deposit more than once or not retaining it when a student fails to arrive within the 10-minute grace period.

**Design Pattern: State Pattern**

We chose the State Pattern because it helps control what actions are allowed depending on the reservation's current status.

For example, when a reservation is Reserved, the student can cancel it before check-in. But once it is Checked In, the normal cancellation option should no longer be allowed.

Using this pattern would help us organize the rules for changing reservation statuses and prevent invalid actions. We would also need to make sure that changes to the reservation and deposit records are saved consistently.

**Connection to SOLID and GRASP:**

- **Single Responsibility Principle (SRP):** Each proposed state class would handle the rules for a specific reservation state instead of putting all the conditions in one place.
- **GRASP Polymorphism:** Different states can handle the same action differently depending on the reservation's current status.

This risk is related to the `Reservation`, `ReservationStatus`, `DepositRecord`, and `DepositStatus` elements in our UML diagram.

### Conclusion

These two risks are important because our system needs to prevent booking conflicts and keep reservation and deposit information correct.

The Repository Pattern would help us organize reservation data operations, together with database transactions to prevent double booking. The State Pattern would help us manage reservation statuses and make sure only valid actions are allowed.

By using these patterns, we aim to make our parking management system more organized, reliable, and easier to maintain or improve in the future.
