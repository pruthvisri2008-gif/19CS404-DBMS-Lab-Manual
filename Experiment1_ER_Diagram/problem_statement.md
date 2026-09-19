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

<img width="893" height="526" alt="image" src="https://github.com/user-attachments/assets/dbd344ab-2d72-4eab-abdb-585a7977e8fc" />


### Entities and Attributes

<img width="838" height="502" alt="image" src="https://github.com/user-attachments/assets/cf8dc421-c4aa-4408-8c91-93530d5917ff" />


### Relationships and Constraints

<img width="842" height="531" alt="image" src="https://github.com/user-attachments/assets/67328b6c-62a0-4337-a15f-5ef2baa20e81" />


### Assumptions

Every trainer can teach one or more programs.
Members may join multiple fitness programs.
Attendance is recorded for every session
Payments are made only by registered members.


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

<img width="873" height="500" alt="image" src="https://github.com/user-attachments/assets/886f99e9-cf4a-4eb5-82e3-890b5cc67203" />


### Entities and Attributes

<img width="847" height="340" alt="image" src="https://github.com/user-attachments/assets/adcefc88-7274-4d1b-bea3-875dc2fb7b7c" />


### Relationships and Constraints

<img width="840" height="351" alt="image" src="https://github.com/user-attachments/assets/c2d33795-e7e7-4da6-8313-d9864fbe7468" />


### Assumptions

Only registered members can borrow books.
Members may register for multiple events.
Every event has at least one speaker.
A book can be borrowed many times at different periods.

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

<img width="877" height="490" alt="image" src="https://github.com/user-attachments/assets/6d87b48d-0376-4af4-86b3-51246bf96412" />


### Entities and Attributes

<img width="846" height="367" alt="image" src="https://github.com/user-attachments/assets/87b80f17-ebb2-4e27-9dea-393dc3c92af7" />


### Relationships and Constraints

<img width="835" height="343" alt="image" src="https://github.com/user-attachments/assets/208003c7-b4ae-426a-afa8-e3637be9f1de" />


### Assumptions

Only customers can make reservations.
Every reservation is served by one waiter
Multiple dishes can be included in a single order.


## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
