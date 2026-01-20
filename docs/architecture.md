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

The system is composed of the following logical components:

- User Interface Service
- Admin Interface Service
- Poll Management Service
- Vote Processing Service
- Results Query Service
- Workflow Orchestration Component
- Data Storage Component
- Monitoring and Logging Component

Each component is designed to have a single, well-defined responsibility.

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
