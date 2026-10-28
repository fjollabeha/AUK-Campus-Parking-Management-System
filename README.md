# AUK Campus Parking Management System

A software design project for a campus parking management system at the American University in Kosovo (AUK), developed for **SWEN 383 — Software Design Principles and Patterns**.

## Project Information

- **Course:** SWEN 383 — Software Design Principles and Patterns
- **Institution:** RIT Kosovo
- **Instructor:** Valon Raca
- **Team:** Enisi me Bijat
- **Team Members:** Marigona, Enis, Anese, and Fjolla
- **Project Part:** Part 1
- **Presentation Date:** October 29, 2026

## Project Overview

The AUK Campus Parking Management System is designed to help students and staff reserve parking spaces on campus. The system also supports administrators in managing parking availability and security personnel in confirming vehicle arrivals and departures.

This project focuses on defining the system's scope, modeling its structure and interactions using UML diagrams, and identifying design risks and suitable design patterns.

## Main Features

- Reserve a parking space.
- Cancel a parking reservation.
- Manage parking space availability.
- Track reservation and deposit statuses.
- Confirm vehicle arrivals and departures.
- Apply reservation time limits, operating hours, and cancellation rules.

## Project Documentation

- **[Project Part 1 Report (PDF)](docs/SWEN383_P1_EnisiMeBijat.pdf)**
- **[Five-Minute Presentation Outline](docs/Presentation_Outline.md)**
- [Project Description and Scope](docs/Project_Documentation/PROJECT_DESCRIPTION_AND_SCOPE.md)
- [Design Risks and Patterns](docs/Project_Documentation/Design_Risks_and_Patterns.md)

## UML Diagrams

### Class Diagram

The class diagram represents the main classes, attributes, methods, and relationships in the parking management system.

- [View Class Diagram (PNG)](docs/UML/Class_Diagram/AUK_Parking_Class_Diagram.png)
- [View PlantUML Source](docs/UML/Class_Diagram/AUK_Parking_Class_Diagram.puml)
- [Read Class Diagram Explanation](docs/UML/Class_Diagram/UML_Class_Diagram_Explanation.md)

### Sequence Diagrams

The sequence diagrams illustrate key interactions within the system.

**1. Reserve a Parking Space**
- [View Diagram (PNG)](docs/UML/Sequence_Diagrams/Sequence_Reserve_Parking.png)
- [View PlantUML Source](docs/UML/Sequence_Diagrams/Sequence_Reserve_Parking.puml)

**2. Cancel a Reservation**
- [View Diagram (PNG)](docs/UML/Sequence_Diagrams/Sequence_Cancel_Reservation.png)
- [View PlantUML Source](docs/UML/Sequence_Diagrams/Sequence_Cancel_Reservation.puml)

**3. Administrator Manages Parking Availability**
- [View Diagram (PNG)](docs/UML/Sequence_Diagrams/Sequence_Admin_Manage_Availability.png)
- [View PlantUML Source](docs/UML/Sequence_Diagrams/Sequence_Admin_Manage_Availability.puml)

## Design Risks and Patterns

- **Double booking:** The Repository Pattern can centralize reservation data access. Database transactions and conflict checks are also needed to prevent overlapping reservations.
- **Incorrect reservation or deposit statuses:** The State Pattern is a proposed approach for organizing status-dependent behavior and valid state transitions.

These patterns are proposed design approaches for the identified risks.

## Repository

[**AUK Campus Parking Management System — GitHub**](https://github.com/fjollabeha/AUK-Campus-Parking-Management-System)