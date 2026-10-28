 MATACS-TH-2026-02: AI Proposal Triage Design

Name: Mohammad Mufrah Jawaid
Assessment Reference: MATACS-TH-2026-02
Time spent: 55 minutes

 Project Overview

This project explains how an AI-assisted tool can review contractor proposals and rank them
based on criteria set by an admin.

AI is used to extract information from proposals. Normal code checks mandatory requirements
and calculates scores. A human reviewer checks the results and makes the final decision.

 Project Files

- [Process Flow Diagram](diagram/diagramflow.png)
- [Design Write-up](WRITEUP.md)
- [AI Prompts](PROMPTS.md)
- [Expected Ranking](ranking.json)

 Design Approach

The system uses AI to read proposal details and organise the information into a consistent
format. Rule-based checks are used for eligibility and score calculations to make results
easier to verify.

Each ranked proposal includes a score and a short reason. Missing or unclear information is
flagged for human review instead of being treated as confirmed.

The system also ignores instructions found inside proposal documents that try to influence
the ranking.

 AI Tool Usage

I used ChatGPT/Claude to help organise my ideas, prepare an initial draft and review the
proposed design. I corrected the approach to Proposal C because instructions inside a
proposal should be treated as document content, not as commands to the AI. I also chose
rule-based checks for mandatory requirements and score calculations because they are easier
to verify.

 Final Decision

The tool supports the review process, but the final contractor selection is always made by
a human reviewer.
