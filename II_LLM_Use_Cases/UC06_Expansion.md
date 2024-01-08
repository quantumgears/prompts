### UC06: Expansion

*Given limited text, e.g., barely comprehensible benefits notes, expansion means the process of filling in the gaps and making the text more understandable. In the example below, we provide responses from three different LLMs. As expected, GPT-4 gives the best response. This example illustrates the danger of hallucination.* 

>**User:**
>
>You are a healthcare expert who understands medical codes (CPT, ICD, HCPCS). You serve as a customer services rep. You take calls from external personas such as members and providers. I am going to give you notes from the interaction between you and the external persona.
>
>Here is the text from the notes:
>
>prov called to see if J1439 needed auth, acc to Med drug req auth page, obn and be no auth needed
>
>Action : I want you to 1) Make the notes human readable along with a detailed explanation of any codes. 2) Brainstorm on why the caller had to call. 3) Provide alternatives to the call (e.g., a website they can go to in the future).

>**LLM [GPT-4]:** 
>
>Based on the provided notes, here's a clearer and more detailed explanation:
>
>1. **Human-Readable Explanation of the Notes:**
    >- **Original Note:** "prov called to see if J1439 needed auth, acc to Med drug req auth page, obn and be no auth needed"
    >- **Interpreted Note:** A provider (prov) called to inquire if the medication identified by the code J1439 requires authorization. According to the medical drug requirements authorization page, this particular medication, both on-brand (obn) and its bioequivalent (be), does not require authorization.
>2. **Explanation of Codes:**
    >- **J1439:** This is a HCPCS (Healthcare Common Procedure Coding System) code. HCPCS codes are used to represent medical procedures, equipment, and services. J1439 specifically refers to an injectable medication, often used in the context of billing and insurance claims.
    >- **Auth:** This is shorthand for "authorization." In a healthcare context, authorization is often required by insurance companies before certain medications or treatments are provided, to ensure they are medically necessary and covered under the patient's plan.
>3. **Brainstorming on Why the Caller Had to Call:**
    >- **Lack of Access or Familiarity with Online Resources:** The provider may not have had easy access to the medical drug requirements authorization page or may not be familiar with how to navigate it.
    >- **Need for Confirmation:** They might have wanted to double-check the information for accuracy to avoid any issues with insurance claims.
    >- **Complexity of Information:** Healthcare coding and authorization can be complex, and the provider may have needed clarification or reassurance from a human representative.
>4. **Alternatives to Calling:**
    >- **Dedicated Online Portal:** Encourage providers to use a specific online portal where they can check medication codes like J1439 for authorization requirements. This portal should be user-friendly and regularly updated.
    >- **Regular Updates via Email or App Notifications:** Sending updates or newsletters to providers about common codes and their authorization requirements.
    >- **Training Sessions:** Offering periodic training sessions or webinars to educate providers on how to navigate the healthcare coding system and authorization processes.
    >- **Comprehensive FAQ Section:** Developing a detailed FAQ section on the website that covers common queries about medication codes and authorization.
    >- **Chat Support:** Implementing a chatbot or live chat support on the website for quick inquiries, reducing the need for phone calls.
>
>These alternatives can help streamline the process, making it more efficient for providers to find the information they need without having to make a phone call.
---
>**LLM [GPT-3.5]:**
>
>Notes:
>The provider (prov) called to inquire about the need for authorization for the medication with the code J1439. According to the medical drug requirements authorization page, it states that this medication does not require authorization.
>
>Explanation:
>
>1. J1439 is a Healthcare Common Procedure Coding System (HCPCS) code. It represents an unclassified drug code, often used for billing purposes in healthcare. In this case, the provider was inquiring about whether authorization (often required for certain medications or treatments) was needed for a medication with this specific HCPCS code.
>2. The reason the caller (the provider) had to make this call could be due to several factors:
    >- The provider may not have had access to the most up-to-date authorization information, so they needed to confirm whether J1439 required authorization.
    >- There may have been recent changes in authorization requirements for this medication, and the provider needed to verify the current status.
    >- It's possible that the provider wanted to ensure they had accurate information before prescribing or administering the medication to a patient, as authorization can impact reimbursement and patient care.
>3. Alternatives to the call:
    >- Providers can often find authorization information on their healthcare organization's or insurance company's website. They should check the specific authorization requirements section to verify if a particular medication requires authorization.
    >- Some healthcare organizations also provide electronic tools or portals where providers can check authorization requirements in real-time, reducing the need for phone calls.
    >- If the provider is unsure about authorization requirements, they can contact the patient's insurance company directly through their provider portal or customer service line to inquire about specific medication authorization.
>
>In summary, the caller (provider) was seeking confirmation on whether medication with the code J1439 required authorization. To avoid such calls in the future, providers should utilize online resources and portals or contact the insurance company directly for authorization information.
---
>**LLM [QS-LLM Aligned]:** 
>
>Action 1) Make the notes human readable along with a detailed explanation of any codes: The note mentions that the caller is checking about the medical code J1439 and the necessity of its authorization according to the medication drug request authorization page. The code J1439 refers to a specific medical procedure, but without the context, it is not possible to provide an accurate explanation. It might be related to diagnostic radiology, cardiology, or ophthalmology procedures, as these are some common specialties where J codes are used.
>
>Obn stands for Obstetrics and Gynecology, and be for Bone and Joint Surgery, which are specialties within the medical field. The note further clarifies that there is no authorization needed for this particular situation.
>
>Action 2) Brainstorm on why the caller had to call: The caller might have had a need to verify the specific medical procedure (represented by the code J1439) and its requirements for authorization. They could be unsure about the exact process and wanted clarification from the healthcare expert, which they found in the notes provided.
>
>Action 3) Provide alternatives to the call (e.g., a website they can go to in the future): To help prevent future calls related to this topic, providing the caller with a link to a reliable source for understanding medical codes and procedures (such as a website for a reputable healthcare organization) could be beneficial. This will give the caller the ability to look up the necessary information without having to call each time.
---
*Note the large variation in responses for a difficult task like this. Also note the hallucinations by the smaller models.*

See [Avoiding Hallucinations ](/III_Prompt_Engineering_Patterns/Avoiding_Hallucinations.md) for tips on avoiding hallucinations. 

**Exercises:**

- Ensure that the model used correctly identifies the medical code (J1439), OBN and, BE
- Resend the notes but provide the LLM with context, e.g., tell it that J1439 is an HCPCS code