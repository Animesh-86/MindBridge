# MindBridge - Mental Health Case Management System

## Overview

MindBridge is a ServiceNow-based Mental Health Case Management platform designed to streamline the process of handling counseling requests, assigning counselors, scheduling appointments, and managing crisis situations.

The system automates counselor allocation, prioritizes crisis cases, balances counselor workloads, and schedules counseling appointments while providing end-to-end visibility into case management operations.

---

## Problem Statement

Educational institutions and organizations often struggle with:

* Manual counselor assignment
* Delayed response to crisis cases
* Uneven counselor workload distribution
* Lack of appointment tracking
* Poor visibility into case lifecycle
* Manual communication and follow-ups

MindBridge addresses these challenges through workflow automation and intelligent routing mechanisms built on the ServiceNow platform.

---

# Key Features

## Case Intake Management

Users can submit counseling requests through a structured intake process containing:

* Emotional description
* Urgency level
* Contact information
* Crisis flag indicator

Each submission automatically generates a unique case record.

---

## Crisis Specialist Routing

When a case is identified as a crisis case:

* The system automatically searches for available counselors.
* Filters counselors by:

  * Status = Available
  * Specialty = Crisis
* Assigns the most suitable counselor.

This ensures critical cases receive immediate attention from trained professionals.

---

## Automatic Counselor Assignment

For non-crisis cases:

The system automatically:

1. Finds available counselors.
2. Checks workload capacity.
3. Assigns the counselor with available capacity.

Conditions:

```text
Status = Available
Active Cases < Maximum Active Cases
```

This prevents counselor overload and ensures balanced distribution.

---

## Counselor Capacity Management

Each counselor record maintains:

* Current Active Cases
* Maximum Active Cases
* Availability Status
* Specialization

Assignment logic ensures counselors do not exceed their configured workload limits.

---

## Appointment Automation

Once a counselor is assigned:

* Appointment records are automatically created.
* Appointment status is initialized as:

```text
Scheduled
```

* Appointment date is generated automatically.

Current implementation schedules appointments dynamically using:

```javascript
var gdt = new GlideDateTime();
gdt.addDaysUTC(1);
return gdt;
```

Result:

Appointments are automatically scheduled for the next day.

---

## Appointment Tracking

Appointment records maintain:

* Appointment Date
* Assigned Counselor
* Related Case
* Status
* Notes

Supported statuses:

* Scheduled
* Completed
* Cancelled
* Rescheduled

---

## Notification System

### Appointment Confirmation

Triggered after appointment creation.

Provides:

* Appointment details
* Counselor information
* Scheduled date and time

---

### Counseling Session Completed

Triggered when a counseling session is marked as completed.

Provides:

* Session completion confirmation
* Case progress updates

---

# Workflow Architecture

## Case Intake Automation

### Crisis Case Flow

```text
Case Created
       ↓
Crisis Flag = True
       ↓
Find Crisis Counselor
       ↓
Available?
       ↓
Assign Counselor
       ↓
Create Appointment
       ↓
Send Confirmation
```

---

### Standard Case Flow

```text
Case Created
       ↓
Find Available Counselor
       ↓
Check Capacity
       ↓
Assign Counselor
       ↓
Create Appointment
       ↓
Send Confirmation
```

---

# Data Model

## MB Case

Stores counseling requests.

Fields:

* Number
* Contact Email
* Emotional Description
* Urgency
* Assigned Counselor
* Status
* Crisis Flag
* Confirmation Token

---

## MB Counselor

Stores counselor information.

Fields:

* Name
* Email
* Availability
* Status
* Specialty
* Active Cases
* Maximum Active Cases
* Crisis Specialist

---

## MB Appointment

Stores appointment information.

Fields:

* Appointment Date
* Case
* Counselor
* Status
* Notes

---

# Business Logic

## Crisis Routing Logic

```text
IF Crisis Flag = True
THEN
Assign Crisis Specialist
```

---

## Capacity Validation

```text
Active Cases < Maximum Active Cases
```

Only counselors satisfying this condition are eligible for assignment.

---

## Appointment Scheduling Logic

```javascript
var gdt = new GlideDateTime();
gdt.addDaysUTC(1);
return gdt;
```

Automatically schedules appointments for the following day.

---

# Technologies Used

## Platform

* ServiceNow Studio
* Flow Designer
* Notifications
* Custom Application Scope

## Development Components

* Custom Tables
* Reference Fields
* Flow Logic
* Record Lookups
* Dynamic Data Pills
* Scripted Date Calculations

---

# Benefits

### Faster Response Time

Automated routing significantly reduces manual assignment delays.

### Crisis Prioritization

Critical mental health cases receive immediate specialist attention.

### Balanced Workload

Counselor assignments are distributed fairly.

### Reduced Administrative Effort

Automated workflows eliminate repetitive manual tasks.

### Improved Case Visibility

Track cases, counselors, and appointments through a centralized platform.

---

# Future Enhancements

* AI-Based Risk Assessment
* Sentiment Analysis
* Automatic Crisis Detection
* Counselor Recommendation Engine
* Follow-up Appointment Automation
* Dashboard & Analytics
* SLA Monitoring
* Real-time Alerts

---

# Project Outcome

MindBridge successfully demonstrates how ServiceNow workflow automation can be leveraged to create an efficient, scalable, and responsive mental health support management system.

The platform automates counselor assignment, prioritizes crisis situations, manages appointment scheduling, and streamlines communication, providing a complete end-to-end mental health case management solution.
