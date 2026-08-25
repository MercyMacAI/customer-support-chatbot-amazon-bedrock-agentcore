# Customer Support Chatbot with Amazon Bedrock AgentCore

An AI-powered customer support agent built with **Amazon Bedrock AgentCore** that classifies customer requests, routes them to appropriate workflows, answers FAQ-based questions, and creates persistent bug reports through AWS services.

## Overview

Built as part of the **AWS Future Agent Engineer** learning journey, this project demonstrates practical implementation of:

- Agentic AI and prompt engineering
- Request classification and routing
- Multi-turn information collection
- Tool calling
- FAQ grounding
- Prompt-injection protection
- AWS serverless integration
- Automated testing and LLM evaluation

## Architecture

```text
Customer Message
       |
       v
Amazon Bedrock AgentCore Harness
       |
       v
Request Classification
       |
   +---+-------------------+
   |           |           |
   v           v           v
BUG REPORT    FAQ       OTHER REQUEST
   |           |           |
   v           v           v
Collect       FAQ        Human Support
Details       Response      Handoff
   |
   v
AgentCore Gateway
   |
   v
AWS Lambda
   |
   v
Amazon DynamoDB

# Key Capabilities 

## Intelligent Request Routing

Incoming customer messages are classified into distinct support behaviors and routed accordingly.

## Bug Report Collection

The assistant collects three required fields before creating a bug report:

## Bug description
## Steps to reproduce
## Customer environment

The bug-report tool is only called after the required information has been collected.

## FAQ Grounding

Platform questions are answered using the provided online_shop_faq.md document.

The system prompt establishes the FAQ as the authoritative source and prevents the assistant from inventing unsupported policies or information.

##Tool Calling##

Completed bug reports are sent through the Amazon Bedrock AgentCore Gateway to an AWS Lambda tool.

##Persistent Storage##

The Lambda tool stores completed bug reports in Amazon DynamoDB, including:

-ticketId
-description
-stepsToReproduce
-environment
-status
c-reatedAt

##Prompt-Injection Protection##

The system prompt instructs the assistant not to reveal:

Hidden system instructions
Internal prompts
Internal reasoning
Tool implementation details
Tool-selection reasoning

Prompt-injection attempts are treated as unsupported requests.

#AWS Services Used#
1. ##Amazon Bedrock AgentCore## — agent harness and gateway
2. Amazon Bedrock — model evaluation
3. Amazon Nova Pro — evaluation model
4. AWS Lambda — bug-report tool
5. Amazon DynamoDB — bug-report persistence
6. AWS CloudFormation — infrastructure provisioning
7. AWS CLI — deployment and verification
8. Python / Boto3 — application and AWS integration
9. Git / GitHub — source control and portfolio documentation

Bug Report Workflow:
Customer reports a problem
          |
          v
Assistant identifies bug report
          |
          v
Collect description
          |
          v
Collect reproduction steps
          |
          v
Collect environment
          |
          v
AgentCore Gateway
          |
          v
AWS Lambda
          |
          v
DynamoDB
          |
          v
Ticket ID returned

This workflow demonstrates how an AI agent can collect information across a conversation before invoking an external tool.

Testing and Evaluation

The project includes test scenarios covering:

Bug reports
Shipping FAQ
Payment methods FAQ
Return policy FAQ
Out-of-scope requests
Prompt-injection attempts

Test definitions are included in:

flow-tests.json
harness-tests.json
Amazon Bedrock Evaluation

The chatbot was evaluated using Amazon Bedrock evaluation.

Evaluation job: support-chatbot-eval-run-1

Evaluator model: amazon.nova-pro-v1:0

Metric: Builtin.Correctness

Evaluation Result

Overall Correctness: 0.83

Five of the six automated test scenarios received a correctness score of 1.0.

Project Outcome

The project was successfully completed and submitted as part of the AWS Future Agent Engineer learning journey.

It received a successful project review, with positive reviewer feedback highlighting the implementation and the chatbot's FAQ-grounded responses.

This repository documents the implementation, testing, evaluation evidence, infrastructure configuration, and lessons learned from building the agent.

# Author #

Mercy Akachukwu Fred-Ekhose

AI Product | Product Management | AI Engineering | Business Technology

GitHub: @MercyMacAI
