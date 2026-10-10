# Home Credit AI Voice Agent

## Approach Document

### 1. Project Overview

This project involves designing an AI voice agent for Home Credit to conduct preliminary customer screening for a pre-approved Loan Against Property (LAP) offer. The agent collects eligibility information through a natural voice conversation, identifies disqualifying conditions, and routes appropriate customers to the relevant specialist.

The agent performs preliminary screening only. Final eligibility, interest rates, fees, and loan approval are handled by the authorized loan team.

### 2. Objectives

* Verify the customer's identity before disclosing offer details.
* Collect and validate the required eligibility information.
* Remember answers even when customers provide them out of order.
* Handle interruptions, corrections, questions, and unrelated diversions.
* Identify ineligible customers and end the fresh-loan flow politely.
* Route existing property-loan, balance-transfer, or EMI-reduction requests to a specialist.
* Transfer eligible customers to a senior loan expert for further assistance.

### 3. Tools Used

* Retell AI: Voice agent creation and call testing.
* GitHub: Project documentation and version control.
* CSV: Recording test scenarios and observed outcomes.

### 4. Conversation Flow

**Step 1: Customer Verification**
The agent verifies the customer according to the approved conversation flow before revealing loan-offer details.

**Step 2: Availability Check**
If the customer is busy, the agent asks for a suitable callback time, confirms it, thanks the customer, and ends the call without continuing the pitch.

**Step 3: Offer Introduction**
Once verification is complete and the customer is available, the agent briefly explains the pre-approved Loan Against Property offer without inventing loan terms.

**Step 4: Transfer-Request Detection**
If the customer mentions an existing property loan, EMI reduction, or loan transfer, the agent routes the request to a loan-transfer specialist and stops the fresh-loan screening flow.

**Step 5: Eligibility Screening**
The agent collects the required information, validates each answer, updates its conversation state, and asks the earliest unanswered question.

**Step 6: Final Routing**

* If a disqualifying condition is found, the agent explains the relevant reason politely and ends the fresh-loan flow.
* If all required answers are eligible, the agent hands the customer over to a senior loan expert.
* If the customer declines the maximum available loan amount, the agent politely ends the conversation.

### 5. Eligibility Checklist

1. **Property type:** Residential, commercial, and industrial properties are eligible. Agricultural property is disqualifying.
2. **Ownership:** Sole and joint ownership are accepted.
3. **Property documents:** Original property documents must be available. Photocopies only, or no documents, are disqualifying.
4. **Loan amount:** The maximum amount offered by this flow is ₹75 lakh. If a customer requests more, the agent explains the limit and asks whether the customer wants to continue with ₹75 lakh.
5. **Occupation:** Salaried and self-employed customers are accepted.
6. **Income mode:** Bank-received income is accepted. Cash-only income is disqualifying.
7. **Property market value:** Record the stated value for the loan expert. No minimum property value is specified in this screening flow.
8. **Requested tenure:** The acceptable tenure is 3 to 15 years, inclusive. A requested tenure below 3 years or above 15 years is disqualifying.

The loan amount is a customer preference and a maximum limit, rather than a separate eligibility checklist answer. All required screening information must be collected before the final handoff.

### 6. Conversation State Management

The agent follows an **Extract → Validate → Update State → Ask Earliest Missing Question** approach.

* Extract relevant information from the customer's latest response.
* Validate each answer against the eligibility rules.
* Save valid answers and retain previously collected information.
* Apply the customer's latest correction when an answer changes.
* Ask only for the earliest required unanswered item.
* Stop screening immediately when a disqualifying condition or transfer request is detected.

This approach reduces repetitive questions and supports natural conversations where customers answer several questions together.

### 7. Handling Exceptions

* **Customer is busy:** Confirm a callback time and end the call.
* **Customer provides multiple answers:** Extract and record all recognizable answers.
* **Customer changes an answer:** Update the saved value and re-evaluate eligibility.
* **Customer asks about rates or fees:** Do not invent figures; explain that the loan expert can provide confirmed details.
* **Customer requests a larger loan:** Explain the ₹75 lakh maximum and ask whether they want to proceed at that amount.
* **Customer requests a loan transfer or EMI reduction:** Route to the appropriate specialist.
* **Customer gives an irrelevant response:** Respond briefly and return to the earliest unanswered question when appropriate.

### 8. Testing Strategy

The agent is evaluated using scenarios covering:

* A fully eligible customer.
* Agricultural property.
* Unacceptable income mode.
* Missing original property documents.
* Tenure below and above the permitted range.
* A loan request above ₹75 lakh.
* Joint property ownership.
* Existing property loan and transfer requests.
* Out-of-order answers and corrections.
* Callback requests.
* Contradictory information.
* Questions about rates and fees.
* Multiple eligibility answers in one response.

Actual outcomes are recorded in `test_results.csv`. Only tests that have been executed and whose observed behavior meets the expected result should be marked PASS.

### 9. Evidence and Deliverables

The repository is intended to contain:

* The final system prompt used in Retell AI.
* This approach document.
* The test-results CSV.
* Selected screenshots, transcripts, and other genuine test evidence.
* A shareable Retell call or log link, where available and accessible to the reviewer.

### 10. Limitations and Responsible Handling

This prototype performs preliminary screening and does not guarantee loan approval. It must not invent financial terms, make unsupported approval promises, or disclose sensitive offer details before the required verification. Real customer information and credentials must not be published in the public repository.

### 11. Conclusion

The proposed agent combines structured eligibility validation with flexible conversational handling. Its state-management approach is designed to reduce repeated questions, detect disqualifying conditions early, and route customers to the appropriate human expert. The final quality assessment depends on the actual test results and evidence collected during execution.
