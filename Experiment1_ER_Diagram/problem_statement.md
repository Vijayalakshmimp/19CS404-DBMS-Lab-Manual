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
<img width="1276" height="849" alt="image" src="https://github.com/user-attachments/assets/b73edeb5-766b-4b41-945b-dfd7abb8cc01" />


### Entities and Attributes
| Entity              | Attributes (PK, FK)                                                                                | Notes                                                    |
| ------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
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
<img width="928" height="622" alt="image" src="https://github.com/user-attachments/assets/f3205757-bb4b-486b-8130-e2a285228493" />


### Entities and Attributes

| Entity                 | Attributes (PK, FK)                                                                               | Notes                                                  |
| ---------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------ |
| **MEMBER**             | **Member_ID (PK)**, Name, Email, Phone                                                            | Stores library member details                          |
| **BOOK**               | **Book_ID (PK)**, Title, Author, Category                                                         | Stores book information                                |
| **LOAN**               | **Loan_ID (PK)**, Member_ID (FK), Book_ID (FK), Loan_Date, Return_Date                            | Records book borrowing and return details              |
| **EVENT**              | **Event_ID (PK)**, Event_Name, Event_Date, Event_Time                                             | Stores library cultural events                         |
| **SPEAKER**            | **Speaker_ID (PK)**, Speaker_Name, Speaker_Type                                                   | Stores speakers/authors participating in events        |
| **EVENT_SPEAKER**      | **Event_ID (PK, FK)**, **Speaker_ID (PK, FK)**                                                    | Associative entity for events having multiple speakers |
| **EVENT_REGISTRATION** | **Registration_ID (PK)**, Event_ID (FK), Member_ID (FK), Registration_Date                        | Records members registering for events                 |
| **ROOM**               | **Room_ID (PK)**, Room_Name, Capacity                                                             | Stores library room details                            |
| **ROOM_BOOKING**       | **Booking_ID (PK)**, Room_ID (FK), Member_ID (FK), Event_ID (FK, optional), Booking_Date, Purpose | Records room bookings for events or study              |
| **FINE**               | **Fine_ID (PK)**, Loan_ID (FK), Amount, Fine_Date, Payment_Status                                 | Records overdue fines for late book returns            |


### Relationships and Constraints

| Relationship                       | Cardinality | Participation                        | Notes                                                                                                                           |
| ---------------------------------- | ----------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------- |
| **Member — borrows — Book**        | M:N         | Both: Partial                        | A member can borrow many books; a book can be borrowed by different members over time. Implemented using **LOAN**.              |
| **Member — registers for — Event** | M:N         | Both: Partial                        | A member can register for multiple events, and an event can have multiple registered members.                                   |
| **Event — has — Speaker**          | M:N         | Event: Total, Speaker: Partial       | Each event has one or more speakers/authors; a speaker may participate in multiple events. Implemented using **EVENT_SPEAKER**. |
| **Event — uses — Room**            | 1:1         | Event: Total, Room: Partial          | Each event is assigned a room; a room can host different events at different times.                                             |
| **Member — books — Room**          | 1:N         | Member: Partial, Room_Booking: Total | A member can make multiple room bookings for study.                                                                             |
| **Loan — incurs — Fine**           | 1:0..1      | Loan: Partial, Fine: Total           | A loan may have a fine only if the book is returned late.                                                                       |


### Assumptions
- Each member is uniquely identified by Member_ID.
- A book can be borrowed multiple times by different members over time, but each LOAN record represents one borrowing transaction.
- An event must have at least one speaker or author.
- A member may register for multiple events, and an event may have multiple registered members.
- A room can be booked for either an event or individual study.
- Event_ID in ROOM_BOOKING is optional because study-room bookings are not associated with an event.
- A fine is generated only when a book is returned after its due date.
- Each loan can have at most one fine.

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
<img width="1310" height="870" alt="image" src="https://github.com/user-attachments/assets/dba77b92-0f5c-48bd-a1c7-68c4e57e2729" />


### Entities and Attributes
| Entity          | Attributes (PK, FK)                                                                             | Notes                                                             |
| --------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| **CUSTOMER**    | **Customer_ID (PK)**, Name, Phone, Email                                                        | Stores customer details                                           |
| **RESERVATION** | **Reservation_ID (PK)**, Customer_ID (FK), Waiter_ID (FK), Res_Date, Res_Time, No_of_Guests     | Stores table reservation details                                  |
| **WAITER**      | **Waiter_ID (PK)**, Waiter_Name, Phone                                                          | Stores waiter details                                             |
| **ORDER**       | **Order_ID (PK)**, Reservation_ID (FK, optional), Order_Time, Order_Type                        | Stores food orders; Reservation_ID is optional for walk-in orders |
| **ORDER_ITEM**  | **Order_ID (PK, FK)**, **Dish_ID (PK, FK)**, Quantity, Unit_Price                               | Represents dishes included in an order                            |
| **DISH**        | **Dish_ID (PK)**, Dish_Name, Price, Category_ID (FK)                                            | Stores individual dishes                                          |
| **CATEGORY**    | **Category_ID (PK)**, Category_Name                                                             | Categories include Starter, Main, and Dessert                     |
| **BILL**        | **Bill_ID (PK)**, Order_ID (FK), Bill_Date, Sub_Total, Service_Charge, Tax_Amount, Total_Amount | Stores billing information for an order                           |


### Relationships and Constraints
| Relationship                           | Cardinality | Participation                              | Notes                                                                                   |
| -------------------------------------- | ----------- | ------------------------------------------ | --------------------------------------------------------------------------------------- |
| **Customer — makes — Reservation**     | 1:N         | Customer: Partial, Reservation: Total      | A customer can make multiple reservations; each reservation belongs to one customer.    |
| **Reservation — places — Order**       | 1:N         | Reservation: Partial, Order: Total/Partial | A reservation can have multiple orders. Walk-in orders may exist without a reservation. |
| **Reservation — assigned to — Waiter** | N:1         | Reservation: Total, Waiter: Partial        | Each reservation is assigned to one waiter; a waiter can serve multiple reservations.   |
| **Order — contains — Order_Item**      | 1:N         | Both: Total                                | Each order contains one or more order items.                                            |
| **Order_Item — belongs to — Dish**     | N:1         | Order_Item: Total, Dish: Partial           | Each order item refers to one dish; a dish can appear in many order items.              |
| **Dish — belongs to — Category**       | N:1         | Dish: Total, Category: Partial             | Each dish belongs to one category; a category can contain many dishes.                  |
| **Order — generates — Bill**           | 1:1         | Both: Total                                | Each order generates one bill containing food, service, and applicable tax charges.     |


### Assumptions
- Each customer is uniquely identified by Customer_ID.
- A customer can make multiple reservations, but each reservation belongs to only one customer.
- Reservation_ID is optional for an ORDER because walk-in customers can place orders without making a reservation.
- Each order contains at least one dish, represented through ORDER_ITEM.
- Each dish belongs to exactly one category: Starter, Main, or Dessert.
- A waiter can serve multiple reservations, but each reservation is assigned to one waiter.
- Each order generates one bill containing the food subtotal, service charge, tax, and total amount.
- Unit_Price in ORDER_ITEM records the price of the dish at the time of ordering, so later price changes do not affect historical orders.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
