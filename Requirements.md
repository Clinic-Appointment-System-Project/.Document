# Clinic Appointment Booking System

## 1. Project Overview

### 1.1 Project Name: 
**Clinic Appointment Booking System**

### 1.2 Purpose

- The Clinic Appointment Booking System is a web-based application that allows patients to search for doctors, view available schedules, and book medical appointments online. The system also provides basic tools for doctors to manage their schedules and appointments. Administrators can manage doctor information. 
- The project focuses on implementing a small and functional appointment booking system .

### 1.3 Project Scope

```text
Patient
 ├── Register / Login
 ├── Manage Profile
 ├── Search & View Doctor
 ├── View Doctor Schedule
 ├── Book Appointment
 └── View / Cancel Appointment
Doctor
 ├── Manage Schedule
 └── Manage Appointments
Admin
 └── Manage Doctors
```

## 2. Actors

### 2.1 Patient

A patient is the main user of the system.

* Register and log in.
* Manage personal information.
* Search for doctors.
* View doctor information.
* View available schedules.
* Book appointments.
* View appointments.
* Cancel eligible appointments.

### 2.2 Doctor

A doctor provides consultation services.

* Log in.
* Manage available working schedules.
* View assigned appointments.
* Update appointment status.

### 2.3 Admin

The administrator performs basic system management.

* Log in.
* Add, edit, view, and deactivate doctors.

## 3. Functional Requirements

### 3.1 Patient Requirements

| ID | Requirement | Description | Priority |
| ----- | ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ----------- |
| FR-01 | Patient Registration & Login | The system shall allow patients to register using name, email, password, and phone number, and log in using their credentials. | Must Have |
| FR-02 | Patient Profile | The system shall allow patients to view and update their basic information, including name, phone number, and date of birth.| Should Have |
| FR-03 | Search & View Doctor | The system shall allow patients to search for doctors by name or specialty and view basic doctor information. | Must Have   |
| FR-04 | View Doctor Schedule | The system shall allow patients to view the available appointment slots of a selected doctor | Must Have |
| FR-05 | Book Appointment | The system shall allow patients to select a doctor, available date and time, and enter a reason for the visit to create an appointment. | Must Have |
| FR-06 | View & Cancel Appointment | The system shall allow patients to view their appointments and cancel eligible appointments | Must Have |

### 3.2 Doctor Requirements

| ID | Requirement | Description | Priority |
| ----- | ------------------- | ------------------------------------------------------------------------------------------------- | --------- |
| FR-07 | Manage Schedule | The system shall allow doctors to create, view, update, and delete their available working slots. | Must Have |
| FR-08 | Manage Appointments | The system shall allow doctors to view their appointments and update appointment status.| Must Have |

### 3.3 Admin Requirements

| ID | Requirement | Description | Priority |
| ----- | ----------- | ---------------------------------------------------------------------- | ----------- |
| FR-09 | Doctor Management | The system shall allow admins to add, view, edit, and deactivate doctor accounts. | Should Have |

## 4. Appointment Status

| Status | Description |
| ----------- | ------------------------------------------------------------------------ |
| `PENDING`   | The patient has created the appointment and is waiting for confirmation. |
| `CONFIRMED` | The doctor has confirmed the appointment.  |
| `COMPLETED` | The appointment has been completed.  |
| `CANCELLED` | The appointment has been cancelled.  |

### Status Flow

```text
PENDING → CONFIRMED → COMPLETED
PENDING → CANCELLED
CONFIRMED → CANCELLED
```

## 5. Business Rules

| ID | Business Rule |
| ----- | ---------------------------------------------------------------------------------------- |
| BR-01 | Each appointment must belong to exactly one patient and one doctor. |
| BR-02 | A doctor cannot have more than one appointment at the same date and time. |
| BR-03 | A patient cannot have more than one appointment at the same date and time. |
| BR-04 | Patients can only book available time slots belonging to the selected doctor's schedule. |
| BR-05 | Patients cannot create appointments for a date or time in the past. |
| BR-06 | A patient can cancel an appointment only when its status is `PENDING` or `CONFIRMED`. |
| BR-07 | A `COMPLETED` appointment cannot be cancelled by the patient. |
| BR-08 | When an appointment is cancelled, its time slot becomes available again. |
| BR-09 | Doctors can only manage their own schedules and appointments. |
| BR-10 | Patients can only view and manage their own appointments. |
| BR-11 | Only admins can create, edit, or deactivate doctor accounts. |

## 6. Non-Functional Requirements

### NFR-01 — Performance

The system should respond to normal operations such as login, doctor search, viewing schedules, and booking appointments within approximately **2–3 seconds** under normal network conditions.

### NFR-02 — Security

The system shall:

* Hash passwords before storing them.
* Never store passwords as plain text.
* Require authentication for protected functions.
* Restrict functions according to user roles.
* Prevent patients from accessing other patients' appointments.
* Prevent doctors from modifying another doctor's schedule.
* Validate user input on the backend.

### NFR-03 — Data Integrity

The system shall maintain consistent appointment data:

* Patient email must be unique.
* Doctor email must be unique.
* Appointment must reference an existing patient.
* Appointment must reference an existing doctor.
* Appointment must reference a valid schedule/time slot.
* The same doctor cannot have two appointments at the same time.
* The same patient cannot have two appointments at the same time.

### NFR-04 — Usability

The system should:

* Provide simple navigation.
* Use clear forms for registration and appointment booking.
* Display clear validation messages.
* Display success and error messages.
* Clearly show appointment status.
* Work on desktop and mobile screen sizes.

### NFR-05 — Reliability

The system should prevent duplicate bookings. If two patients attempt to book the same doctor's time slot at approximately the same time, only one booking should be successfully created.

### NFR-06 — Maintainability

The application should use a simple modular architecture.

```text
Frontend
├── components
├── pages
├── services
└── utils

Backend
├── routes
├── controllers
├── services
├── middleware
└── database
```

## 7. System Constraints

The MVP is limited to basic clinic appointment management.
The following features are outside the scope and can be implemented later in the future version :

* Online payment
* SMS notification
* Email notification
* Video consultation
* Real-time chat
* AI diagnosis
* Medical records
* Insurance management
* Pharmacy management
* Laboratory management
* Online prescription
* Advanced reporting
* Multiple clinic/hospital branches
  These features may be considered for future versions.

## 8. Main Business Flow

```text
Patient
 ↓
Register / Login
 ↓
Search Doctor
 ↓
View Doctor
 ↓
View Available Schedule
 ↓
Select Date & Time
 ↓
Book Appointment
 ↓
PENDING
 ↓
Doctor Reviews Appointment
 ↓
CONFIRMED
 ↓
Patient Visits Doctor
 ↓
COMPLETED


Patient
   │
   ▼
View Appointment
   │
   ▼
Cancel Appointment
   │
   ▼
CANCELLED
   │
   ▼
Time Slot Available