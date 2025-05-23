# Database Essentials and Relational Model

## Data, Database and Information
- Data is facts that can be recorded and/or stored
    - Data is the core of the digital world
- Database is a storage to store data (a computer)
- Information is processed and organized data that provides meaningful context

## DBMS and Why DBMS?
- DBMS --> Database Management System
    - A piece of software to manage data
- Why DBMS?
    - Manage data in a structured way
    - Reduce/Remove redundancy and maintain consistency
    - Security and access management
- SQL --> Structured Query Language

## Different Types of Database Model
- Hierarchical
- Network
- Relational (i.e. MySQL, PostgreSQL)
- Document (i.e. MongoDB)
- Key value (i.e. Radis)

## Anatomy of a Table/Relation (What a DBMS Table can have)
- Entity --> Name of the table or which type of data will be stored in the table in RDBMS
- Column / Attribute --> Which data will be stored.
- Constraint / Domain --> What type of data must be stored in the column
- Degree --> Collection of column
- Rows / Records / Tuples --> Refer to each row of a table
- Cardinality → Collection of rows

## Key and Type of Keys in RDBMS
- Key --> A field or combination of fields that uniquely identifies a record in a table
- Types of keys
    - Super key --> Attribute or set of attributes by which identify a record uniquely
    - Candidate key --> Super key whose proper subset is not a super key
        - Which set of key doesn’t give any more super key after breaking in subsets
    - Primary key --> That doesn’t change, not null and unique
        - Any one of the candidate key that uniquely identify a record
    - Alternate key --> Candidate keys that aren’t chosen as primary key
    - Composite key --> Set of more than one attribute that uniquely identify a record
    - Foreign key --> A key in a table that exists as a primary key in another table
        - Make connections between multiple tables


## Database Design

### SDLC --> Software Development Life Cycle
- Planning --> What need to build
- Analysis --> Can it be build, Can it be build in budged, Capability to build
- System Design --> Build structure of the system
- Building --> Coding Part
- Testing --> Is it ok, Meet the expectation
- Deployment --> Release the final product

### Techniques to design DB
- Top-down --> System build from a2z
- Bottom-up --> Build/Reshape from an existing system
- Hybrid --> Mix of Top-down and Bottom-up

### ER Diagram --> Entity-Relationship Diagram
- Visual representation used in DB design to illustrate the relationships between entities

### Steps of Top-down technique
- Step-1: Determining Entities
- Step-2: Determining Attributes for each Entities
- Step-3: Relationships among Entities

### Characteristics of Entity (Table)
- Can be Place, Person, or thing
- Have some Properties or Attribute
- Must have Unique Identifier (Primary Key)
- Should contain more than one instance of data

### ER Diagram Symbols
- Entity → Rectangle (▭)
- Attribute → Oval (⬭)
- Relationship → Diamond (◇)
- Connection → Line ( — )
- Primary Key → Attribute name with underline ( <u>ID</u> )

### Cardinality
- One-to-One (1:1) → One person has one passport
- One-to-Many (1:N) → One department has many students
- Many-to-One (N:1) → Many employee works in one company
- Many-to-Many (N:N) → One student can take many courses and one course has many students
- Optional One-to-One (0..1:0..1) → A student may or may not taken any course or a course may or may not taken by any student
- Optional One-to-Many (0..1:N) → A student may or may not taken any course but must be a student of an academy

### Resolving Many-to-Many (N:N) with Junction Table
- Introduce a new table with columns that causing N:N relation
    - This will help to reduce N:N --> 1:N & N:1

### Other Notes
- Database Design is a part of System Design
- Purpose of DB Design --> Structured organization for efficient DB management and retrieval


# Database Normalization, Postgres Installation, and Application Insights

## Anomalies
- Type of Anomalies
    - Update Anomalies
    - Delete Anomalies
    - Insert Anomalies
- Solution to resolve Anomalies --> **Normalization**

## Normalization
- Functional Dependency
    - One attribute value can define other attribute/attributes value uniquely
    - X --> Y [X can define Y] or [Y depends on X]
        - t<sub>1</sub>.x = t<sub>2</sub>.x <br />then, t<sub>1</sub>.y = t<sub>2</sub>.y
    - A --> B, C [A can Define both B, and C] or [B, and C depends on A]
- Normal Form
    - 1st Normal Form
    - 2nd Normal Form
    - 3rd Normal Form
- Lossy Decomposition --> Data loss during normalization
    - Solution --> Include reference column and use foreign key
- Lossless Decomposition --> No data loss during normalization

### 1st Normal Form (1NF)
- Rules:
    - Atomic Values (One column must contain only one value)
    - Unique Column Name (Table can't have multiple columns with same name)
    - Positional Dependency of Data (Order doesn't matter)
    - Column should contain data that are of the same type (Data type must be same for a single column)
    - Determine Primary key

### 2nd Normal Form (2NF)
- Rules:
    - Must be in 1NF
    - Must not contain any non-prime/non-key attribute that is functionally dependent on a proper subset of any candidate key of the relation
- In simple way --> If primary key is a composite key and any non-primary key attribute is depended on a part of the primary key then the table is not in 2NF
- Solution --> Break a single table into multiple tables and connect tables using foreign key

### 3rd Normal Form (3NF)
- Rules:
    - Must be in 2NF
    - Must not contain transitive dependency
        - X --> Y & Y --> Z then, X --> Z [Finding values through other column value]


# Postgres
- Postgres is a Database Management System based on RDBMS

## Why Postgres?
- Open Source → Many developer to help and continuous upgrade
- RDBMS → Based on Relational DBMS
- Modern → Moderen technology supported
- ACID Compliance
- Advanced Data Types → Support advanced data types
- Scalability → Both vertically or horizontally scalable
- Indexing
- Community Support → Vast community to help
- Popularity and Demand → More popular and demanding than MongoDB or MySQL

## SQL Shell (psql)
- Basic Commands
    - Basic Commands in SQL Shell (psql):
    - Check version → ```select version();```
    - Database List → ```\l```
    - Go to different DB → ```\c <db_name>``` i.e: ```\c template1```
    - Show relations/table list (with vue) in a DB → ```\d```
    - Show relations/table list in a DB with more info → ```\d+```
    - Show relations/table list without vue → ```\dt```
    - Create a Table in DB → ```create table <table_name>(<attribute_name <attribute_type>(<attribute_length>));``` i.e: ```create table test_table(name varchar(50));```
    - Show schema → ```\dn```
    - Clear SQL Shell Console → ```\! cls```
    - Show connection information → ```\conninfo```
    - Quit SQL Shell Console → ```\q```

# Case Study

A Medical Database System is needed to enhance the efficiency and effectiveness of healthcare services. This system will be able to seamlessly integrates the information of patients, doctors, appointments, medical records, and medical facilities.

**Entities:**

1. **Patients:**
    - Attributes: PatientID (Primary Key), FirstName, LastName, DateOfBirth, Gender, ContactNumber, Email
2. **Doctors:**
    - Attributes: DoctorID (Primary Key), FirstName, LastName, Specialization, ContactNumber, Email
3. **Appointments:**
    - Attributes: AppointmentID (Primary Key), PatientID (Foreign Key), DoctorID (Foreign Key), AppointmentDate, AppointmentTime, Status
4. **Medical Records:**
    - Attributes: RecordID (Primary Key), AppointmentID (Foreign Key), Diagnosis, Prescription, TestResults, createdAt
5. **Medical Facilities:**
    - Attributes: FacilityID (Primary Key), FacilityName, Location, ContactNumber

**Relationships:**
- Patients can have multiple appointments with different doctors.
- Doctors can have multiple appointments with different patients.
- Each appointment may have a corresponding medical record, and vice versa.
- A medical facility can have multiple doctors, and a doctor can work in multiple medical facilities. This relationship is represented through a junction table.

## **Solution**
![ER Diagram Solution](https://i.ibb.co/RTBpTbLs/Case-Study.jpg)