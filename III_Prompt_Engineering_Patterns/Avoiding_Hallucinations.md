### Avoiding Hallucinations

*While powerful, LLMs can sometimes confidently assert false or misleading information—known as hallucinating. Telling the LLM that it is permitted to say “I don’t know” and related techniques can help mitigate hallucination.*

1. Tell LLM not to make things up
2. Tell LLM to say “I don’t know” if it does not know the answer
3. Ask the LLM to select some relevant information from the text to add credence to their claim

Example **with warning** against hallucination:

>**User:** You are a healthcare insurance expert. What is HCPCS code 2JZF84? **It is ok to say "I don't know" if you don't know**

>**LLM [GPT-4]:** I apologize, I couldn't find any information about HCPCS code 2JZF84. Can you please provide more context, such as the Health Insurance claim you're referring to, it could help me get the information you're looking for.

---

>**User:** What is CPT code 48636? **It is ok to say "I don't know" if you don't know**

>**LLM [GPT-4]:**
>
>I couldn't find specific information about CPT code 48636. CPT (Current Procedural Terminology) codes are used in the medical field to describe procedures and services for billing and documentation purposes. These codes are numerous and updated regularly, making it challenging to keep track of each specific code without access to a current and comprehensive medical coding resource

>**User:** What about 90630?

>**LLM [GPT-4]:**
>
>CPT code 90630 refers to the influenza virus vaccine, which is a quadrivalent (IIV4) vaccine. This vaccine is designed to protect against four different strains of the influenza virus. It is typically administered intradermally, using a shorter needle that does not go into the muscle. This form of administration is different from other types of flu vaccines that may be administered intramuscularly.
>
>The code 90630 is specifically used in the medical billing process to denote this particular type of flu vaccine and its method of administration.

---

Example **without warning** against hallucination:

>**User:** You are a healthcare insurance expert. **What is CPT code 97826?**

>**LLM [GPT-3.5]:**
>
>CPT Code 97826 represents a specific medical service or procedure within the Current Procedural Terminology (CPT) system. CPT codes help classify and identify various medical, surgical, and diagnostic services, making it easier to bill and reimburse them.
>
>To understand CPT code 97826 better, it is crucial to know its description and the corresponding service it represents. CPT code 97826 falls under the "Diagnostic Imaging" section and more specifically, within the "Mammography" category.
>
>More precisely, CPT code 97826 refers to the administration of a "Mammogram - Breast Ultrasound or Breast MR with Intervention (Includes Radiologist Supervision and Interpretation)." In this procedure, a patient undergoes a mammogram, followed by either breast ultrasound or breast magnetic resonance imaging (MRI) with the assistance of an intervention, such as a biopsy, fine needle aspiration (FNA), or cyst aspiration.

*Note: the above is entirely hallucinated. For specific factual questions, telling the LLM to not hallucinate is recommended as it will often confidently and plausibly answer even when it is wrong.* 