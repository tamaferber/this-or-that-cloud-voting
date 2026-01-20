# System Architecture – This or That Voting System

## 1. Introduction

This document describes the high-level architecture of the "This or That" serverless voting system, developed as part of the Cloud Computing course.

The system is a cloud-native, serverless, event-driven application based on a microservices architecture. It allows users to vote on a simple two-option poll, while administrators can manage polls and monitor real-time results.

The design focuses on:
- Serverless architecture
- Event-driven flow
- Scalability and high availability
- Security by design
- Use of managed AWS services

---

## 2. High-Level System Overview

The system consists of the following main parts:

- Public User Interface (Voting UI)
- Admin Interface (Management Dashboard)
- Serverless Backend (Microservices)
- Persistent Storage
- Monitoring and Logging Infrastructure

At a high level, users access the system through a web interface, submit votes, and the system processes and stores them using serverless cloud services. Administrators can create new polls and view updated results through a separate dashboard.

---

## 3. Architectural Style

The system is designed according to the following architectural principles:

- Serverless architecture – no server management
- Microservices-based design – each responsibility is isolated
- Event-driven processing – actions trigger workflows
- Fully managed cloud services – minimal operational overhead

---

## 4. Logical Components

The system is decomposed into several logical services, each responsible for a single, well-defined task. This separation follows the microservices principle and allows independent scaling, development, and security isolation of each component.

### 4.1 User Interface Service
Responsible for serving the public voting interface.  
This component displays the currently active poll and allows the user to submit a vote.

Responsibilities:
- Display the active "This or That" poll
- Submit user vote requests to the backend

---

### 4.2 Admin Interface Service
Responsible for serving the administrative dashboard.

Responsibilities:
- Display real-time voting results as a graph
- Provide an interface for creating new polls
- Allow administrators to monitor system state

---

### 4.3 Poll Management Service
Responsible for managing poll definitions.

Responsibilities:
- Create new polls
- Store poll questions and options
- Mark a poll as active
- Retrieve the currently active poll

---

### 4.4 Vote Intake Service
Responsible for receiving and validating vote requests from users.

Responsibilities:
- Receive vote submissions
- Validate input data
- Perform basic request validation and filtering
- Forward valid votes to the processing workflow

---

### 4.5 Vote Processing Service
Responsible for processing accepted votes.

Responsibilities:
- Persist the vote
- Update aggregated counters
- Ensure data consistency

---

### 4.6 Results Query Service
Responsible for providing read-only access to aggregated results.

Responsibilities:
- Retrieve current voting results
- Provide data to the admin dashboard
- Provide data in a format suitable for visualization

---

### 4.7 Workflow Orchestration Component
Responsible for orchestrating the voting process.

Responsibilities:
- Coordinate multi-step vote processing
- Ensure each step in the workflow is executed in the correct order
- Handle failures and retries between steps

---

### 4.8 Data Storage Component
Responsible for persistent storage.

Responsibilities:
- Store polls
- Store votes or aggregated counters
- Provide reliable and durable data storage

---

### 4.9 Monitoring and Logging Component
Responsible for observability of the system.

Responsibilities:
- Collect logs from all components
- Provide basic metrics (number of votes, errors, latency)
- Enable debugging and system monitoring


---

## 5. High-Level Architecture Diagram

[Architecture diagram will be added here]

---

## 6. Technology Mapping (AWS Services)

This section maps the logical components to AWS managed services.

(To be filled in later)

---

## 7. Design Considerations

This section describes the main architectural design decisions and their rationale, including:

- Why serverless was chosen
- Why microservices architecture was chosen
- Scalability and availability considerations
- Cost considerations (Free Tier)
- Security considerations (high-level)

---

## 8. Summary

This document presented the high-level architecture of the system and the main design principles guiding its implementation.
