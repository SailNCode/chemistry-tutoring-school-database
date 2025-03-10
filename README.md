# Chemistry Tutoring School Database
> This project eases the everyday problems of managing a tutoring school. Including gathering information about the students, their progress and managing payment data.

## Table of Contents
* [General Info](#general-information)
* [Technologies Used](#technologies-used)
* [Features](#features)
* [Screenshots](#screenshots)
* [Setup](#setup)
* [Usage](#usage)
* [Project Status](#project-status)
* [Room for Improvement](#room-for-improvement)
* [Contact](#contact)


## General Information
- Includes setup of DB and declaration of procedures and triggers. Optionally, there is sample data for testing of the functionalities.
- Solves the problems of managing a tutoring school. Including gathering information about students, their progress and managing payment data.
- I am myself a chemistry tutor and I developed that project to save time in the future and reduce probability of error to build a reliable brand.


## Technologies Used
- **PL/SQL:** version 21.0.0
- **T-SQL:** version SQL Server 2016


## Features
### Procedures
#### "addStudent"
> Adds the student to tables: **PERSON**, **STUDENT**, **LANGUAGESPEAKING**; including the passed arguments. In case of unknown arguments, transaction is terminated and message is displayed.
#### "registerPayment"
> Creates a new payment in the **PAYMENT**. This amount is then distributed across individual lesson payments in the **PAYMENTFORLESSON** table, starting with the oldest lessons. If there is a remainder or no lessons left to pay for, a message is printed advising to refund the remaining amount to the payer, and the **PAYMENT** record is updated accordingly.
### Triggers
#### "guardPricePerHourIntegrity"
> Ensures that the lesson price does not exceed the **DefaultPricePerHour** in the **STUDENT** table. If this rule is violated, the lesson price is automatically set to the student’s **DefaultPricePerHour**.
#### "updateRatingAverage"
> After inserting, deleting, or updating a record in the **TUTORREVIEW** table, a new average rating is calculated for each tutor in the **TUTOR** table. The rating is within the range of [1–5].

## Setup
1. **Clone the repository**:
   ```bash
   git clone https://github.com/SailNCode/chemistry-tutoring-school-database.git
   cd chemistry-tutoring-school-database
   ```

2. **Set up the database**:
  - Choose your database platform:
    - For **SQL Server**, navigate to the `ms-sql-server` directory.
    - For **Oracle**, navigate to the `oracle` directory.
  - Run the following files in order:
    - `ddl_drop.sql` optional script to drop tables
    - `ddl_create.sql` script to create tables
3. **(Optionally) Populate with sample data**:
- `dml.sql` script to populate with sample data
4. **Create procedures and triggers**:
- `init.sql` script to create functions, procedures and trigers


## Usage
- Exemplary usages are given under `ms-sql-server` or `oracle` directories inside `testing.sql` file.
- NOTE: Remember to populate DB with sample data in `dml.sql` first to make tests work correctly.


## Project Status
Project is: _finished_


## Room for Improvement

1. Procedure accepting the **STUDENT** as parameter and printing all the subtopics that has been covered in the form of the tree:
> chapter -> topic -> subtopic
2. Trigger for UPDATE and INSERT on **SubtopicCovered** which guards that no **Subtopic** on HL (Higher Level) is assigned to the **STUDENT** on SL (Standard Level).


## Contact
For questions or feedback, feel free to reach out the author:

- **SailNCode**: [GitHub Profile](https://github.com/SailNCode)
