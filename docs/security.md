# Security Architecture – This or That Voting System

## 1. Introduction

This document describes the security architecture and threat model of the system.

The system was designed with security as a core requirement, following the principles of:
- Least privilege
- Isolation between components
- Minimized attack surface
- Defense in depth

---

## 2. Assets

The main assets to protect include:

- Poll definitions
- Voting results and counters
- System availability
- Administrative interfaces
- Backend services and data stores

---

## 3. Threat Model

### 3.1 Attack Surface

The main exposed attack surfaces of the system are:

- Public API endpoints:
  - Vote submission endpoint
  - Results query endpoint
- Admin API endpoints:
  - Poll creation endpoint
- Public web interfaces served via CloudFront
- API Gateway endpoints
- AWS IAM roles and permissions

---

### 3.2 Attack Vectors

Potential attack vectors include:

- Automated vote spamming (bot attacks)
- Parameter tampering in API requests
- Denial of Service (DoS) attempts on public endpoints
- Unauthorized access to admin APIs
- Privilege escalation through overly permissive IAM roles
- Data exposure through misconfigured logging
- Injection of malformed or malicious input data

---

## 4. Security Controls and Mitigations

The system implements the following security controls:

### 4.1 API Layer Protection

- API Gateway request validation is used to validate input structure.
- Rate limiting and throttling are applied to public endpoints to reduce abuse.
- Separate API endpoints are used for public and admin operations.

### 4.2 Identity and Access Management

- Each Lambda function runs under a dedicated IAM role.
- Each role follows the principle of least privilege.
- No Lambda function has direct access to resources it does not require.

### 4.3 Data Protection

- No direct access to DynamoDB is allowed from outside the backend services.
- All data access is performed only through controlled backend APIs.
- HTTPS is enforced for all external access via CloudFront and API Gateway.

### 4.4 Workflow Isolation

- The orchestration layer (Step Functions) controls the execution order of sensitive operations.
- Individual processing steps are isolated into separate Lambda functions.

---

## 5. Identity and Access Management (IAM)

The IAM model follows these principles:

- Separate roles for:
  - Public API Lambdas
  - Admin API Lambdas
  - Workflow orchestration
- No wildcard ("*") permissions are used unless strictly necessary.
- Each role is limited to:
  - Specific DynamoDB tables
  - Specific CloudWatch log groups
  - Specific Step Functions workflows

---

## 6. Logging and Monitoring

- All Lambda functions write logs to CloudWatch Logs.
- The following events are monitored:
  - Number of votes submitted
  - Error rates
  - Failed validations
  - Throttling events
- These logs support:
  - Security auditing
  - Incident investigation
  - Operational troubleshooting

---

## 7. Summary

This document presented the security architecture and threat model of the system, including the identified attack surfaces, attack vectors, and the mitigation strategies applied in the design.
