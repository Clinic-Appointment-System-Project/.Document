# Clinic Appointment Booking System


## 1. Project Overview

### 1.1 Project Name

**Clinic Appointment Booking System**

### 1.2 Purpose

- The Clinic Appointment Booking System is a web-based application that allows patients to search for doctors, view available schedules, and book medical appointments online.

- The system also provides doctors with tools to manage their schedules and appointments, while administrators can manage doctors, patients, specialties, and appointments.

### 1.3 Project Scope

- The system focuses on the basic appointment booking process:

```text
Patient
   │
   ├── Register / Login
   ├── Search Doctor
   ├── View Doctor
   ├── View Available Schedule
   ├── Book Appointment
   ├── View Appointments
   └── Cancel Appointment

Doctor
   │
   ├── Login
   ├── Manage Schedule
   ├── View Appointments
   └── Update Appointment Status

Admin
   │
   ├── Login
   ├── Manage Doctors
   ├── Manage Specialities
   ├── Manage Patients
   └── Manage Appointments
```

---

# 2. Actors

- The system contains three main actors.

## 2.1 Patient

- A patient is a user who wants to make an appointment with a doctor.

The patient can:

- Register an account.
- Log in.
- Manage personal information.
- Search for doctors.
- View doctor information.
- View available schedules.
- Book an appointment.
- View personal appointments.
- Cancel appointments.

## 2.2 Doctor

- A doctor is a medical professional who provides consultation services.

The doctor can:

- Log in.
- View personal information.
- Manage working schedules.
- View appointments.
- View patient appointment information.
- Update appointment status.

## 2.3 Admin

- An administrator manages the overall system.

The admin can:

- Log in.
- Manage doctors.
- Manage specialties.
- Manage patients.
- Manage appointments.

---

# 3. Functional Requirements

## 1. User & Authentication Requirements

| ID | Requirement | Description | Priority |
|---|---|---|---|
| FR-01 | User Registration | The system shall allow patients to create an account using full name, email, password, and phone number. The email must be unique. | Must Have |
| FR-02 | User Login | The system shall allow users to log in using email and password and redirect them according to their role. | Must Have |
| FR-03 | Role-Based Access Control | The system shall restrict system functions according to the user's role: Patient, Doctor, or Admin. | Must Have |
| FR-04 | Patient Profile Management | The system shall allow patients to view and update their personal information, including name, phone number, and date of birth. | Should Have |

---

## 2. Doctor & Specialty Requirements

| ID | Requirement | Description | Priority |
|---|---|---|---|
| FR-05 | Doctor Search | The system shall allow patients to search for doctors by name or specialty. | Must Have |
| FR-06 | Doctor Information | The system shall allow patients to view doctor information, including name, specialty, description, experience, and working schedule. | Must Have |
| FR-07 | Doctor Management | The system shall allow admins to add, view, edit, and deactivate doctors. | Must Have |
| FR-08 | Specialty Management | The system shall allow admins to add, view, edit, and deactivate medical specialties. | Must Have |

---

## 3. Doctor Schedule Requirements

| ID | Requirement | Description | Priority |
|---|---|---|---|
| FR-09 | View Doctor Schedule | The system shall allow patients to view the available working schedule of a selected doctor. | Must Have |
| FR-10 | Manage Doctor Schedule | The system shall allow doctors to create, view, edit, and delete their available working periods. | Must Have |
| FR-11 | Schedule Validation | The system shall ensure that appointments can only be booked within the doctor's available working schedule. | Must Have |

---

## 4. Appointment Requirements

| ID | Requirement | Description | Priority |
|---|---|---|---|
| FR-12 | Book Appointment | The system shall allow patients to select a doctor, date, time, and reason for visit to create an appointment. | Must Have |
| FR-13 | Appointment Validation | The system shall validate that the selected date and time are valid, available, and not already booked. | Must Have |
| FR-14 | View Appointments | The system shall allow patients to view their appointments, including doctor, date, time, reason, and status. | Must Have |
| FR-15 | Cancel Appointment | The system shall allow patients to cancel eligible appointments. Cancelled slots shall become available again. | Must Have |
| FR-16 | Doctor Appointment Management | The system shall allow doctors to view appointments assigned to them and patient appointment information. | Must Have |
| FR-17 | Update Appointment Status | The system shall allow doctors to update appointment status, such as Pending, Confirmed, Completed, or Cancelled. | Must Have |
| FR-18 | Admin Appointment Management | The system shall allow admins to view, search, filter, and cancel appointments when necessary. | Must Have |

---

## 5. Patient Management Requirements

| ID | Requirement | Description | Priority |
|---|---|---|---|
| FR-19 | Patient Management | The system shall allow admins to view patient information and activate or deactivate patient accounts. | Should Have |

---

## 6. Dashboard Requirements

| ID | Requirement | Description | Priority |
|---|---|---|---|
| FR-20 | Doctor Dashboard | The system shall provide doctors with a dashboard showing today's, upcoming, completed, and cancelled appointments. | Must Have |
| FR-21 | Admin Dashboard | The system should provide admins with an overview of doctors, patients, specialties, and appointments. | Should Have |

---

# 7. Appointment Status

The system shall support the following appointment statuses:

| Status | Description |
|---|---|
| `PENDING` | Appointment has been created and is waiting for confirmation. |
| `CONFIRMED` | Doctor has confirmed the appointment. |
| `COMPLETED` | The appointment has been completed. |
| `CANCELLED` | The appointment has been cancelled. |

### Status Flow

```text
PENDING
   │
   ▼
CONFIRMED
   │
   ▼
COMPLETED
```

An appointment may also be cancelled:

```text
PENDING ──────► CANCELLED

CONFIRMED ────► CANCELLED
```

---


# 8. Business Rules

| ID | Business Rule |
|---|---|
| BR-01 | A doctor cannot have two appointments at the same date and time. |
| BR-02 | A patient cannot have two appointments at the same date and time. |
| BR-03 | An appointment must be within the doctor's available schedule. |
| BR-04 | Patients cannot create appointments in the past. |
| BR-05 | A completed appointment cannot be cancelled by the patient. |
| BR-06 | When an appointment is cancelled, its time slot becomes available again. |
| BR-07 | Only admins can manage doctors and specialties. |
| BR-08 | Doctors can only manage their own schedules and appointments. |
| BR-09 | Patients can only view and manage their own appointments. |

---

# 5. Non-Functional Requirements

## NFR-01 — Performance

The system should respond to normal user operations within approximately 2–3 seconds under normal network conditions.

---

## NFR-02 — Security

The system shall:

- Hash passwords before storing them.
- Never store passwords as plain text.
- Authenticate protected API requests.
- Authorize requests according to user roles.
- Prevent unauthorized access to user information.
- Validate user input.
- Protect APIs from common security vulnerabilities.

---

## NFR-03 — Data Integrity

The database shall maintain data consistency.

Examples:

- Email addresses must be unique.
- Doctor IDs must reference existing doctors.
- Patient IDs must reference existing patients.
- Appointment records must reference valid doctors and patients.
- A doctor cannot have duplicate appointments at the same time.

---

## NFR-04 — Usability

The system should:

- Have a simple and consistent interface.
- Provide clear navigation.
- Provide form validation.
- Display meaningful error messages.
- Display success messages after important operations.
- Support desktop and mobile screen sizes.

---

## NFR-05 — Reliability

The system should prevent inconsistent appointment data.

For example, two patients attempting to book the same slot at approximately the same time should not result in two successful bookings for the same doctor and slot.

---

## NFR-06 — Maintainability

The application should use a modular architecture.

Example:

```text
Frontend
├── components
├── pages
├── services
├── hooks
└── utils

Backend
├── routes
├── controllers
├── services
├── middleware
└── prisma
```

---

# 6. System Constraints

The first version of the system will focus on basic clinic appointment management.

The following features are outside the scope of the MVP:

- Online payment.
- Real SMS notification.
- Video consultation.
- Real-time chat.
- AI diagnosis.
- Insurance management.
- Pharmacy management.
- Laboratory management.
- Advanced electronic medical records.

-> These features may be considered for future versions.

---

# 7. Requirement Priority

Requirements are divided into three levels.

| Priority | Meaning |
|---|---|
| **Must Have** | Essential for the MVP |
| **Should Have** | Important but can be implemented after core features |
| **Could Have** | Optional/future feature |

### Must Have

- FR-01 User Registration
- FR-02 User Login
- FR-03 Role-Based Access Control
- FR-05 Doctor Search
- FR-06 Doctor Information
- FR-07 Doctor Schedule
- FR-08 Book Appointment
- FR-09 Appointment Validation
- FR-10 View Appointments
- FR-11 Cancel Appointment
- FR-12 Doctor Dashboard
- FR-13 Doctor Schedule Management
- FR-14 View Patient Appointments
- FR-15 Update Appointment Status
- FR-16 Admin Doctor Management
- FR-17 Admin Specialty Management
- FR-19 Admin Appointment Management

### Should Have

- FR-04 Patient Profile Management
- FR-18 Admin Patient Management

### Could Have

- Email notifications
- SMS notifications
- Online payment
- Medical records
- Online consultation
- Real-time chat

---

# 8. MVP Scope for Three-Week Deadline

For a three-week development period, the recommended MVP is:

```text
                    Clinic Appointment System
                              │
        ┌─────────────────────┼─────────────────────┐
        │                     │                     │
      Patient               Doctor                Admin
        │                     │                     │
   ┌────┴─────┐         ┌─────┴─────┐        ┌────┴─────┐
   │          │         │           │        │          │
 Register   Booking   Schedule   Appointment Doctors  Specialty
 Login      Cancel    Management  Management  Management Management
 Search     View
 Doctor     Appointment
```

The primary business flow is:

```text
Patient
   │
   ▼
Search Doctor
   │
   ▼
Select Doctor
   │
   ▼
View Available Schedule
   │
   ▼
Select Date & Time
   │
   ▼
Book Appointment
   │
   ▼
Appointment Created
   │
   ▼
PENDING
   │
   ▼
Doctor Confirms
   │
   ▼
CONFIRMED
   │
   ▼
Patient Visits Doctor
   │
   ▼
COMPLETED
```

- This scope is designed to be achievable within approximately three weeks while still providing enough functionality for database design, REST API development, frontend implementation, authentication, authorization, testing, and deployment.