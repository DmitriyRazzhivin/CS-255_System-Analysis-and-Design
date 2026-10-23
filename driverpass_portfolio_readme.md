# CS 255: Systems Analysis and Design Portfolio

| Metadata | Details |
| :--- | :--- |
| **Student** | Dmitriy Razzhivin |
| **Institution** | Southern New Hampshire University |
| **Course** | CS 255 System Analysis and Design |
| **Project** | DriverPass Driving School Management Platform |

---

## Repository Overview

This repository archives the foundational software analysis, business domain modeling, and technical system architecture artifacts produced for **DriverPass** across two major Software Development Life Cycle (SDLC) milestones:

* **[`final_Business_Requir_Doc.docx`](./final_Business_Requir_Doc.docx) — Project One:**  
  The initial *Business Requirements Document* capturing client discovery interview transcripts, operational objectives, categorized functional and nonfunctional requirements, system assumptions and limitations, user interface dashboard wireframes, and project scheduling Gantt chart timelines.

* **[`CS 255 System Design Document.docx`](./CS%20255%20System%20Design%20Document.docx) — Project Two:**  
  The formal *System Design Document* containing CASE-engineered UML models (*Use Case Diagram*, two *Activity Diagrams*, a *Sequence Diagram*, and a static domain *Class Diagram*) alongside technical requirements detailing cloud compute infrastructure, microservices architecture, relational database management (DBMS) concurrency controls, and third-party API integrations.

---

## Project Reflection & Self-Assessment

### 1. Project Summary & Client Vision

The **DriverPass** initiative centered on analyzing, modeling, and designing a cloud-hosted driving school management system for **Liam** (*Business Owner*) and **Ian** (*IT Officer*). The primary business goal was addressing a severe market gap in which over 65% of regional driver's license candidates fail practical state DMV examinations due to a lack of structured, hands-on instruction.

The client required a unified, multi-tiered platform capable of:
* **Student Lifecycle Management:** Automating registration, personal profile management, and payment card onboarding.
* **Curriculum & Progress Monitoring:** Delivering interactive online DMV modules, recording completion statistics, and administering randomized practice quizzes.
* **Intelligent Fleet Scheduling:** Scheduling in-car appointments in strict two-hour increments across **10 company vehicles** and certified driving instructors without double-booking.
* **Role-Based Workspaces:** Providing customized interfaces for Students, Office Secretaries, Driving Instructors, IT Administrators, and Ownership.
* **Regulatory Compliance Integration:** Consuming automated real-time feeds from state DMV servers to maintain question banks and rule policies.

---

### 2. Key Accomplishments & Design Strengths

My most notable accomplishments involved translating multi-faceted business policies into unambiguous, mathematically bounded system models:

* **Rigorous Scheduling Validation:**  
  In the *Book Road Lesson* UML Activity and Sequence diagrams, I formalized a sequential validation chain that prevents scheduling conflicts:
  1. *Geographic Integrity:* Enforcing that `dropOffLocation == pickupLocation`.
  2. *Fleet & Staff Availability:* Verifying that an unassigned vehicle and certified instructor are available simultaneously within the requested time window across the 10-car fleet.
  3. *Balance Verification:* Ensuring the student’s remaining package hours satisfy `remainingHours >= 2` prior to committing database transactions.

* **Architectural Boundaries & Security Controls:**  
  In the technical requirements, I established strict operational rules:
  * **Online-Only Write Model:** Eliminated multi-master replication conflicts and data drift by requiring active network connectivity for state changes, while supporting offline analytical needs via server-side Microsoft Excel (`.xlsx`) report exports.
  * **Payment Tokenization:** Mitigated PCI-DSS liabilities by routing sensitive credit card details through tokenized third-party APIs (e.g., Stripe) so raw financial data never touches DriverPass storage.

---

### 3. Areas for Future Revision & Enhancement

If given the opportunity to iterate further on these specifications, I would expand the system models in two specific areas:

1. **Explicit Class Method Signatures:**  
   The baseline rubric only required classes and attributes. I would expand the UML Class Diagram to include full public and private operational methods with complete parameter and return types, such as:
   * `+ checkFleetAvailability(slot: TimeSlot): Boolean`
   * `+ validateLocationCoordinates(pickup: Address, dropOff: Address): Boolean`
   * `+ ingestDmvPayload(updateFeed: JSON): Void`

2. **Vehicle Lifecycle State Machine Modeling:**  
   I would incorporate a formal UML State Machine diagram tracking the state transitions of each `FleetVehicle`:
   $$\text{Available} \xrightarrow{\text{Booked}} \text{In-Service} \xrightarrow{\text{Milestone Reached}} \text{Maintenance} \xrightarrow{\text{Inspected}} \text{Available}$$
   This would automate safety lockouts so vehicles flagged for routine maintenance are withheld from the booking engine.

---

### 4. Interpreting User Needs & Human-Centered Design

User requirements were identified by decomposing interview transcripts and user interface sketches into dedicated operational personas:

* **Secretary Interface:** Optimized with a streamlined, single-screen data entry form for rapid telephone intake.
* **Instructor Interface:** Built as a mobile-responsive viewport for immediate post-lesson drive-log entry and qualitative student feedback.
* **Owner Interface:** Configured with real-time analytics widgets and one-click data export tools.
* **IT Console:** Focused on role-based access control (RBAC), brute-force account defense monitoring, and self-service password reset tools.

> **Why User-Centered Design Matters:**  
> Systems analysis must prioritize end-user workflows over abstract engineering preferences. When software fails to align with operational reality, staff abandon automated systems in favor of error-prone manual spreadsheets. Designing directly to user needs ensures high adoption, minimizes human error, and creates measurable operational efficiency.

---

### 5. Software Design Methodology & Future Strategies

My approach to software engineering is structured, user-focused, and model-driven:

```text
[ Business Needs Analysis ]
           │
           ▼
[ Functional & Nonfunctional Decomposition ]
           │
           ▼
[ Visual Behavioral & Structural Modeling (UML) ]
           │
           ▼
[ Technical Infrastructure & Concurrency Engineering ]
           │
           ▼
[ Iterative Prototype & Implementation ]
```

1. **Requirements Decomposition:** Isolate business capabilities, define data dictionaries, and document environmental constraints early.
2. **Visual Model-Driven Design:** Utilize CASE tools (e.g., Lucidchart) to resolve edge cases in behavioral flows (Activity/Sequence) and object relationships (Class) prior to implementation.
3. **Resilient Data Engineering:** Enforce ACID transaction compliance, foreign key constraints, concurrency locks, and tamper-evident audit trails.

In future initiatives, I will continue utilizing this hybrid approach—combining thorough upfront architectural analysis with agile development iterations to ensure software deliverables remain technically sound and aligned with stakeholder objectives.