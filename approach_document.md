# Home Credit AI Voice Agent

**Prompt Engineering Internship Assignment**

## Project Overview

This project implements an AI voice agent using Retell AI for preliminary screening of customers interested in a pre-approved Loan Against Property (LAP) offer from Home Credit.

The agent collects eligibility information, validates customer responses, handles interruptions and corrections, identifies disqualifying conditions, and routes customers to the appropriate human specialist.

## Objectives

* Conduct customer verification before discussing offer details.
* Collect and validate the required eligibility information.
* Handle out-of-order answers and customer corrections.
* Identify disqualifying conditions and end the fresh-loan screening flow appropriately.
* Route existing property-loan, EMI-reduction, and loan-transfer requests to a specialist.
* Hand off eligible customers to a senior loan expert.

## Technology Used

* Retell AI — Voice agent creation and testing.
* GitHub — Project documentation and version control.

## Repository Contents

* `system_prompt.txt` — Final system prompt for the voice agent.
* `approach_document.md` — Agent design and conversation logic.
* `test_results.csv` — Test scenarios and actual outcomes.
* `evidence/` — Selected screenshots and transcripts from actual test calls, when available.

## Eligibility Rules

* Eligible property types: residential, commercial, and industrial.
* Ownership: sole or joint.
* Original property documents must be available.
* Maximum loan amount in this screening flow: ₹75 lakh, subject to customer acceptance if a higher amount was requested.
* Eligible occupations: salaried and self-employed.
* Income must be received through a bank; cash-only income is disqualifying.
* Property market value is recorded for further assessment.
* Acceptable tenure: 3–15 years, inclusive.

## Demo and Submission Evidence

* Retell demo/call recording: [Add your actual shareable Retell link]
* Call logs/transcript: [Add your actual shareable link, if available]

## Testing

The agent is evaluated against eligible and ineligible applicants, loan-transfer requests, callback requests, corrections, and out-of-order answers.

Actual test outcomes are documented in `test_results.csv`. Only executed tests are marked as passed or failed.

## Limitations

This agent performs preliminary screening only. It does not guarantee loan approval or provide unverified interest rates, fees, or loan terms. Final decisions and confirmed terms must come from the authorized loan team.

## Author

S. Asmitha Reddy
