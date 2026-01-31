This or That – Serverless Cloud Voting System
📌 Project Overview

This project implements a cloud-native, serverless, event-driven voting system based on a microservices architecture using Amazon Web Services (AWS).

The system allows users to participate in a simple “This or That” poll, where each poll presents a single question with two possible options (A or B).
Users can vote through a public interface, while administrators can manage polls and observe near real-time voting results via a dedicated dashboard.

The project was developed as part of the Cloud Computing course, with a strong focus on:

Serverless architecture

Event-driven workflows

Managed cloud services

Scalability and fault tolerance

Security and least-privilege design

Clean separation of responsibilities

🎯 System Features
👤 Public User Interface

Hosted via Amazon S3 + CloudFront

Displays the currently active poll

Allows a user to submit a single vote

Vote submission is protected against duplicate voting

🧑‍💼 Admin Interface

Allows manual creation of new polls

Displays aggregated voting results

Results update automatically as votes are received

🏗️ Architectural Principles

The system follows these architectural principles:

Serverless – No servers or infrastructure management

Microservices – Each responsibility is implemented as a separate Lambda function

Event-Driven – The system reacts to API calls and data changes

Stateless Compute – All state is stored in managed services

Scalable by Design – AWS-managed services scale automatically

Highly Available – No single point of failure in the voting flow

Secure by Design – IAM least privilege, isolated services, HTTPS-only access

☁️ AWS Services Used

AWS Lambda – Business logic and microservices

AWS Step Functions – Orchestration of the voting workflow

Amazon API Gateway (HTTP API) – Public and admin endpoints

Amazon DynamoDB – Persistent storage

Amazon DynamoDB Streams – Event source for real-time updates

Amazon API Gateway (WebSocket) – Real-time result distribution

Amazon S3 + CloudFront – Frontend hosting and delivery

Amazon CloudWatch – Logging and monitoring

AWS IAM – Access control and security enforcement

🔁 High-Level System Flow

A user accesses the public voting page via CloudFront.

The frontend fetches the currently active poll using an HTTP API.

The user submits a vote (POST /vote).

API Gateway forwards the request to a vote-wrapper Lambda.

The vote triggers an AWS Step Functions state machine.

The workflow validates the vote and prevents duplicate submissions.

Valid votes are persisted in DynamoDB and results counters are updated.

DynamoDB Streams trigger a real-time update to connected clients via WebSocket.

The admin dashboard reflects updated results automatically.

🧠 Voting Workflow (Step Functions)

The voting process is orchestrated using AWS Step Functions, ensuring a clear and reliable execution flow:

ValidateVote

Verifies required parameters

Checks for duplicate voting using VotesLog

Decision State

Rejects invalid or duplicate votes

SubmitVote

Writes the vote to VotesLog

Updates aggregated counters in GameResults

End State

Successful completion or rejection

This orchestration ensures:

Deterministic execution

Clear separation of concerns

Easy debugging and monitoring

📦 Data Model Overview
DynamoDB Tables

Polls

Stores poll definitions

VotesLog

Records individual votes

Prevents duplicate voting

GameResults

Stores aggregated counters per poll

WebSocketConnections

Tracks active client connections for real-time updates

⚡ Real-Time Updates

Real-time result updates are implemented using an event-driven pattern:

Updates to GameResults trigger DynamoDB Streams

A dedicated Lambda (results-stream-handler) processes stream events

Updated results are broadcast to connected clients via WebSocket API

This approach avoids polling and ensures efficient real-time communication.

🔐 Security Considerations

Security was treated as a core requirement throughout the system design:

Least-privilege IAM roles per Lambda

Separation between public voting APIs and admin functionality

No direct database access from the frontend

HTTPS-only access enforced via CloudFront

Explicit CORS handling through dedicated preflight Lambdas

Full logging and observability via CloudWatch

A detailed threat model including Attack Surface, Attack Vectors, and Mitigations is documented in the project documentation.

🧪 Testing and Validation

The system was validated through:

Manual end-to-end testing of the voting flow

Step Functions execution inspection

DynamoDB state verification

Duplicate vote prevention tests

CORS and API Gateway validation

Real-time update verification via WebSocket

📌 Summary

This project demonstrates a complete serverless, event-driven cloud system, implementing:

Clean microservice separation

Orchestrated workflows with Step Functions

Reliable persistence with DynamoDB

Real-time updates using DynamoDB Streams and WebSockets

Secure, scalable, and maintainable cloud architecture
