# This or That - Serverless Cloud Voting System

## 📌 Project Overview

This project implements a **cloud-native, serverless, event-driven voting system** based on a **Microservices architecture** using Amazon Web Services (AWS).

The system allows users to participate in a simple **"This or That"** poll, where each poll presents a single question with two possible options.  
Users can vote via a public interface, while administrators can manage polls and view **real-time updated results** through a dedicated dashboard.

The project was developed as part of the **Cloud Computing course**, with a strong emphasis on:
- Serverless architecture
- Event-driven systems
- Scalability and high availability
- Security and least-privilege design
- Managed cloud services

---

## 🎯 System Features

### 👤 Public User Interface
- Accessed via a public URL
- Displays the currently active "This or That" poll
- Allows the user to vote for one of two options
- Submits the vote as a one-time action

### 🧑‍💼 Admin Interface
- Allows manual creation of new polls
- Displays voting results in a graphical dashboard
- Results are updated continuously (near real-time)

---

## 🏗️ Architectural Principles

The system is built according to the following principles:

- **Serverless** – No servers or EC2 instances are managed
- **Microservices** – Each responsibility is implemented as a separate service
- **Event-Driven** – The system reacts to user actions and data changes
- **Scalable by Design** – All components rely on managed AWS services
- **Highly Available** – No single point of failure in the core flow
- **Secure by Design** – Least-privilege IAM, isolated services, protected APIs

---

## ☁️ Main AWS Services Used

- **AWS Lambda** – Business logic and microservices
- **AWS Step Functions** – Orchestration of the voting workflow
- **Amazon API Gateway** – Public and admin APIs
- **Amazon DynamoDB** – Persistent storage for polls and results
- **Amazon S3 + CloudFront** – Hosting and delivery of the frontend
- **Amazon CloudWatch** – Logging and monitoring
- **AWS IAM** – Access control and security enforcement

---

## 🔁 High-Level System Flow

1. A user accesses the public voting page via CloudFront.
2. The system retrieves the currently active poll.
3. The user submits a vote.
4. The vote is processed through an orchestrated serverless workflow.
5. The results are stored and counters are updated.
6. The admin dashboard periodically fetches updated results and refreshes the chart.

---

## 🔐 Security Considerations

The system was designed with security as a core requirement:

- Least-privilege IAM roles per service
- Separation between public and admin APIs
- API Gateway request validation and throttling
- No direct access to the database from outside
- HTTPS-only access via CloudFront
- Monitoring and logging using CloudWatch

A full threat model including **Attack Surface**, **Attack Vectors**, and **Mitigations** is documented in the project documentation.



