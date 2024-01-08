### UC02: Keywords
***Ask an LLM to extract keywords from a block of text.***

User: 
```
You are a healthcare expert. Please extract top 5 most significant keywords from the following:

This modification ADDS benefits for one hair prosthesis (wig) per member, per the lifetime of the contract with the following criteria:

The benefits are limited to members with one of the following medical conditions or treatment thereof:

- Alopecia
- Hair loss caused by chemotherapy and/or radiation treatment for malignant and non-malignant conditions

Additional benefit criteria include:

- The hair prosthesis must be obtained from eligible durable medical equipment (DME) or prosthetic and orthotic appliance (P & O) providers
- Payer will pay no more than the approved amount for a hair prosthesis, minus the applicable deductible and coinsurance requirements
- Claims must be submitted, by the member, with an itemized receipt and letter of medical necessity from a physician. The letter of medical necessity must contain the patient's diagnosis and/or a description of the defined medical condition or treatment of the medical condition that resulted in hair loss
```
>**LLM [QS-LLM Aligned]**:  1. Modification 2. ADDS benefits 3. Hair prosthesis (wig) 4. Lifetime contract 5. Medical conditions

User:
```
Can you extract keywords? Please organize in a hierarchical fashion such that it maintains context?
```
>**LLM [QS-LLM Aligned]:**
>
>Certainly! Here's a hierarchical organization of keywords based on the provided information:
>
>Modification Benefits:
>
>- Adds benefits for one hair prosthesis (wig) per member
>- Lifetime coverage during the contract period
>
>Eligibility Criteria:
>
>- Limited to members with the following medical conditions or treatments:
>    - Alopecia
    >- Hair loss due to chemotherapy and/or radiation treatment for malignant and non-malignant conditions
>
>Additional Benefit Criteria:
>
>- Hair prosthesis must be obtained from eligible providers:
>    - Durable Medical Equipment (DME)
>    - Prosthetic and Orthotic Appliance (P & O)
>- Payer payment conditions:
>    - Pays no more than the approved amount
>    - Minus applicable deductible and coinsurance requirements
>
>Claims Submission:
>
>- Claims must be submitted by the member
>- Submission requirements:
>    - Itemized receipt
>    - Letter of medical necessity from a physician
>
>Letter of Medical Necessity:
>
>- Must contain:
>    - Patient's diagnosis
    >- Description of the defined medical condition or treatment resulting in hair loss

**Exercises**:

- Remove the restriction of 5 keywords
- Give hints on what kind of keywords to expect
- Ask for a hierarchy of keywords