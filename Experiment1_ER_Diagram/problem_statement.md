# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.


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
<img width="1066" height="685" alt="Screenshot 2026-07-27 202540" src="https://github.com/user-attachments/assets/f46bc3ab-9ca7-4bcb-9052-2d40564431ab" />


### Entities and Attributes

| Entity     |                            Attributes (PK, FK)                                              |                        Notes                         |
|------------|---------------------------------------------------------------------------------------------|------------------------------------------------------|

| Member     | **PK:** Member_ID, Member_Name, Membership_Type, Start_Date, Phone_No, Membership_Duration  | Stores member details.                               |
| Membership | **PK:** Membership_ID, **FK:** Member_ID, Program_ID, Join_Date, Status                     | Records member enrollment in programs.               |
| Program    | **PK:** Program_ID, Program_Name, Duration, Schedule, Fees                                  | Stores fitness program details.                      |
| Trainer    | **PK:** Trainer_ID, Trainer_Name, Experience, Phone_No, Specialization                      | Stores trainer information.                          |
| Session    | **PK:** Session_ID, **FK:** Member_ID, Trainer_ID, Session_Date & Time, Attendance_Status   | Records personal training sessions & attendance.|
| Payment    | **PK:** Payment_ID, **FK:** Member_ID, Payment_Date, Amount, Payment_Method, Balance_Amount | Stores membership and session payment details.       |


### Relationships and Constraints

|           Relationship            | Cardinality | Participation |                 Notes                       |
|-----------------------------------|-------------|---------------|---------------------------------------------|
| Member — Enrolls In — Membership  | 1 : N       | Total         | One member can enroll in multiple programs. |
| Membership — Belongs To — Program | N : 1       | Total         | Each membership belongs to one program.     |
| Trainer — Teaches — Program       | M : N       | Partial       | Trainers may teach multiple programs.       |
| Member — Attends — Session        | 1 : N       | Partial       | Members may attend multiple sessions.       |
| Trainer — Conducts — Session      | 1 : N       | Partial       | Trainers conduct multiple sessions.         |
| Member — Makes — Payment          | 1 : N       | Total         | Members can make multiple payments.         |


### Assumptions
- Every member has a unique Member_ID.
- Attendance is recorded for every training session.
- Payments include membership fees and personal training charges.
- Trainers can teach multiple programs.

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
<img width="1600" height="825" alt="WhatsApp Image 2026-07-27 at 21 48 21" src="https://github.com/user-attachments/assets/3c72d884-3511-4128-9eae-383b35a41a07" />


### Entities and Attributes

| Entity  |                                        Attributes (PK, FK)                                             |              Notes                  |  
| ------- | ------------------------------------------------------------------------------------------------------ | ----------------------------------- |
| Member  | **PK:** Member_ID, Member_Name, Address, Membership_Date, Phone_No                                     | Stores library member information.  |
| Book    | **PK:** Book_ID, Title, Category, ISBN, Author                                                         | Stores book details.                |
| Loan    | **PK:** Loan_ID, **FK:** Member_ID, Book_ID, Loan_Date, Due_Date, Return_Date, Fine_Amount             | Records book borrowing information. |
| Event   | **PK:** Event_ID, Event_Name, Event_Date, Event_Time, Room_ID                                          | Stores event details.               |
| Speaker | **PK:** Speaker_ID, Speaker_Name, Expertise, Contact_No                                                | Stores speaker information.         |
| Room    | **PK:** Room_ID, Room_Name, Capacity, Room_Type                                                        | Stores room information for events. |


### Relationships and Constraints

|          Relationship          | Cardinality | Participation |                  Notes                    |
| ------------------------------ | ----------- | ------------- | ----------------------------------------- |
| Member — Borrows — Loan        | 1 : N       | Total         | One member can borrow multiple books.     |
| Loan — Contains — Book         | N : 1       | Total         | Each loan is associated with one book.    |
| Member — Registers For — Event | M : N       | Partial       | Members can register for multiple events. |
| Event — Has — Speaker          | M : N       | Partial       | Events may have multiple speakers.        |
| Room — Hosts — Event           | 1 : N       | Total         | One room can host multiple events.        |


### Assumptions
- A book can be borrowed by only one member at a time.
- Fine amount is calculated from the due date and return date.
- Each event is conducted in one room.
- Members can register for multiple events.
  
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
<img width="1600" height="837" alt="WhatsApp Image 2026-07-27 at 21 51 15" src="https://github.com/user-attachments/assets/1d13f119-7082-4ffa-99b1-8246ac743073" />


### Entities and Attributes

|   Entity    |                                          Attributes (PK, FK)                                                |              Notes               |
| ----------- | ----------------------------------------------------------------------------------------------------------- | -------------------------------- |
| Customer    | **PK:** Customer_ID, Customer_Name, Email, Phone_No                                                         | Stores customer details.         |
| Reservation | **PK:** Reservation_ID, **FK:** Customer_ID, Table_ID, Reservation_Date, Reservation_Time, Number_of_Guests | Stores reservation details.      |
| Table       | **PK:** Table_ID, Table_Number, Capacity, Availability_Status                                               | Stores restaurant table details. |
| Order       | **PK:** Order_ID, **FK:** Reservation_ID, Order_Date, Order_Time                                            | Stores food order information.   |
| Dish        | **PK:** Dish_ID, Dish_Name, Category, Price                                                                 | Stores menu item details.        |
| Bill        | **PK:** Bill_ID, **FK:** Reservation_ID, Food_Charge, Service_Charge, Grand_Total                           | Stores billing information.      |


### Relationships and Constraints

|           Relationship            | Cardinality | Participation |                                     Notes                                       |
| --------------------------------- | ----------- | ------------- | ------------------------------------------------------------------------------- |
| Customer — Makes — Reservation    | 1 : N       | Total         | One customer can make multiple reservations.                                    |
| Table — Assigned To — Reservation | 1 : N       | Partial       | A table can be reserved multiple times on different dates.                      |
| Reservation — Contains — Order    | 1 : N       | Total         | A reservation may include multiple orders.                                      |
| Order — Includes — Dish           | M : N       | Partial       | An order can contain multiple dishes, and a dish can appear in multiple orders. |
| Reservation — Generates — Bill    | 1 : 1       | Total         | One bill is generated for each reservation.                                     |


### Assumptions
- Walk-in customers are also recorded as reservations.
- One reservation is assigned to one table.
- Grand total is calculated from food charges and service charges.
- Each reservation generates only one bill.
