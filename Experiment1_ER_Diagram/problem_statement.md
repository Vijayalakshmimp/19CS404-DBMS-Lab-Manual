# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_fitness.png)

### Entities and Attributes

| Entity              | Attributes (PK, FK)                                                                                | Notes                                 

| **MEMBER**          | **Member_ID (PK)**, Name, Membership_Type, Start_Date                                              | Stores registered gym members                            |
| **PROGRAM**         | **Program_ID (PK)**, Program_Name                                                                  | Examples: Yoga, Zumba, Weight Training                   |
| **TRAINER**         | **Trainer_ID (PK)**, Trainer_Name, Specialization                                                  | Stores trainer details                                   |
| **SESSION**         | **Session_ID (PK)**, Session_Date, Session_Time, Member_ID (FK), Trainer_ID (FK)                   | Personal training session booked by a member             |
| **ATTENDANCE**      | **Attendance_ID (PK)**, Session_ID (FK), Attendance_Status                                         | Records attendance for each session                      |
| **PAYMENT**         | **Payment_ID (PK)**, Member_ID (FK), Session_ID (FK, optional), Amount, Payment_Date, Payment_Type | Tracks membership and personal-training payments         |
| **MEMBER_PROGRAM**  | **Member_ID (PK, FK)**, **Program_ID (PK, FK)**, Join_Date                                         | Associative entity for members joining multiple programs |
| **PROGRAM_TRAINER** | **Program_ID (PK, FK)**, **Trainer_ID (PK, FK)**                                                   | Associative entity for trainers assigned to programs     |


### Relationships and Constraints
| Relationship                            | Cardinality | Participation                      | Notes                                                                                     |
| --------------------------------------- | ----------- | ---------------------------------- | ----------------------------------------------------------------------------------------- |
| **Member — joins — Program**            | M:N         | Member: Partial, Program: Partial  | A member can join multiple programs; a program can have multiple members                  |
| **Trainer — assigned to — Program**     | M:N         | Trainer: Partial, Program: Partial | A trainer can handle multiple programs; a program can have multiple trainers              |
| **Member — books — Session**            | 1:N         | Member: Partial, Session: Total    | A member can book multiple personal-training sessions; each session belongs to one member |
| **Trainer — conducts — Session**        | 1:N         | Trainer: Partial, Session: Total   | A trainer can conduct multiple sessions; each session is conducted by one trainer         |
| **Session — has — Attendance**          | 1:1         | Both: Total                        | Each session has one attendance record                                                    |
| **Member — makes — Payment**            | 1:N         | Member: Partial, Payment: Total    | A member can make multiple payments                                                       |
| **Session — associated with — Payment** | 1:0..1      | Session: Partial, Payment: Partial | A payment may be for a personal-training session; membership payments need no session     |


### Assumptions
- Each member is uniquely identified by a Member_ID.
- A member can join one or more fitness programs, and a program can have multiple members.
- A trainer can be assigned to multiple programs, and each program can have multiple trainers.
- Each personal training session is booked by one member and conducted by one trainer.
- Each session has one attendance record indicating whether the member attended.
- A member can make multiple payments for memberships and personal training sessions.
- A payment for a membership does not require a Session_ID; therefore, Session_ID is optional in PAYMENT.
- The associative entities MEMBER_PROGRAM and PROGRAM_TRAINER are used to resolve the M:N relationships.

---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_library.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_restaurant.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
