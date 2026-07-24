# NetSuite Teams Assistant

Enterprise self-service assistant that enables Microsoft Teams users to execute NetSuite processes through Copilot Studio, Power Automate, and NetSuite RESTlets.
<img width="1535" height="1024" alt="image" src="https://github.com/user-attachments/assets/5f234c72-e78e-41c5-94d1-653cc0ea61e7" />

[![Ask DeepWiki](https://deepwiki.com/badge.svg)](https://deepwiki.com/orozcoisboseth/netsuite-teams-assistant)

## Overview

NetSuite Teams Assistant is an enterprise solution that allows users to interact with NetSuite directly from Microsoft Teams using natural language.

The solution leverages Microsoft Copilot Studio to understand user intent, collect required information, orchestrate business processes through Power Automate, and execute operations in NetSuite via RESTlets.

By centralizing ERP actions within Teams, employees can complete common business processes without leaving their collaboration environment.

This repository contains architecture documentation, screenshots, integration design, and sample implementations. Sensitive business logic, credentials, and company-specific information have been removed.

## Business Problem

Many business processes require users to access NetSuite to retrieve information or perform operational tasks.

Common challenges include:

Multiple application context switching
Limited ERP familiarity among employees
Manual approval and request processes
Increased training requirements
Slow access to operational information

The objective was to provide a conversational interface within Microsoft Teams that simplifies access to NetSuite functionality.

## Solution Architecture
Microsoft Teams -> Copilot Studio -> Power Automate -> NetSuite RESTlet -> NetSuite ERP

## How It Works
1. User Interaction

The user initiates a conversation with the assistant through Microsoft Teams.

Example:

Create a purchase request for office equipment.

or

Check the status of my PTO request.

2. Intent Detection

Copilot Studio analyzes the user's message and determines the requested business operation.

The agent can:

Detect user intent
Request missing information
Validate required inputs
Guide the user through the process

3. Process Orchestration

Once all required information has been collected, Copilot Studio invokes a Power Automate flow.

4. NetSuite Request Generation

Power Automate is responsible for:
Building the request payload
Generating OAuth authentication headers
Applying business validations
Calling the appropriate NetSuite RESTlet

5. NetSuite Processing

The RESTlet receives the request and executes the requested operation inside NetSuite.

Examples:

Purchase requests
Approval workflows
Record updates
Information retrieval

6. Response Handling

The RESTlet returns the operation result to Power Automate.

Example:
{
  "success": true,
  "message": "Purchase request created successfully",
  "transactionId": "PR-10245"
}

7. User Response

Power Automate returns the result to Copilot Studio.

Copilot Studio generates a user-friendly response and displays it directly in the Teams chat.

Example:

Your purchase request has been submitted successfully.

Request ID: PR-10245

## Design Principles: Low-Code First

The solution prioritizes Microsoft Power Platform capabilities before introducing custom development.

Separation of Responsibilities
Component	ResponsibilityTeams	User experience
Copilot Studio	Conversation and intent handling
Power Automate	Workflow orchestration
RESTlet	NetSuite business execution
NetSuite	Data persistence
Reusable Integration Pattern

New operations can be added by:

Creating a new topic in Copilot Studio.
Extending the Power Automate flow.
Implementing the corresponding RESTlet action.

## Screenshots
### Teams Conversation
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/9c317a18-043e-4262-9a42-db132386c03f" />

### Copilot Studio Topics
<img width="1181" height="684" alt="image" src="https://github.com/user-attachments/assets/70897b12-5b1c-441b-8173-a42baca972af" />

### Copilot topic diagram

<img width="294" height="1521" alt="image" src="https://github.com/user-attachments/assets/fa11c6f0-867d-43e1-823c-4cc7aed7e2cf" />

### Power Automate Flow

<img width="466" height="902" alt="image" src="https://github.com/user-attachments/assets/cf9470f2-5650-410b-a9ca-9ca15ebdfaec" />


## Security Considerations

The production implementation includes:
- OAuth authentication
- Secure HTTP communications
- Identity propagation
- Access control validation
- Error handling
- Auditability

## Disclaimer

This repository is intended for portfolio and educational purposes only.

The implementation shown here has been sanitized to remove proprietary information, internal business logic, credentials, tenant-specific configuration, and confidential data.
