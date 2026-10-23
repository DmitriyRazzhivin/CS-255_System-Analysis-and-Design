# CS 255: Systems Analysis and Design Portfolio

- **Student:** Dmitriy Razzhivin
- **Institution:** Southern New Hampshire University
- **Course:** CS 255 System Analysis and Design
- **Project:** DriverPass Driving School Management System

---

## Repository Overview

This repository archives the core systems analysis, business architecture, and technical modeling artifacts developed for the DriverPass platform across two major software development lifecycle (SDLC) milestones:

- **`Business Requirements Document.docx` (Project One):** The initial Business Requirements Document capturing stakeholder discovery interviews, operational goals, functional and nonfunctional requirements, system constraints, user interface dashboard sketches, and project scheduling Gantt chart milestones.
- **`System Design Document.docx` (Project Two):** The comprehensive technical system design document containing standardized UML diagrams (Use Case Diagram, two Activity Diagrams, a Sequence Diagram, and a Domain Class Diagram) alongside the complete architectural specification for cloud infrastructure, microservices, relational database management (DBMS), and third-party integrations.

---

## Project Reflection & Self-Assessment

### 1. Project Summary & Client Vision

The DriverPass project focused on analyzing and architecting a modern, cloud-hosted enterprise management platform for Liam (Business Owner) and Ian (Information Technology Officer). DriverPass aimed to address a regional market failure where over 65% of driver's license candidates fail practical DMV examinations due to a lack of structured behind-the-wheel instruction and modern curriculum delivery.

The client required an integrated web-based system capable of:

- Centralizing online and telephone student onboarding and secure payment processing.
- Delivering interactive DMV educational coursework, tracking progress, and administering randomized practice tests.
- Coordinating driving lesson reservations in strict 2-hour blocks across a company fleet of 10 dedicated vehicles and certified instructors without double-booking.
- Providing role-based administrative consoles for secretaries, instructors, IT staff, and ownership.
- Establishing an automated regulatory integration pipeline with local DMV endpoints to consume real-time policy and testing updates.

---

### 2. Key Accomplishments & Design Strengths

My strongest contribution was translating complex operational policies into rigorous, unambiguous visual and technical models:

- **Constraint Validation in Scheduling Logic:** In both the UML Activity and Sequence diagrams for the *Book Road Lesson* workflow, I successfully formalized the multi-tier validation chain: verifying that the drop-off location strictly matches the pickup address, evaluating live resource concurrency across the 10-vehicle fleet and instructor rosters, and decrementing prepaid student package balances before confirming appointments.
- **Architectural Integrity & Data Protection:** In the technical requirements specification, I established clear operational boundaries. Specifically, I enforced an online-only write model to eliminate multi-server synchronization errors while supporting Liam’s need for offline reporting via server-side Microsoft Excel (`.xlsx`) exports. Additionally, I integrated PCI-DSS tokenized payment gateways to eliminate sensitive credit card liabilities from DriverPass databases.

---

### 3. Areas for Future Revision & Enhancement

If given the opportunity to revise and expand the design artifacts, I would enhance the structural and behavioral depth in two key areas:

- **UML Class Diagram Method Signatures:** The Project Two rubric only mandated classes and attributes. Expanding each class to include full method signatures, parameter types, and return values (e.g., `assignFleetResource(slot: TimeSlot, vehicleId: String): Boolean` or `validateDropOffMatch(pickup: Address, dropOff: Address): Boolean`) would deliver an immediate, turn-key blueprint for backend software developers.
- **Vehicle State Machine Modeling:** I would introduce a UML State Machine diagram modeling the lifecycle of a `FleetVehicle` entity across distinct operational states (`Available`, `In-Service/On Route`, `Scheduled for Maintenance`, and `Deactivated`) to better automate maintenance lockout triggers during booking transactions.

---

### 4. Interpreting User Needs & Human-Centered Design

I interpreted the client’s needs by extracting core domain entities, operational constraints, and workflow pain points directly from the stakeholder interview transcripts and Liam’s original UI sketches:

- **Role-Differentiated Interfaces:** I segmented features into dedicated personas: a rapid telephone onboarding form for the office secretary, mobile-friendly post-lesson log sheets for on-the-road instructors, an account security console for Ian, and high-level financial and activity reporting for Liam.
- **The Importance of User-Centered Design:** Systems analysis must always be grounded in user realities rather than theoretical software ideals. When software fails to mirror operational workflows, users inevitably resort to manual workarounds, spreadsheets, and error-prone side channels. Designing around real user constraints ensures system adoption, reduces onboarding overhead, and eliminates operational friction.

---

### 5. Approach to Software Design & Future Strategies

My approach to systems design is iterative, analytical, and model-driven:

1. **Deconstruct Requirements:** Distinguish core functional behaviors from nonfunctional constraints, regulatory requirements, and physical limitations.
2. **Model Behavior Before Implementation:** Utilize CASE modeling tools (such as Lucidchart) to visually map dynamic sequences, decision paths, and state changes before writing production code.
3. **Establish Strong Data Foundations:** Design normalized relational data schemas with explicit integrity constraints, row-level locking mechanisms, and audit logging.

In future software engineering initiatives, I will continue applying blended agile-waterfall modeling: combining thorough upfront architectural analysis and living documentation with iterative delivery cycles to ensure software remains aligned with stakeholder goals throughout the development lifecycle.
