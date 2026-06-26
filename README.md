# MindBridge – AI-Powered Mental Health Case Management System

## Overview

MindBridge is a ServiceNow-based AI-powered Mental Health Case Management platform designed to streamline counseling request management through intelligent case intake, automated counselor assignment, AI-driven risk assessment, appointment scheduling, and counseling session tracking.

The platform combines ServiceNow workflow automation with the Groq LLM to analyze emotional distress, prioritize high-risk cases, balance counselor workloads, generate counseling recommendations, automate appointment management, and provide operational insights through interactive dashboards.

---

## Features

### AI-Powered Mental Health Assessment

MindBridge integrates with the Groq API using the **Llama 3.1 8B Instant** model to perform intelligent analysis of every counseling request.

The AI evaluates:

* Emotional Description
* Mental Health Risk
* Potential Crisis Indicators

It automatically generates:

* AI Risk Level
* AI Summary
* AI Recommendation

These insights assist counselors in prioritizing and responding to cases more effectively.

---

### Smart Case Intake

Students can submit counseling requests through an intuitive intake form.

Each request includes:

* Student Name
* Email Address
* Phone Number
* Emotional Description

Upon submission, the system automatically creates a unique counseling case.

---

### Intelligent Counselor Assignment

MindBridge automatically assigns counselors based on workload and availability.

Assignment Criteria:

* Counselor Status = Available
* Active Cases < Maximum Active Cases

This ensures:

* Balanced workload distribution
* Faster response time
* Reduced manual effort

---

### Crisis Case Prioritization

Cases identified as high-risk through AI analysis are automatically flagged as crisis cases.

The platform prioritizes these requests, enabling counselors to respond quickly to students requiring immediate support.

---

### Appointment Automation

After a counselor is assigned:

* Appointment records are created automatically.
* Appointments are linked to the associated case.
* Status is initialized as **Scheduled**.
* Appointment date is generated automatically.

Students and counselors can track appointments throughout the counseling lifecycle.

---

### Counseling Session Management

Counselors can update appointments by:

* Recording session notes
* Updating appointment status
* Completing counseling sessions

The complete counseling history remains linked to the original case.

---

### Interactive Operations Dashboard

The MindBridge Operations Dashboard provides real-time visibility into counseling activities.

### Overview

Displays:

* Total Cases
* Open Cases
* Resolved Cases
* Crisis Cases

### Analytics & Performance

Provides:

* Case Status Distribution
* Counselor Workload Analysis

Dashboard widgets update automatically as new cases and appointments are processed.

---

## System Architecture

```
Student

      │

      ▼

Case Intake Form

      │

      ▼

AI Risk Assessment (Groq)

      │

      ▼

Risk Classification

      │

      ▼

Counselor Assignment

      │

      ▼

Appointment Creation

      │

      ▼

Counseling Session

      │

      ▼

Case Resolution

      │

      ▼

Operations Dashboard
```

---

## Application Components

### Custom Tables

* MB Case
* MB Counselor
* MB Appointment
* MB Resource

### Business Rules

* AI Risk Assessment
* Counselor Assignment
* Confirmation Token Generation
* Appointment Automation

### Flow Designer

* Case Intake Automation
* Appointment Creation
* Counselor Assignment
* Notification Automation

### Notifications

* Appointment Confirmation
* Counseling Session Updates

### Dashboard

* KPI Cards
* Case Status Distribution
* Counselor Workload

---

## Dashboard Preview

### Overview

<p align="center">
  <img src="https://github.com/user-attachments/assets/8edf3fdc-3787-426e-9d4b-732331bbdecc" alt="Overview Dashboard" width="850"/>
</p>

---

### Analytics & Performance

<p align="center">
  <img src="https://github.com/user-attachments/assets/6b353a57-0ae3-4a7a-a9ff-16099684ff88" alt="Analytics Dashboard" width="850"/>
</p>

---

## Technology Stack

### Platform

* ServiceNow App Engine Studio

### Development

* Business Rules
* Flow Designer
* GlideRecord API
* Client Scripts
* UI Policies
* Notifications
* Platform Analytics Dashboards

### Artificial Intelligence

* Groq API
* Llama 3.1 8B Instant
* RESTMessageV2

---

## Project Structure

```
MindBridge

│

├── Tables

│   ├── MB Case

│   ├── MB Counselor

│   ├── MB Appointment

│   └── MB Resource

│

├── Business Rules

│   ├── AI Risk Assessment

│   ├── Counselor Assignment

│   ├── Confirmation Token

│   └── Appointment Logic

│

├── Flow Designer

│   ├── Case Intake Automation

│   ├── Counselor Assignment

│   └── Appointment Automation

│

├── Notifications

│   ├── Appointment Confirmation

│   └── Session Completion

│

└── Platform Analytics Dashboard
```

---

## Workflow

```
Student Submits Case

      │

      ▼

AI Risk Assessment

      │

      ▼

Assign Counselor

      │

      ▼

Generate Appointment

      │

      ▼

Counseling Session

      │

      ▼

Update Session Notes

      │

      ▼

Resolve Case

      │

      ▼

Dashboard Analytics
```

## Author

**Animesh Sharma**

ServiceNow Certified Application Developer (CAD) • ServiceNow Certified System Administrator (CSA) • Java Backend Developer
