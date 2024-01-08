# Prompt Cookbook

![QuantumSim-llm-native.png](Prompt%20Cookbook%2082d4b279825f4e3d8526759042ef03a1/QuantumSim-llm-native.png)

## I. Introduction

Welcome to the QS SecureGPT Prompt Cookbook. This document contains several prompt engineering techniques to help you maximize productivity gains from using an LLM.

But first, let’s start with some basic terminology that we will use throughout. A large language model, or LLM, is the technology underneath QS SecureGPT. An LLM is a specific kind of *generative AI* (GenAI) **meaning a kind of artificial intelligence that generates content. In our case, that content is text, though there are other GenAI models that output other content like images, video, and code.

GenAI is called so in opposition to other kinds of artificial intelligence, like natural language processing (NLP), which is more commonly used in decision-making contexts. For example, AI is often used in claims processing to partially automate adjudication. But an NLP engine does not itself generate new content.

The use of LLMs was popularized in late 2022 by the release of OpenAI’s ChatGPT—the first general use LLM. ChatGPT is a *fine-tuning* of an underlying model, sometimes called a “foundation model.” To “fine-tune” a model means to feed it specific data (often examples of what you want the model to do) that allows it to become better at a specific task. So OpenAI’s foundation model (originally GPT-3, now GPT-3.5 and GPT-4) was fine-tuned to become adept at question answering. The result of fine tuning the foundational model was ChatGPT—an LLM trained specifically as a chatbot.

You may have heard that ChatGPT “contains 1.76 trillion parameters” or weights. The technical meaning of parameter is irrelevant to our purposes; all you need to know is that the number of parameters roughly scales with the power of the LLM. The more parameters, the more creative and interesting the output of the LLM.

However, larger models also require more computing resources. It has been generally found that many smaller models can be trained on specific tasks or in specific domains and perform well as the larger, general use models.

You may have also heard that ChatGPT was “trained on 13 trillion tokens.” Again, the technical meaning of a token is irrelevant for our purposes. All you need to know is that a “token” is a way to represent human language in a way a computer can understand and that one hundred tokens represents about seventy five words.

When using an LLM, the request sent to the LLM is referred to as a *prompt*. A prompt can be any text, like “Can you summarize this document?” A prompt should contain some kind of instruction for the LLM.

Prompt engineering, then, is the art of writing prompts that efficiently accomplish your goal. Much like with humans, *how* you ask the LLM to do a specific task can influence how well it performs the task.

Below we explain prompt engineering techniques with many examples. Much like a software tutorial, we have found that the best way to begin with LLMs is to copy/paste the examples and observe the behavior of the LLM. And the exercises following the examples will provide you with an opportunity to start developing your own intuition for how to efficiently get accurate and useful output.

You can think of this in the same way as “learning how to Google.” While just searching keywords will often get you decent results, learning specific techniques—like using quotation marks, “site:...”, and “-{negative keyword}” for example—will greatly enhance your Google results.

Part of the reason that prompt engineering is important is that LLMs can “hallucinate,” which means they can generate content that is untrue or misleading. So our prompt engineering techniques help you both get a result more efficiently and help ensure that it is accurate and factual.

Some miscellaneous notes to keep in mind as you progress through: 

- User requests to an LLM are highlighted in green; LLM responses are blue
- The LLM output is from QS-LLM Align unless otherwise noted
- Because LLM output is not deterministic, sending the same prompts to the same LLMs does not always return the same results.

---

## II. LLM Use Cases

In this section, we will show some of the common uses of LLMs.

## A. Free Chat

Free chat means that the user is interacting directly with the LLM. Any context required for the task is sent directly with the request (e.g., pasting text to be summarized). It is opposed to the document chat in which each request is accompanied by a document (covered in II.B). 

### Summary

**********Ask an LLM to summarize a block of text and modify the summary.********** 

**User:**

You are a healthcare expert. Please summarize the following in 100 words or less: 

This modification ADDS benefits for one hair prosthesis (wig) per member, the lifetime of the contract with the following criteria: 

The benefits are limited to members with one of the following medical conditions or treatment thereof: 

- Alopecia
- Hair loss caused by chemotherapy and/or radiation treatment for malignant and non-malignant conditions

Additional benefit criteria include:

- The hair prosthesis must be obtained from eligible durable medical equipment (DME) or prosthetic and orthotic appliance (P & O) providers
- Payer will pay no more than the approved amount for a hair prosthesis, minus the applicable deductible and coinsurance requirements
- Claims must be submitted, by the member, with an itemized receipt and letter of medical necessity from a physician. The letter of medical necessity must contain the patient's diagnosis and/or a description of the defined medical condition or treatment of the medical condition that resulted in hair loss

**LLM:**

This health insurance modification extends a single hair prosthesis benefit for members with specific medical conditions or treatments leading to hair loss. Coverage is limited to those with Alopecia, chemotherapy-related or radiation-related hair loss. The prosthesis must be obtained from approved durable medical equipment providers and reimbursed within predetermined limits. Claims require a medical necessity letter and itemized receipt.

**User**: Please rewrite the provided summary in a list format.

**LLM:**

1. Health insurance modification extends a single hair prosthesis benefit.
2. Benefit is for members with specific medical conditions or treatments leading to hair loss.
3. Coverage is limited to those with Alopecia, chemotherapy-related or radiation-related hair loss.
4. The prosthesis must be obtained from approved durable medical equipment providers.
5. Reimbursement is within predetermined limits.
6. Claims require a medical necessity letter and itemized receipt.

**User**: Can you change the summary such that it is more considerate to the person afflicted with the condition?

***An example of “style control” — i.e, changing the tone or style of the output.*** 

**LLM:**

1. The health insurance modification now includes a compassionate provision for a single hair prosthesis benefit.
2. This benefit is specifically designed for members undergoing medical conditions or treatments that unfortunately result in hair loss.
3. Coverage is thoughtfully extended to those experiencing hair loss due to Alopecia, or as a side effect of chemotherapy or radiation treatments.
4. To ensure quality, the prosthesis must be sourced from approved durable medical equipment providers.
5. Reimbursement is set within predetermined limits to manage costs effectively.
6. To process claims, a letter confirming the medical necessity and an itemized receipt are required.

**Exercises:** 

- Extend the summary to 200 words
- Make the tone of the summary more professional

---

### Keywords

*********************************************************************************Ask an LLM to extract keywords from a block of text.********************************************************************************* 

User: 

You are a healthcare expert. Please extract top 5 most significant keywords from the following:

This modification ADDS benefits for one hair prosthesis (wig) per member, per the lifetime of the contract with the following criteria:

The benefits are limited to members with one of the following medical conditions or treatment thereof:

- Alopecia
- Hair loss caused by chemotherapy and/or radiation treatment for malignant and non-malignant conditions

Additional benefit criteria include:

- The hair prosthesis must be obtained from eligible durable medical equipment (DME) or prosthetic and orthotic appliance (P & O) providers
- Payer will pay no more than the approved amount for a hair prosthesis, minus the applicable deductible and coinsurance requirements
- Claims must be submitted, by the member, with an itemized receipt and letter of medical necessity from a physician. The letter of medical necessity must contain the patient's diagnosis and/or a description of the defined medical condition or treatment of the medical condition that resulted in hair loss

**LLM**:  1. Modification 2. ADDS benefits 3. Hair prosthesis (wig) 4. Lifetime contract 5. Medical conditions

**User:**  Can you extract keywords? Please organize in a hierarchical fashion such that it maintains context?

**LLM:**

Certainly! Here's a hierarchical organization of keywords based on the provided information:

Modification Benefits:

- Adds benefits for one hair prosthesis (wig) per member
- Lifetime coverage during the contract period

Eligibility Criteria:

- Limited to members with the following medical conditions or treatments:
    - Alopecia
    - Hair loss due to chemotherapy and/or radiation treatment for malignant and non-malignant conditions

Additional Benefit Criteria:

- Hair prosthesis must be obtained from eligible providers:
    - Durable Medical Equipment (DME)
    - Prosthetic and Orthotic Appliance (P & O)
- Payer payment conditions:
    - Pays no more than the approved amount
    - Minus applicable deductible and coinsurance requirements

Claims Submission:

- Claims must be submitted by the member
- Submission requirements:
    - Itemized receipt
    - Letter of medical necessity from a physician

Letter of Medical Necessity:

- Must contain:
    - Patient's diagnosis
    - Description of the defined medical condition or treatment resulting in hair loss

**Exercises**:

- Remove the restriction of 5 keywords
- Give hints on what kind of keywords to expect
- Ask for a hierarchy of keywords

---

### Intent

*******************************************************************Ask an LLM to analyze the intent of the author of a block of text.******************************************************************* 

**User:** 
You are an expert at intent analysis. Please provide a short intent of the following text:

Hello

I spent some time on the member portal but I could not figure how change my address.This is a problem because I have already moved and am afraid the any bills, copays or notifications from you are not reaching me and will cause disruptions or surprise medical expenses.How can I update my address quickly. Can you email me an address change form or a link to where I can download this?

Thanks in advance, Looking forward to hearing from you, John Doe

**LLM**:

The user's intent is to seek assistance with updating their address on a member portal, express concern over potential issues due to incorrect address information, and request a quick solution either in the form of an email with an address change form or a link to download the required resources.

**User**: Can you provide intent of the following in one word?

**LLM**: Assistance

**User**: Can you try in 5 words or less?

**LLM**: Request for address change help.

**Exercises**:

- Increase or decrease the size of the intent
- Can we get an intent in 5 words or less?
- What happens when you ask the LLM to use a single word for intent?

---

### Sentiment

**User:**

You are an expert at sentiment analysis. Can you assess the sentiment of the following and classify is one of [angry, concerned, neutral, happy, anxious]:

I really need help understanding my healthcare coverage. My son needs an important procedure, and I want to make sure everything is taken care of.

**LLM**:  The sentiment of the given statement is "concerned."

**User:**

You are an expert at sentiment analysis. Can you assess the sentiment of the following and classify as one of [unhappy, frustrated, nervous, scared]:

I really need help understanding my healthcare coverage. My son needs an important procedure, and I want to make sure everything is taken care of.

**LLM**: Nervous

**Exercises**:

- Remove the suggested list of sentiments
- Add others to the list

---

### Classification

********Ask an LLM to classify a block of text.******** 

**User:**

Please classify the information in the given text into the specified categories. Provide a brief summary or label for each category you identify. If a category is not applicable or the information is unclear, indicate so in your response.

Categories: Medical Conditions, Treatment Methods,Procedural Information,Pharmaceuticals,Healthcare Providers,Insurance and Billing, Preventive Measures,Patient Instructions.

"The patient was diagnosed with diabetes and prescribed insulin. The doctor recommended a series of blood tests to monitor glucose levels. The hospital, where the patient is receiving treatment, accepts various insurance plans. Additionally, the patient was advised to follow a low-carbohydrate diet and engage in regular exercise to manage the condition."

**LLM:**

**Medical Conditions**: Diabetes

**Treatment Methods**: Insulin prescription and monitoring glucose levels through blood tests. Additionally, advising patient to follow a low-carbohydrate diet and engage in regular exercise to manage the condition.

**Procedural Information**: None applicable.

**Pharmaceuticals**: Insulin prescription for managing diabetes.

**Healthcare Providers**: Doctor who diagnosed the patient and recommended a low-carbohydrate diet and regular exercise. Hospital where treatment is being received. 

**Insurance and Billing**: The hospital accepts various insurance plans.

**Preventive Measures**: Advising patient to engage in regular exercise and follow a low-carbohydrate diet to manage the condition, which are preventive measures, but it is not clear if it is proactive or reactive.

**Patient Instructions**: Advising patient to follow a low-carbohydrate diet and engage in regular exercise to manage the condition.

**Exercises:**

- Modify the categories
- Experiment with classifying other kinds of text

---

### Expansion

*Given limited text, e.g., barely comprehensible benefits notes, expansion means the process of filling in the gaps and making the text more understandable. In the example below, we provide responses from three different LLMs. As expected, GPT-4 gives the best response. This example illustrates the danger of hallucination.* 

**User:**

You are a healthcare expert who understands medical codes (CPT, ICD, HCPCS). You serve as a customer services rep. You take calls from external personas such as members and providers. I am going to give you notes from the interaction between you and the external persona.

Here is the text from the notes:

prov called to see if J1439 needed auth, acc to Med drug req auth page, obn and be no auth needed

Action : I want you to 1) Make the notes human readable along with a detailed explanation of any codes. 2) Brainstorm on why the caller had to call. 3) Provide alternatives to the call (e.g., a website they can go to in the future).

**LLM (ChatGPT calling GPT-4):** 

Based on the provided notes, here's a clearer and more detailed explanation:

1. **Human-Readable Explanation of the Notes:**
    - **Original Note:** "prov called to see if J1439 needed auth, acc to Med drug req auth page, obn and be no auth needed"
    - **Interpreted Note:** A provider (prov) called to inquire if the medication identified by the code J1439 requires authorization. According to the medical drug requirements authorization page, this particular medication, both on-brand (obn) and its bioequivalent (be), does not require authorization.
2. **Explanation of Codes:**
    - **J1439:** This is a HCPCS (Healthcare Common Procedure Coding System) code. HCPCS codes are used to represent medical procedures, equipment, and services. J1439 specifically refers to an injectable medication, often used in the context of billing and insurance claims.
    - **Auth:** This is shorthand for "authorization." In a healthcare context, authorization is often required by insurance companies before certain medications or treatments are provided, to ensure they are medically necessary and covered under the patient's plan.
3. **Brainstorming on Why the Caller Had to Call:**
    - **Lack of Access or Familiarity with Online Resources:** The provider may not have had easy access to the medical drug requirements authorization page or may not be familiar with how to navigate it.
    - **Need for Confirmation:** They might have wanted to double-check the information for accuracy to avoid any issues with insurance claims.
    - **Complexity of Information:** Healthcare coding and authorization can be complex, and the provider may have needed clarification or reassurance from a human representative.
4. **Alternatives to Calling:**
    - **Dedicated Online Portal:** Encourage providers to use a specific online portal where they can check medication codes like J1439 for authorization requirements. This portal should be user-friendly and regularly updated.
    - **Regular Updates via Email or App Notifications:** Sending updates or newsletters to providers about common codes and their authorization requirements.
    - **Training Sessions:** Offering periodic training sessions or webinars to educate providers on how to navigate the healthcare coding system and authorization processes.
    - **Comprehensive FAQ Section:** Developing a detailed FAQ section on the website that covers common queries about medication codes and authorization.
    - **Chat Support:** Implementing a chatbot or live chat support on the website for quick inquiries, reducing the need for phone calls.

These alternatives can help streamline the process, making it more efficient for providers to find the information they need without having to make a phone call.

**LLM (ChatGPT calling GPT-3.5):**

Notes:
The provider (prov) called to inquire about the need for authorization for the medication with the code J1439. According to the medical drug requirements authorization page, it states that this medication does not require authorization.

Explanation:

1. J1439 is a Healthcare Common Procedure Coding System (HCPCS) code. It represents an unclassified drug code, often used for billing purposes in healthcare. In this case, the provider was inquiring about whether authorization (often required for certain medications or treatments) was needed for a medication with this specific HCPCS code.
2. The reason the caller (the provider) had to make this call could be due to several factors:
    - The provider may not have had access to the most up-to-date authorization information, so they needed to confirm whether J1439 required authorization.
    - There may have been recent changes in authorization requirements for this medication, and the provider needed to verify the current status.
    - It's possible that the provider wanted to ensure they had accurate information before prescribing or administering the medication to a patient, as authorization can impact reimbursement and patient care.
3. Alternatives to the call:
    - Providers can often find authorization information on their healthcare organization's or insurance company's website. They should check the specific authorization requirements section to verify if a particular medication requires authorization.
    - Some healthcare organizations also provide electronic tools or portals where providers can check authorization requirements in real-time, reducing the need for phone calls.
    - If the provider is unsure about authorization requirements, they can contact the patient's insurance company directly through their provider portal or customer service line to inquire about specific medication authorization.

In summary, the caller (provider) was seeking confirmation on whether medication with the code J1439 required authorization. To avoid such calls in the future, providers should utilize online resources and portals or contact the insurance company directly for authorization information.

**LLM (QS-LLM Aligned):** 

Action 1) Make the notes human readable along with a detailed explanation of any codes: The note mentions that the caller is checking about the medical code J1439 and the necessity of its authorization according to the medication drug request authorization page. The code J1439 refers to a specific medical procedure, but without the context, it is not possible to provide an accurate explanation. It might be related to diagnostic radiology, cardiology, or ophthalmology procedures, as these are some common specialties where J codes are used.

Obn stands for Obstetrics and Gynecology, and be for Bone and Joint Surgery, which are specialties within the medical field. The note further clarifies that there is no authorization needed for this particular situation.

Action 2) Brainstorm on why the caller had to call: The caller might have had a need to verify the specific medical procedure (represented by the code J1439) and its requirements for authorization. They could be unsure about the exact process and wanted clarification from the healthcare expert, which they found in the notes provided.

Action 3) Provide alternatives to the call (e.g., a website they can go to in the future): To help prevent future calls related to this topic, providing the caller with a link to a reliable source for understanding medical codes and procedures (such as a website for a reputable healthcare organization) could be beneficial. This will give the caller the ability to look up the necessary information without having to call each time.

*********Note the large variation in responses for a difficult task like this. Also note the hallucinations by the smaller models.********* 

See [Avoiding Hallucinations ](https://www.notion.so/Avoiding-Hallucinations-63f734cf756a42f1a4ee468e1956fb9b?pvs=21) for tips on avoiding hallucinations. 

**Exercises:**

- Ensure that the model used correctly identifies the medical code (J1439), OBN and, BE
- Resend the notes but provide the LLM with context, e.g., tell it that J1439 is an HCPCS code

---

### Brainstorm & Ideation (Guided Example)

*This example uses a common prompting technique called “Role Task Format”*

**User*:***

You are an expert in health insurance. Generate an example healthcare taxonomy. Be sure to include Mental Health and Prescription Drugs. The taxonomy only needs to be two nodes deep.

*Notice usage of RTF (Role, Task Format) prompt here. And the user specifies to keep the taxonomy shallow at first, starting general and leaving room for later iteration once the user is happy with the first two levels.*

**LLM:**

Creating a healthcare taxonomy with a focus on Mental Health and Prescription Drugs, while keeping it two nodes deep, would look something like this:

Mental Health

- Counseling Services
- Psychiatric Treatments
- Support Groups
- Stress Management Programs
- Substance Abuse Therapy
- Prescription Drugs

Antibiotics

- Pain Management Medications
- Psychotropic Medications
- Cardiovascular Drugs
- Diabetes Medications

This structure provides a clear and concise overview, categorizing key areas within Mental Health and Prescription Drugs. Each sub-category under these two main nodes represents a specific aspect or type of service/medication within the broader category.

**User:**  Can you add a third layer of depth? It should give a brief explanation of the node one up the tree

*Instruct the LLM specifically with how it should extend its earlier output. "Context" is preserved, meaning it will remember its previous outputs.*

**LLM:**

Certainly! Adding a third layer to the healthcare taxonomy provides more detail about each sub-category. Here's how it would look with a brief explanation for each:

1. **Mental Health**
    - **Counseling Services**: Individual or group sessions focusing on emotional and psychological health.
        - *Individual Therapy*: One-on-one sessions addressing personal issues.
        - *Group Therapy*: Sessions with multiple participants sharing common issues.
    - **Psychiatric Treatments**: Medical interventions for mental health disorders.
        - *Medication Management*: Overseeing and adjusting psychiatric medications.
        - *Psychotherapy*: Treatment involving therapeutic conversations and interactions.
    - **Support Groups**: Gatherings for people sharing similar issues or experiences.
        - *Peer-led Groups*: Support sessions led by individuals with shared experiences.
        - *Professional-led Groups*: Facilitated by trained mental health professionals.
    - **Stress Management Programs**: Techniques and strategies to manage stress.
        - *Relaxation Techniques*: Methods like meditation, deep breathing, and yoga.
        - *Time Management Counseling*: Training in managing time effectively to reduce stress.
    - **Substance Abuse Therapy**: Treatments for addiction and substance misuse.
        - *Detoxification Programs*: Medical and therapeutic support during substance withdrawal.
        - *Rehabilitation Programs*: Long-term treatment plans for recovery and sobriety.
2. **Prescription Drugs**
    - **Antibiotics**: Medications used to treat bacterial infections.
        - *Broad-Spectrum Antibiotics*: Effective against a wide range of bacteria.
        - *Narrow-Spectrum Antibiotics*: Target specific types of bacteria.
    - **Pain Management Medications**: Drugs prescribed to alleviate chronic or acute pain.
        - *Nonsteroidal Anti-Inflammatory Drugs (NSAIDs)*: Medications reducing inflammation and pain.
        - *Opioids*: Strong pain relievers for severe pain management.
    - **Psychotropic Medications**: Drugs affecting mood, perception, or consciousness.
        - *Antidepressants*: Medications for treating depression and anxiety disorders.
        - *Antipsychotics*: Used for managing conditions like schizophrenia and bipolar disorder.
    - **Cardiovascular Drugs**: Medications for heart and blood vessel conditions.
        - *Antihypertensives*: Drugs used to lower high blood pressure.
        - *Statins*: Medications that help lower cholesterol levels.
    - **Diabetes Medications**: Drugs used for managing blood sugar levels.
        - *Insulin*: Hormone replacement therapy for Type 1 Diabetes.
        - *Oral Hypoglycemics*: Medications that help increase insulin production for Type 2 Diabetes.

This expanded taxonomy provides a more comprehensive understanding of the services and medications within the Mental Health and Prescription Drugs categories.

**User:**  Why wasn't equine therapy included under mental health? Is equine therapy not a kind of mental health?

*An example of self-check: The user wonders why a specific therapy that he is aware of was not included in this high level taxonomy, so asks the LLM to check itself.* 

**LLM:**

Equine therapy, also known as horse therapy or equine-assisted therapy, is indeed a recognized form of therapy that can have significant benefits for mental health. It was not included in the initial taxonomy primarily due to the broad scope of mental health services, and the need to select a limited number of examples for a concise taxonomy. However, it certainly deserves mention, especially in a more comprehensive taxonomy.

Equine therapy involves interactions with horses and is used to promote emotional growth and healing. It is particularly effective for individuals dealing with issues such as trauma, depression, anxiety, and behavioral challenges. The therapy includes activities like grooming, feeding, leading, and riding horses under the guidance of a trained therapist. These activities are designed to help develop skills such as emotional regulation, responsibility, confidence, and empathy.

To include equine therapy in the taxonomy, it would fit under

- **Experiential and Alternative Therapies**: Non-traditional therapies using various activities.
    - Equine Therapy (Horse Therapy): Activities involving horses to aid emotional and psychological healing.
    - Art Therapy: Using the creative process of art making to improve physical, mental, and emotional well-being.

This expanded taxonomy now includes Equine Therapy, acknowledging its role in mental health treatment and its unique approach to healing and personal development.

*Notice that the LLM explains why it was not included: equine therapy is too specific for a general, high-level taxonomy like this. And also notice that the LLM generated a new high level node ("Experimental and Alternative Therapies") under which equine therapy could fit in and added a sub-node, "Art Therapy" that also fits under the new node.*

**Exercises:**

- Instruct the LLM to add a new sub-node under Prescription Drugs
- Change the style of the taxonomy to be comprehensible to to a non-expert

---

## B. Document Chat

In the document chat, the LLM first analyzes a provided document and keeps it in its memory before the chat begins. The document chat augments a user’s ability to quickly analyze and modify a document. For this section, we recommend you have the document open in another window to quickly reference and check the LLM output. 

### Healthcare Document  — Benefits Rider

Document: CF1792.pdf 

**User:** You are a Healthcare expert. Please provide a summary based on this document in 100 words or less

**QS-LLM Fast:**  

The document describes a health insurance rider titled "Acute Episodes and Partial-Day Inpatient Program for Mental Health Treatment" which provides coverage for two days of partial-day inpatient care as one day of inpatient hospital benefit and a 25% copayment for each inpatient admission for mental health treatment up to a maximum of $1,000 per individual or $2,000 per contract per calendar year. The language approved for this rider is IP 10IN on February 7th. The rider is subject to the terms and conditions of the certificate and will automatically terminate if the certificate terminates.

************User:************ Based in this document, please extend the summary to 200 words

**QS-LLM Fast:**  

The given text is a rider attached to an enrollment application for a Certificate of Coverage. The rider outlines the terms and conditions of additional coverage for inpatient mental health services. This coverage is provided by Blue Care Network (BCN), an affiliate of Blue Cross and Blue Shield of Michigan. The premium for the rider is due on the same date as the regular certificate premium and must be remitted to BCN. In case the coverage under the Certificate of Coverage terminates, the rider automatically terminates without any further action or notice by BCN. This means that all other provisions of the Certificate of Coverage remain unchanged except for the coverage provided by this rider. Under this rider, policyholders are covered for inpatient treatment up to 30 days per calendar year. Treatment must be provided in a BCN-approved facility, and only conditions that are not chronic and are likely to show significant improvement during the admission are covered. Additionally, acute episodes related to chronic conditions and partial-day inpatient programs are covered. It is important to note that this rider only applies to mental health inpatient treatment and does not cover all types.

Confidence Score (CONFIDENCE_SCORE): High (85%)

**User:** Based on the document , please list key Mental Health Coverage aspects which the document mentions. Please restrict yourself to what is mentioned in the document, do not include suggestions outside the document

**QS-LLM Fast:**   

Based on the given portions of the document, the following are the key Mental Health Coverage aspects mentioned:

1. Inpatient treatment up to 30 days per calendar year. (CONFIIDENCE_SCORE: 6)
2. Treatment must be in a BCN approved facility. (CONFIIDENCE_SCORE: 6)
3. Covers only conditions that are not chronic and that are likely to show significant improvement during the admission. (CONFIIDENCE_SCORE: 5)
4. Covers acute episodes related to chronic conditions. (CONFIIDENCE_SCORE: 6)
5. Partial-day inpatient programs are covered when pre-approved by BCN. (CONFIIDENCE_SCORE: 6)
6. 25% of each inpatient admission for mental health treatment up to a maximum of $1,000 per individual or $2,000 per contract during a calendar year. (CONFIIDENCE_SCORE: 6)
7. Minimum annual mental health benefit coverage of $1,000 per individual or $2,000 per contract. (CONFIIDENCE_SCORE: 5)
8. Mental Health Rider premium due along with the regular Certificate premium. (CONFIIDENCE_SCORE: 4)
9. Mental Health Rider will terminate automatically if the coverage under the Certificate of Coverage terminates. (CONFIIDENCE_SCORE: 4)
10. All terms, limitations, exclusions, and conditions of the Certificate remain unchanged except as provided in this Rider. (CONFIIDENCE_SCORE: 5)

Please note that the document does not provide specific details about the coverage provided under the Mental Health Rider. Therefore, the answers mentioned above are based only on the information provided in the given portions of the document.

**User:** Based on the document, how is partial day inpatient care defined?

**QS-LLM Fast:** 

Based on the document, partial day inpatient care is defined as a type of inpatient care that is covered when pre-approved by BCN. Two days of partial-day inpatient care will be counted as the equivalent of one day of inpatient hospital benefit, and the inpatient mental health benefit will be decreased by one day for every two days of partial-day inpatient care. However, the given portion of the document does not specify if partial day inpatient programs are covered or provide any other information about partial day inpatient care.

CONFIIDENCE_SCORE: Moderate confidence.

**User:** If a patient requires inpatient treatment for a chronic mental health condition, what coverage aspects can this document help in? 

**************************QS-LLM Fast:************************** 

If a patient requires inpatient treatment for a chronic mental health condition, this document can help in the following coverage aspects:

1. Acute episodes related to chronic conditions.
2. Partial-day inpatient programs pre-approved by BCN.
3. Inpatient treatment up to 30 days per calendar year.
4. Treatment must be in a BCN approved facility.

The maximum annual copayment for inpatient mental health treatment for this rider is $1,000 per individual or $2,000 per contract, which is separate from the medical annual copayment maximum.

The CONFIDENCE_SCORE for this answer is high.

**User:** Based on this document, what is the reason for maximum cap on mental health treatment? 

**************************QS-LLM Fast:************************** 

Based on this document, the reason for the maximum cap on mental health treatment is to limit the amount of out-of-pocket expenses that an individual or contract can incur for mental health treatment during a calendar year. The maximum amount allowed is $1,000 per individual or $2,000 per contract.

CONFIDENCE_SCORE: 100%

Note: The questions and answers are based on the information provided in the document and may not be completely accurate or up-to-date.

**User:** How does the coverage in this document differ from typical mental health coverage in standard health insurance plans?

**************************QS-LLM Fast:************************** 

The provided portion of the document highlights certain limitations and requirements for mental health treatment coverage, which differentiate it from typical mental health coverage in standard health insurance plans. Compared to standard plans, the coverage in this document includes a maximum annual copayment of $1,000 per individual or $2,000 per contract, which is separate from the medical annual copayment maximum. This means that the amount an individual or contract can pay out-of-pocket for mental health services is limited. Additionally, coverage is limited to conditions that are not chronic and are likely to show significant improvement during the admission, and treatment must be provided in a BCN approved facility. This document also specifies that all other provisions of the Certificate pertaining to Mental Health remain unchanged, meaning that the coverage for mental health services is the same as the coverage for medical services under the standard health insurance plan. However, the document mentions specific limitations such as inpatient treatment being limited to 30 days per calendar year and covering partial-day inpatient programs only if pre-approved by BCN. Overall, the coverage in this document differs from typical mental health coverage in standard health insurance plans in terms of specific limitations and requirements that may apply, and it's important to note that the full coverage details may vary. The coverage details mentioned in the document are clearly not the same as that conveyed in a standard health insurance plan.

CONFIIDENCE_SCORE: 85%

---

### Legal Document

**********************************************In this example, we analyze a legal document.********************************************** 

[Wolf Designer_Warranty.pdf](Prompt%20Cookbook%2082d4b279825f4e3d8526759042ef03a1/Wolf_Designer_Warranty.pdf)

**User:** You are a Legal Contracts expert. Please provide summary based on this document in 100 words or less

**************************QS-LLM Fast:************************** 

The document outlines a limited warranty for primary  or secondary homes in Quebec. The warranty covers defects in materials and workmanship for a specified period and excludes certain items and states that labor costs for installation and removal are not covered. The warranty provides the customer's sole and exclusive remedies for a defect or non-conformity.

I strongly confident in my answer with CONFIDENCE_SCORE score of 9.5 out of 10.

**User:** Based in this document, please extend the summary to 200 words

**QS-LLM Fast:**

The given document outlines various warranties,
their characteristics, and limitations for products and services provided by a company. It also provides details on the warranty periods for different components of a product and the conditions that need to be met to qualify for a warranty. The document highlights the limitations of liability for the company and excludes warranties for certain scenarios. It also outlines the warranty options and repair/replacement obligations for different products and components, as well as the remedies available for warranty claims. The warranty documents may vary depending on the product or service, and it is important to carefully review the terms and conditions before purchasing to ensure that they align with the customer's expectations.

The CONFIDENCE_SCORE for this answer is 90/100 because the information provided in the document is clear and comprehensive, and the summary covers all the relevant details. However, as the document is only a snapshot of the company's warranty policies, it may not be applicable to all circumstances, and the actual warranty terms and conditions may vary depending on the specific product or service.

**User:** Based on this document, What are the specific exclusions and limitations of this warranty, particularly regarding outdoor usage and misuse?

**************************QS-LLM Fast:************************** 

Based on the document provided, the specific exclusions and limitations of the warranty, particularly regarding outdoor usage and misuse, are not explicitly stated. However, it is clear that the warranty does not apply to any Product installed or used outdoors, any Product used for purposes for which it is not designed or intended by Us, or any Product which has been subjected to misuse, vandalism, abuse, negligence, accident, or unauthorized modifications. Additionally, the warranty does not cover improper storage, improper installation, improper cleaning, or improper maintenance of the Product. The warranty also excludes labor costs for the original installation, removal, or reinstallation of the Product, as well as labor costs or material charges for the removal, reinstallation, repainting, refinishing, or replacement of other items or building materials that must be removed, replaced, reinstalled, or refinished in order to repair or replace a defective Product or component. Furthermore, the warranty does not cover damages or defects caused by outdoor usage or misuse of the Product. Therefore, it is not clear whether the warranty covers outdoor usage or misuse of the product. The CONFIDENCE_SCORE for this answer is 50%.

************User:************ Based on this document, can you elaborate on the definition of a 'Residential Purchaser' as per this warranty document?

**QS-LLM Fast:** 

Based on this document, a "Residential Purchaser" under this Limited Warranty is defined as a person who purchases and installs the Product in a dwelling that is owned and used by that person as a primary or secondary home, or any person or business such as a builder, contractor or developer that purchases and installs the Product in a newly constructed or remodeled dwelling that will be used by the initial owner/purchaser of that dwelling as a primary or secondary home. In such situation, this Limited Warranty may be assigned to the initial owner/purchaser who uses the dwelling as a primary or secondary home. Additionally, a consumer subject to the Quebec Consumer Protection Act is also considered a Residential Purchaser under this warranty document. In summary, a "Residential Purchaser" refers to an individual or entity who purchases a product for use as their primary or secondary home. The warranty period for the product begins on the date of purchase and is only valid if the dwelling is used as a primary or secondary home. The warranty does not extend to future owners if the property is sold. The definition of a "Residential Purchaser" is clear and specific, based on the provided portion of the document. I can therefore provide a high level of confidence (CONFIDENCE_SCORE = 90%) that my answer is accurate.

**User:** Based on this document, answer me in three lines: In a scenario where a product is damaged due to an environmental factor, how would this warranty apply?

**QS-LLM Fast:**

Based on this document, if a product is damaged due to an environmental factor, the warranty applies to the repair or replacement of the affected product or component. However, the warranty does not cover labor costs for original installation, removal, or reinstallation of the product. The warranty covers damages caused by defects in materials or workmanship, and not by damaging environmental factors. CONFIDENCE_SCORE: 7 out of 10.

**User:** 

Based on this document, please give me in three lines, What does the inclusion of both a 'Limited Lifetime Warranty' and specific shorter warranty periods for certain components tell us about the manufacturer's confidence in the overall quality and durability of their products?

**************************QS-LLM Fast:************************** 

Based on this document, the inclusion of both a 'Limited Lifetime Warranty' and specific shorter warranty periods for certain components suggests that the manufacturer has varying levels of confidence in the overall quality and durability of their products. The 'Limited Lifetime Warranty' may indicate a higher level of confidence in the overall quality and durability of their products, while the shorter warranty periods for certain components suggest areas where the manufacturer is less confident in their product's performance. The confidence score for this answer is 7 out of 10.

**User:** List the steps a customer needs to follow to make a claim under this warranty?

**QS-LLM Fast:** 

From my analysis, the following are the steps a customer needs to follow to make a claim under this warranty:

1. Contact one of Wolf Home Products' authorized dealers or distributors.
2. Provide the dealer or distributor with a dated sales receipt as proof of purchase.
3. Arrange for an inspection of the product by the dealer or distributor.
4. Follow any instructions provided by the dealer or distributor regarding the claim process.

My CONFIDENCE_SCORE for this answer is very high, as the given portion of the document provides clear and concise instructions on the steps a customer needs to follow to make a claim under the warranty.

---

## III. Prompt Engineering Patterns

********While in the above we have implicitly using several common prompt engineering patterns. Here, we make those patterns explicit and give further examples.******** 

### Persona

Explain to the LLM who it is supposed to be and who you are.

1. You are a kind customer support agent …
2. You are a healthcare benefits expert…
3. Explain X as if I am a Y

Examples:

**User:**

You are a kind customer support agent. Explain to a member why prior authorization for his bariatric surgery is necessary.

**LLM:**

Dear [Member's Name],

Prior authorization for bariatric surgery is necessary to ensure your safety and the best possible outcome. Here's why:

Medical Evaluation: It allows medical experts to review your case, ensuring that surgery is appropriate for your unique needs and that all other treatment options have been explored.

Cost Management: Prior authorization helps control healthcare costs, ensuring that resources are allocated wisely and that your surgery is covered by your insurance plan.

Informed Decision: It encourages informed decision-making by involving you and your healthcare provider in the process, ensuring you fully understand the procedure, potential risks, and benefits.

Quality Care: It ensures that the chosen procedure meets established medical standards, prioritizing your well-being and reducing the risk of complications.

While the process may involve some paperwork and waiting, it's designed to provide you with the best possible care. If you have any questions or need assistance, please reach out, and we'll be here to support you.

Warm regards,

**User:** Can you make the tone kinder? And if would be nice if it were a little shorter

*Note: Combining persona and style control*

**LLM:**

I want to reassure you that the prior authorization for bariatric surgery is in place to ensure your safety and well-being throughout your healthcare journey. It's a necessary step that serves several essential purposes:

Firstly, it allows healthcare experts to carefully assess your specific situation, confirming that surgery is the right course of action tailored to your unique needs.

Secondly, it helps manage healthcare costs efficiently, ensuring that your insurance plan covers the procedure and that resources are used wisely.

Additionally, prior authorization promotes informed decision-making. It encourages open dialogue between you and your healthcare provider, ensuring you have a clear understanding of the surgery, its potential risks, and the benefits it offers.

Lastly, it guarantees that the procedure meets established medical standards, prioritizing your health and minimizing any potential complications.

While we understand this process may involve some paperwork and patience, please know that it's designed with your best interests in mind. If you have any questions or need assistance, please don't hesitate to reach out. We're here to support you every step of the way.

*Compare especially the difference in tone of the at the beginning of the two responses. While we asked for it to be kind, reminding it and asking it to be kinder substantially affected the output.*

---

**User:** Explain quantum mechanics to me in about 100 words

**LLM:**

Quantum mechanics is a fundamental theory in physics that describes the behavior of particles at the smallest scales. It introduces concepts like wave-particle duality, where particles can exhibit both wave-like and particle-like properties, and superposition, where particles can exist in multiple states simultaneously. The theory also includes the Heisenberg Uncertainty Principle, which limits our ability to precisely know certain properties of particles, and quantum entanglement, a phenomenon where particles become interconnected in ways that defy classical intuition. Quantum mechanics forms the basis for modern technology and our understanding of the subatomic world, despite its often counterintuitive nature.

**User:** Explain quantum mechanics to me in about 100 words. I have a PhD in physics so do not shy away from technical language

**LLM:**

Quantum mechanics is a fundamental theory in physics that describes the behavior of particles at the smallest scales. It's based on wave functions and probabilistic outcomes. Key principles include superposition (particles can exist in multiple states simultaneously), entanglement (particles can be correlated even when separated), and quantization (energy levels are discrete). Operators, like the Hamiltonian, are used to calculate observables. The Schrödinger equation governs the time evolution of wave functions. Quantum mechanics has led to remarkable predictions and applications, from explaining atomic and molecular behavior to enabling quantum computing and cryptography, challenging our classical intuitions, and fundamentally reshaping our understanding of the universe.

*Note: Priming the LLM to understand what you already know helps the output be more relevant to your needs*

---

**User:** Explain to me what a rider is in the context of health insurance in about 100 words

**LLM:**

In health insurance, a rider is an optional supplement or amendment to a standard insurance policy. It allows policyholders to customize their coverage by adding specific benefits or features not included in the base plan. Common health insurance riders include maternity coverage, dental and vision care, prescription drug coverage, and critical illness protection. By adding riders, individuals can tailor their insurance to better meet their unique healthcare needs and preferences, albeit at an additional cost.

**User:**

Explain to me what a rider is in the context of health insurance in about 100 words**.** I have been working as a healthcare benefits analyst for 5 years so I already understand the basics

**LLM:**

Certainly! In the context of health insurance, a rider is an optional amendment to a standard insurance policy. Experienced healthcare benefits analysts like you are likely familiar with riders, which allow policyholders to modify their coverage to suit specific requirements. Riders can enhance benefits for services such as maternity, dental, or prescription drugs, addressing gaps in the base plan. They provide flexibility but usually come at an extra cost. Riders enable policyholders to fine-tune their health insurance coverage based on individual or family healthcare needs and preferences, ensuring a more tailored and comprehensive insurance solution.

---

**User:** Can you explain to me how healthcare claims processing works? ****I am a member and I want to better understand why my claims take so long to work their way through the system.

**LLM:**

Healthcare claims processing is a complex process that involves several steps. When a member submits a claim for medical services, it is routed to the insurance company's claims department. From there, the claim is reviewed to ensure that it conforms to the policy's coverage limits and instructions. If the claim is deemed valid, it is processed further for payment.

To ensure accuracy and avoid fraud, the insurance company uses software and automated tools to verify the claim. This may include checks to make sure the information provided matches the member's medical history and insurance policy details.

Processing time may vary depending on several factors, including the complexity of the claim, the availability of information, and the member's medical history. Additionally, if the claim requires further investigation, it may take longer to process. In some cases, claims can take several weeks or even months to be processed, depending on the specific circumstances. It's important to be patient with the process and seek clarification if needed for your claim.

**User:**

Can you explain to me how healthcare claims processing works? I have been working on a procurement team for a healthcare payer for several years. We have a vendor that promises to do real-time, as opposed to batch, claims processing. I want to better understand how that could help us

**LLM:**

Healthcare claims processing is the process of verifying, coding, and reimbursing medical claims made by healthcare providers for treatment rendered to patients. Typically, this involves sending claims to a payer, who then reviews and approves them.

Real-time claims processing differs from batch processing in that instead of collecting and reviewing claims in large batches on a regular basis, claims are processed on an individual basis as they are received. This allows for quicker processing times and potentially more efficient use of healthcare resources.

By using real-time claims processing, a payer can also gain valuable insights and understanding of the healthcare system as claims are processed. This can help them make more informed decisions and better manage the healthcare coverage they provide to their customers. Additionally, real-time claims processing can improve provider satisfaction, as they don't have to wait for weeks or months to receive payment for their services.

Overall, real-time claims processing can bring several benefits, such as faster processing times, improved provider satisfaction and understanding of healthcare system, and more efficient use of healthcare resources.

*Note: With the given context, the LLM assumes the user already knows the basics of claims processing and gives a much more specific answer*

---

### Problem Action Result (PAR)

Example:

**User:**

Problem: A member's claim was denied.

Action: Please draft a letter to the provider stating the reasons for the denial.

Result: The provider can either accept the result. But also allow him the option to submit the claim with new information that might allow the claim to be accepted

**LLM:**

[Provider's Name]

[Provider's Address]

[City, State, Zip Code]

Subject: Denial of Member's Claim - Request for Reconsideration

Dear [Provider's Name],

I hope this letter finds you well. I am writing on behalf of [Insurance Company Name] to inform you of the recent denial of a claim submitted by one of our members, [Member's Name]. We understand the importance of providing quality healthcare services and want to maintain a transparent and collaborative relationship with our valued providers.

Claim Details:

Member: [Member's Name]

Claim Number: [Claim Number]

Date of Service: [Date of Service]

Amount Claimed: [Claimed Amount]

Reason for Denial: [Brief Explanation of Denial]

Reasons for Denial:

Upon review of the claim, it was determined that there were specific reasons for its denial, which include [briefly outline the key reasons for denial, such as missing documentation or incorrect coding]. We acknowledge the possibility of human error or incomplete information contributing to the denial and want to ensure a fair and accurate assessment of the claim.

Options for Resolution:

We value our partnership with your facility and recognize that misunderstandings or omissions can occur during the claim submission process. Therefore, we would like to offer the following options for resolution:

Acceptance of Denial: You may choose to accept the denial decision as it stands.

Reconsideration with Additional Information: If you believe that there is additional information or documentation that could support the validity of the claim, we encourage you to resubmit the claim with the necessary details. Please ensure that any new information is clearly highlighted for our review.

We appreciate your prompt attention to this matter and kindly request your response within [reasonable timeframe] to inform us of your chosen course of action.

Should you decide to submit additional information or have any questions regarding this matter, please do not hesitate to contact our Claims Department at [Claims Department Contact Information].

We value your partnership and aim to provide the best possible healthcare services to our members. Your cooperation in resolving this matter is highly appreciated.

Thank you for your understanding and collaboration.

Sincerely,

[Your Name]

[Your Title]

[Insurance Company Name]

[Contact Information]

*Note: while specifying the prompt in the PAR format, the LLM gives a concise and specific output the the requested format.*

---

### Contrastive (or Contrafactual) Prompting

*Give the LLM a negative example (don’t do this…). Prompts including words like “because,” “explain,” and “despite” are often implicitly using this method.*

Example:

**User:**

I work for a healthcare payer. Explain to me how a more efficient prior authorization system would benefit my organization. ****Don't tell me how it will affect our budget. Instead, focus on how it would improve member experience.

**LLM:**

An efficient prior authorization system in healthcare enhances member experience in several key ways. First, it speeds up access to care, as members receive quicker approvals for treatments and medications, reducing wait times and uncertainty. Second, it simplifies the healthcare journey, cutting down on administrative complexities and frustrations often encountered by members. This streamlined process leads to increased member satisfaction and trust in the healthcare system. Additionally, clearer communication and transparency in the authorization process improve member understanding and engagement, leading to better health outcomes. Overall, a more efficient system contributes to a smoother, more positive healthcare experience for members.

*Note: the LLM did not mention budget*

---

### Role Task Format (RTF)

[Brainstorm & Ideation (Guided Example)](https://www.notion.so/Brainstorm-Ideation-Guided-Example-980c568b09d744ac83e46bfd46e38a71?pvs=21) 

---

### Chain of Thought

Chain of thought prompting means asking the LLM to break down a complex problem and tackle it step by step. It is often useful for math problems or other tasks that require complex logic and reasoning. Appending a phrase like “let’s think this step by step” is often enough to substantially improve the LLM output. 

Example **without** chain of thought**:**

**User:** Your department has a budget of $50,000. You spend $10,000 on new software licenses and allocate $15,000 for marketing. You later receive a budget increase of $5,000. What is your remaining budget?

**LLM:** You have a remaining budget of $20,000 after spending $10,000 on new software licenses, $15,000 on marketing, and taking a $5,000 budget increase.

N*ote: the answer is incorrect*

**With chain of thought:**

**User:**  Your department has a budget of $50,000. You spend $10,000 on new software licenses and allocate $15,000 for marketing. You later receive a budget increase of $5,000. What is your remaining budget? **Let’s think step by step.**

**LLM:**

Sure, let's break it down step by step:

1. Your department initially has a budget of $50,000.

2. You spend $10,000 on new software licenses.

3. You allocate $15,000 for marketing.

4. So, your original budget is now at $50,000 - $10,000 (software licenses) - $15,000 (marketing) = $25,000 remaining.

5. Then, you receive a budget increase of $5,000.

6. So, your new budget is at $25,000 (original) + $5,000 (budget increase) = $30,000.

Therefore, your department has a remaining budget of $30,000.

N*ote: By simply appending “*Let’s think step by step.*” to the end of the prompt, the LLM automatically breaks down the question into steps, which helps it get to the right answer. It decided unprompted to output a list of each stage in its reasoning.*

---

### Avoiding Hallucinations

************************While powerful, LLMs can sometimes confidently assert false or misleading information—known as hallucinating. Telling the LLM that it is permitted to say “I don’t know” and related techniques can help mitigate hallucination.************************ 

1. Tell LLM not to make things up
2. Tell LLM to say say “I don’t know” if it does not know the answer
3. Ask the LLM to select some relevant information from the text to add credence to their claim

Example with warning against hallucination:

**User:** You are a healthcare insurance expert. What is HCPCS code 2JZF84? **It is ok to say "I don't know" if you don't know**

**LLM:** I apologize, I couldn't find any information about HCPCS code 2JZF84. Can you please provide more context, such as the Health Insurance claim you're referring to, it could help me get the information you're looking for.

---

**User:** What is CPT code 48636? **It is ok to say "I don't know" if you don't know**

**LLM:**

I couldn't find specific information about CPT code 48636. CPT (Current Procedural Terminology) codes are used in the medical field to describe procedures and services for billing and documentation purposes. These codes are numerous and updated regularly, making it challenging to keep track of each specific code without access to a current and comprehensive medical coding resource

**User:** What about 90630?

**LLM:**

CPT code 90630 refers to the influenza virus vaccine, which is a quadrivalent (IIV4) vaccine. This vaccine is designed to protect against four different strains of the influenza virus. It is typically administered intradermally, using a shorter needle that does not go into the muscle. This form of administration is different from other types of flu vaccines that may be administered intramuscularly.

The code 90630 is specifically used in the medical billing process to denote this particular type of flu vaccine and its method of administration.

---

Example without warning against hallucination:

**User:** You are a healthcare insurance expert. **What is CPT code 97826?**

**LLM:**

CPT Code 97826 represents a specific medical service or procedure within the Current Procedural Terminology (CPT) system. CPT codes help classify and identify various medical, surgical, and diagnostic services, making it easier to bill and reimburse them.

To understand CPT code 97826 better, it is crucial to know its description and the corresponding service it represents. CPT code 97826 falls under the "Diagnostic Imaging" section and more specifically, within the "Mammography" category.

More precisely, CPT code 97826 refers to the administration of a "Mammogram - Breast Ultrasound or Breast MR with Intervention (Includes Radiologist Supervision and Interpretation)." In this procedure, a patient undergoes a mammogram, followed by either breast ultrasound or breast magnetic resonance imaging (MRI) with the assistance of an intervention, such as a biopsy, fine needle aspiration (FNA), or cyst aspiration.

*Note: the above is entirely hallucinated. For specific factual questions, telling the LLM to not hallucinate is recommended as it will often confidently and plausibly answer even when it is wrong.* 

---

## IV. Tips

Below are some general tips to keep in mind that may improve LLM output

1. Encourage the LLM (“this is important,” “feel free to be creative”)
2. They are open to correction (“I don’t think you understood what I wanted; let me rephrase…”)
3. Ask it to self-check (“are you sure? Couldn’t it be…?”)
    1. Although sometime an LLM will overcorrect itself, going from a good answer to a worse one
4. Context helps (“You are writing an email to a member…”)
    1. If stuck, try starting with broader context, getting a general response, then iteratively improving on it as you layer in more context.
    2. Provide the LLM with an example of the kind of response you want
5. Provide positive and negative instructions (“Instead of X, do Y”)
6. Specify the length of the output (“keep your summary to about 100 words”) 
7. Clearly separate instruction and context
    1. Possibly putting context in between block quotes or some other demarcation symbol as applicable
        
        Example:
        
        User: Please summarize the this text: {text}
        
        LLM: {summary}
        
        ---
        
        User: Please summarize this text between the block quotes:
        
        ‘ ‘ ‘
        
        {text}
        
        ‘ ‘ ‘
        
        LLM: {better summary}
        
8. Specify the intermediate steps (“first calculate X, then use X to find Y”)

---

## V. References

[OpenAI’s Prompt Engineering Guide](https://platform.openai.com/docs/guides/prompt-engineering)

[LegalPromptGuide.com](https://www.legalpromptguide.com/1.-introduction-to-legal-prompt-engineering-lpe)

[12 Prompt Engineering Techniques: Cobus Greyling](https://cobusgreyling.medium.com/12-prompt-engineering-techniques-644481c857aa)

[Advanced Chain of Thought Prompting (Medium)](https://medium.com/@hello_21549/a-deep-dive-into-prompt-engineering-techniques-fd28ab695076)

[7 Prompt Patterns You Should Know](https://medium.com/@corraljrmiguel/21-prompt-patterns-you-should-know-636c931bba2a)