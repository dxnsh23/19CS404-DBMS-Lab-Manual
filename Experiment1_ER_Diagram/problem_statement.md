# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

---

## 🧪 Choose One Scenario:

### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

---

### 🔹 Scenario 2: Hospital Database
Design a database for patient management, appointments, medical records, and billing.

**User Requirements:**
- Patient details including contact and insurance.
- Doctors and their departments, contact info, specialization.
- Appointments with reason, time, patient-doctor link.
- Medical records with treatments, diagnosis, test results.
- Billing and payment details for each appointment.

---

## 📝 Tasks:
1. Identify entities, relationships, and attributes.
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3. Include:
   - Cardinality & participation constraints
   - Prerequisites for University OR Billing for Hospital
4. Explain:
   - Why you chose the entities and relationships.
   - How you modeled prerequisites or billing.

# ER Diagram Submission - Student Name

## Scenario Chosen:
Hospital 

## ER Diagram:
![image](https://github.com/user-attachments/assets/4af61e2a-71d3-4dfc-ba8d-3fef0d949a32)


## Entities and Attributes:

### 📄 1. Patient

| Field   | Description                           |
|---------|---------------------------------------|
| `P-ID`  | Unique identifier for each Patient    |
| `Name`  | Name of the Patient                   |
| `DOB`   | Date of birth of Patient              |
| `Gender`| Gender of Patient                     |
| `Mob-No`| Contact number of the Patient         |
| `Age`   | Age of Patient                        |

---

### 🧑‍💼 2. Employee

| Field    | Description                          |
|----------|--------------------------------------|
| `E-ID`   | Unique identifier for each Employee  |
| `Name`   | Name of the Employee                 |
| `Salary` | Salary of Employee                   |
| `Sex`    | Gender of Employee                   |
| `Mob-No` | Contact number of the Employee       |
| `Address`| Address of Employee                  |
| `State`  | State of Employee                    |
| `City`   | City of Employee                     |
| `Pin-no` | Pin code of Employee                 |

---

### 🥼 3. Doctor

| Field        | Description                                         |
|--------------|-----------------------------------------------------|
| `E-ID`       | Foreign Key referencing `Employee`                  |
| `Department` | Department of the Doctor                            |
| `Qualification` | Qualification of the Doctor                     |

---

### 👩‍⚕️ 4. Nurse

| Field  | Description                                     |
|--------|-------------------------------------------------|
| `E-ID` | Foreign Key referencing `Employee`              |

---

### 🛏️ 5. Room

| Field         | Description                                     |
|---------------|-------------------------------------------------|
| `R-ID`        | Unique identifier for each Room                 |
| `Type`        | Room quality: Deluxe, Private, General, etc.    |
| `Capacity`    | Number of people the room can accommodate       |
| `Availability`| Duration or availability of the room            |

---

### 🧾 6. Receptionist

| Field  | Description                                     |
|--------|-------------------------------------------------|
| `E-ID` | Foreign Key referencing `Employee`              |

---

### 🔬 7. Test Report

| Field       | Description                                     |
|-------------|-------------------------------------------------|
| `R-ID`      | Primary Key - Unique identifier for each Report |
| `P-ID`      | Foreign Key referencing `Patient`               |
| `Test Type` | Type of test (e.g., Blood, MRI, etc.)           |
| `Result`    | Test result                                     |

---

### 💰 8. Bill

| Field    | Description                                     |
|----------|-------------------------------------------------|
| `B-ID`   | Unique identifier for each Bill                 |
| `P-ID`   | Foreign Key referencing `Patient`               |
| `Amount` | Amount the Patient has to pay to the Hospital   |

---

### 📚 9. Records

| Field      | Description                                     |
|------------|-------------------------------------------------|
| `Record-no`| Record number for each patient                  |
| `App-no`   | Appointment number for each patient             |

...

## Relationships and Constraints:
### 1️⃣ Patient-Doctor Relationship

- A **Patient** can consult one or more **Doctors**.
- A **Doctor** can treat multiple **Patients**.
- 🔁 **Type**: Many-to-Many (M:N)

> ✅ **Implementation Tip**: Use a junction/association table like `Patient_Doctor(P-ID, E-ID)` to manage this relationship.

---

### 2️⃣ Nurse-Rooms Relationship

- A **Nurse** can be assigned to multiple **Rooms** during their shift.
- A **Room** can have multiple **Nurses** assigned across different shifts.
- 🔁 **Type**: Many-to-Many (M:N)

> ✅ **Implementation Tip**: Create a link table such as `Nurse_Room(E-ID, R-ID)`.

---

### 3️⃣ Receptionist-Records Relationship

- A **Receptionist** manages multiple **Records** (e.g., appointments, patient logs).
- A **Record** can be handled by multiple **Receptionists**.
- 🔁 **Type**: Many-to-Many (M:N)

> ✅ **Implementation Tip**: Use a mapping table like `Receptionist_Records(E-ID, Record-no)`.

---

### 4️⃣ Patient-Bills Relationship

- A **Patient** can have multiple **Bills**.
- Each **Bill** is tied to only **one Patient**.
- 🔁 **Type**: One-to-Many (1:N)

> ✅ **Implementation Tip**: Place `P-ID` as a foreign key in the `Bill` table.

---

### 5️⃣ Patient-Test Report Relationship

- A **Patient** can have multiple **Test Reports**.
- Each **Test Report** belongs to only one **Patient**.
- 🔁 **Type**: One-to-Many (1:N)

> ✅ **Implementation Tip**: Include `P-ID` as a foreign key in the `Test_Report` table.

---

### 6️⃣ Room-Patient Relationship

- A **Room** can be assigned to multiple **Patients** over time.
- A **Patient** stays in only one **Room** at a time.
- 🔁 **Type**: One-to-Many (1:N)

> ✅ **Implementation Tip**: Use `R-ID` as a foreign key in the `Patient_Room` table, with check-in/check-out dates to track history.
...

## 📌 Extension (Prerequisite / Billing)

### 🔹 Billing Model:
Billing is modeled as a **One-to-Many** relationship between `Patient` and `Bill`.  
- A single patient can generate multiple bills over time due to consultations, tests, surgeries, room charges, etc.
- Each `Bill` is uniquely identified with `B-ID` and contains a foreign key `P-ID` referencing the patient who is liable for payment.
- This design keeps billing modular and traceable per service.

> 💡 If future functionality requires itemized billing, we can extend this with a `Bill_Details` table that captures breakdowns (e.g., doctor fee, room charge, test fees) per `B-ID`.

---

## 🎯 Design Choices

### ✅ Entities:
- We created **core entities** such as `Patient`, `Employee`, `Room`, `Test_Report`, and `Bill` to mirror real-world hospital components.
- The `Employee` table acts as a super-entity for roles like `Doctor`, `Nurse`, and `Receptionist` to avoid redundancy and promote normalization.

### ✅ Relationships:
- **Many-to-Many** relationships (e.g., Patient-Doctor, Nurse-Room, Receptionist-Records) are handled through **junction tables**, which scale better and preserve data integrity.
- **One-to-Many** relationships (e.g., Patient-Bill, Patient-Test Report) ensure that dependent entities like bills and reports are clearly tied to a parent patient.

### ✅ Assumptions:
- Each role (Doctor, Nurse, Receptionist) inherits from a common Employee base using the `E-ID` foreign key.
- A patient can only occupy **one room at a time**, but a room can serve multiple patients over time—tracked via room assignments.
- All time-based associations (e.g., room stay duration) are assumed to be handled via timestamps or logs in extension tables if needed.

> ⚙️ This schema is designed to be normalized, flexible for future enhancements (like treatment history or inventory management), and easy to extend with minimal refactoring.

## RESULT
The experiment successfully demonstrates the design of a normalized relational database schema for a hospital management system.
