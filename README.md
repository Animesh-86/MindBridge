# MindBridge - AI-Powered Mental Health Case Management System

## Overview

MindBridge is a ServiceNow-based AI-powered Mental Health Case Management platform designed to streamline counseling request management, automate counselor assignment, prioritize high-risk cases, schedule appointments, and generate AI-driven assessments.

The platform combines ServiceNow workflow automation with Groq LLM integration to provide intelligent case triage, counselor workload balancing, appointment management, and session documentation.

---

## Problem Statement

Educational institutions and organizations often face challenges such as:

* Manual counselor assignment
* Delayed response to students in distress
* Uneven counselor workload distribution
* Lack of appointment tracking
* Limited visibility into counseling operations
* Manual session documentation
* Difficulty identifying high-risk cases

MindBridge addresses these challenges through workflow automation, intelligent routing, and AI-assisted analysis.

---

## Key Features

### AI-Powered Case Assessment

When a student submits a counseling request, MindBridge automatically analyzes the emotional description using Groq LLM.

The AI generates:

* Risk Level Classification
* Case Summary
* Counselor Recommendation

Supported Risk Levels:

* Low
* Medium
* High
* Critical

Example:

Student Input:

> "I feel hopeless and overwhelmed. I cannot sleep and sometimes think about hurting myself."

AI Output:

* Risk Level: Critical
* Summary: Signs of emotional distress and potential self-harm indicators detected.
* Recommendation: Immediate counselor intervention required.

---

### Case Intake Management

Students can submit counseling requests through a structured intake form containing:

* Student Name
* Contact Email
* Phone Number
* Emotional Description

Each submission automatically generates a unique case record.

---

### Automatic Counselor Assignment

Once a case is created:

* Available counselors are identified.
* Counselor capacity is evaluated.
* The most suitable counselor is assigned automatically.

Assignment Conditions:

* Status = Available
* Active Cases < Maximum Active Cases

This ensures balanced workload distribution across counselors.

---

### Crisis Case Prioritization

Critical and high-risk cases are prioritized through automated routing logic.

The system can:

* Flag crisis situations
* Assign counselors immediately
* Prioritize urgent interventions

---

### Counselor Capacity Management

Each counselor maintains:

* Availability Status
* Specialty
* Active Cases
* Maximum Active Cases

MindBridge prevents counselor overload by validating capacity before assignment.

---

### Appointment Automation

After counselor assignment:

* Appointment records are generated automatically.
* Appointments are linked to the associated case.
* Status is initialized as Scheduled.

Automatic Scheduling Logic:

```javascript
var gdt = new GlideDateTime();
gdt.addDaysUTC(1);
return gdt;
```

Appointments are automatically scheduled for the next day.

---

### Appointment Tracking

Appointment records maintain:

* Appointment Date
* Related Case
* Assigned Counselor
* Status
* Session Notes
* AI Session Summary
* Follow-up Recommendation

Supported Appointment Statuses:

* Scheduled
* Completed
* Cancelled
* Rescheduled

---

### AI Session Summary Generation

After a counseling session:

1. Counselor enters session notes.
2. AI generates:

   * Session Summary
   * Follow-up Recommendation

This reduces manual documentation effort and improves record consistency.

---

### Notification System

#### Appointment Confirmation

Automatically triggered after appointment creation.

Provides:

* Appointment details
* Assigned counselor information
* Scheduled date and time

#### Session Completion Notification

Triggered when a counseling session is completed.

Provides:

* Session completion confirmation
* Case progress updates

---

## Workflow Architecture

### Student Intake Flow

Student Creates Case
↓
AI Risk Assessment (Groq)
↓
Risk Classification
↓
Counselor Assignment
↓
Appointment Creation
↓
Notification Sent

---

### Counseling Flow

Appointment Scheduled
↓
Counseling Session Conducted
↓
Counselor Adds Session Notes
↓
AI Session Summary Generated
↓
Follow-up Recommendation Created
↓
Case Updated

---

## Data Model

### MB Case

Stores counseling requests.

Fields:

* Number
* Student Name
* Contact Email
* Phone Number
* Emotional Description
* AI Risk Level
* AI Summary
* AI Recommendation
* Assigned Counselor
* Status
* Crisis Flag
* AI Analyzed

---

### MB Counselor

Stores counselor information.

Fields:

* Name
* Email
* Status
* Specialty
* Active Cases
* Maximum Active Cases
* Availability

---

### MB Appointment

Stores appointment information.

Fields:

* Appointment Date
* Related Case
* Counselor
* Status
* Session Notes
* AI Session Summary
* Follow-up Recommendation

---

## AI Integration

MindBridge integrates with Groq LLM through REST APIs.

Process:

Case Description
↓
Groq API
↓
LLM Analysis
↓
Risk Level
Summary
Recommendation
↓
Case Record Updated

Benefits:

* Faster triage
* Improved risk identification
* Reduced manual review effort
* Consistent recommendations

---

## Technologies Used

### Platform

* ServiceNow
* Flow Designer
* Business Rules
* Notifications
* Custom Application Scope

### AI Integration

* Groq API
* Llama 3.1 Model
* RESTMessageV2

### Development Components

* Custom Tables
* Reference Fields
* Flow Automation
* Script Includes
* Async Business Rules
* Dynamic Data Pills

---

## Benefits

### Faster Response Time

Automated routing significantly reduces counselor assignment delays.

### AI-Assisted Triage

Risk assessment helps identify students requiring urgent support.

### Balanced Workload

Counselor assignments are distributed fairly based on capacity.

### Reduced Administrative Effort

Automation minimizes repetitive manual work.

### Improved Documentation

AI-generated summaries streamline counseling records.

### Better Visibility

Centralized tracking of cases, counselors, and appointments.

---

## Future Enhancements

* Resource Recommendation Engine
* Mental Health Resource Library
* AI-Based Counselor Suggestions
* Sentiment Trend Analysis
* Follow-up Appointment Automation
* SLA Monitoring
* Advanced Analytics Dashboard
* Real-Time Crisis Alerts

---

## Project Outcome

MindBridge demonstrates how ServiceNow workflow automation and Generative AI can be combined to create an intelligent, scalable, and responsive mental health support platform.

The system automates case intake, performs AI-powered risk assessment, assigns counselors intelligently, schedules appointments, generates counseling summaries, and streamlines the complete counseling lifecycle from intake to resolution.
