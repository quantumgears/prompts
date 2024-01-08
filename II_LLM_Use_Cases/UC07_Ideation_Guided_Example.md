### UC07: Ideation (Guided Example)

*This example uses a common prompting technique called “Role Task Format”*

User:
```
You are an expert in health insurance. Generate an example healthcare taxonomy. Be sure to include Mental Health and Prescription Drugs. The taxonomy only needs to be two nodes deep.
```
*Notice usage of RTF (Role, Task, Format) prompt here. And the user specifies to keep the taxonomy shallow at first, starting general and leaving room for later iteration once the user is happy with the first two levels.*

>**LLM [GPT-4]:**
>
>Creating a healthcare taxonomy with a focus on Mental Health and Prescription Drugs, while keeping it two nodes deep, would look something like this:
>
>Mental Health
>
>- Counseling Services
>- Psychiatric Treatments
>- Support Groups
>- Stress Management Programs
>- Substance Abuse Therapy
>- Prescription Drugs
>
>Antibiotics
>
>- Pain Management Medications
>- Psychotropic Medications
>- Cardiovascular Drugs
>- Diabetes Medications
>
>This structure provides a clear and concise overview, categorizing key areas within Mental Health and Prescription Drugs. Each sub-category under these two main nodes represents a specific aspect or type of service/medication within the broader category.

User:
```
Can you add a third layer of depth? It should give a brief explanation of the node one up the tree
```
*Instruct the LLM specifically with how it should extend its earlier output. "Context" is preserved, meaning it will remember its previous outputs.*

>**LLM [GPT-4]:**
>
>Certainly! Adding a third layer to the healthcare taxonomy provides more detail about each sub-category. Here's how it would look with a brief explanation for each:
>
>1. **Mental Health**
>    - **Counseling Services**: Individual or group sessions focusing on emotional and psychological health.
>        - *Individual Therapy*: One-on-one sessions addressing personal issues.
>        - *Group Therapy*: Sessions with multiple participants sharing common issues.
>    - **Psychiatric Treatments**: Medical interventions for mental health disorders.
>        - *Medication Management*: Overseeing and adjusting psychiatric medications.
>        - *Psychotherapy*: Treatment involving therapeutic conversations and interactions.
>    - **Support Groups**: Gatherings for people sharing similar issues or experiences.
>        - *Peer-led Groups*: Support sessions led by individuals with shared experiences.
>        - *Professional-led Groups*: Facilitated by trained mental health professionals.
>    - **Stress Management Programs**: Techniques and strategies to manage stress.
>        - *Relaxation Techniques*: Methods like meditation, deep breathing, and yoga.
>        - *Time Management Counseling*: Training in managing time effectively to reduce stress.
>    - **Substance Abuse Therapy**: Treatments for addiction and substance misuse.
>        - *Detoxification Programs*: Medical and therapeutic support during substance withdrawal.
>        - *Rehabilitation Programs*: Long-term treatment plans for recovery and sobriety.
>2. **Prescription Drugs**
>    - **Antibiotics**: Medications used to treat bacterial infections.
>        - *Broad-Spectrum Antibiotics*: Effective against a wide range of bacteria.
>        - *Narrow-Spectrum Antibiotics*: Target specific types of bacteria.
>    - **Pain Management Medications**: Drugs prescribed to alleviate chronic or acute pain.
>        - *Nonsteroidal Anti-Inflammatory Drugs (NSAIDs)*: Medications reducing inflammation and pain.
>        - *Opioids*: Strong pain relievers for severe pain management.
>    - **Psychotropic Medications**: Drugs affecting mood, perception, or consciousness.
>        - *Antidepressants*: Medications for treating depression and anxiety disorders.
>        - *Antipsychotics*: Used for managing conditions like schizophrenia and bipolar disorder.
>    - **Cardiovascular Drugs**: Medications for heart and blood vessel conditions.
>        - *Antihypertensives*: Drugs used to lower high blood pressure.
>        - *Statins*: Medications that help lower cholesterol levels.
>    - **Diabetes Medications**: Drugs used for managing blood sugar levels.
>        - *Insulin*: Hormone replacement therapy for Type 1 Diabetes.
>        - *Oral Hypoglycemics*: Medications that help increase insulin production for Type 2 Diabetes.
>
>This expanded taxonomy provides a more comprehensive understanding of the services and medications within the Mental Health and Prescription Drugs categories.

User:
```
Why wasn't equine therapy included under mental health? Is equine therapy not a kind of mental health?
```
*An example of self-check: The user wonders why a specific therapy that he is aware of was not included in this high level taxonomy, so asks the LLM to check itself.* 

>**LLM [GPT-4]:**
>
>Equine therapy, also known as horse therapy or equine-assisted therapy, is indeed a recognized form of therapy that can have significant benefits for mental health. It was not included in the initial taxonomy primarily due to the broad scope of mental health services, and the need to select a limited number of examples for a concise taxonomy. However, it certainly deserves mention, especially in a more comprehensive taxonomy.
>
>Equine therapy involves interactions with horses and is used to promote emotional growth and healing. It is particularly effective for individuals dealing with issues such as trauma, depression, anxiety, and behavioral challenges. The therapy includes activities like grooming, feeding, leading, and riding horses under the guidance of a trained therapist. These activities are designed to help develop skills such as emotional regulation, responsibility, confidence, and empathy.
>
>To include equine therapy in the taxonomy, it would fit under
>
>- **Experiential and Alternative Therapies**: Non-traditional therapies using various activities.
>    - Equine Therapy (Horse Therapy): Activities involving horses to aid emotional and psychological healing.
>    - Art Therapy: Using the creative process of art making to improve physical, mental, and emotional well-being.
>
>This expanded taxonomy now includes Equine Therapy, acknowledging its role in mental health treatment and its unique approach to healing and personal development.

*Notice that the LLM explains why it was not included: equine therapy is too specific for a general, high-level taxonomy like this. And also notice that the LLM generated a new high-level node ("Experimental and Alternative Therapies") under which equine therapy could fit and added a sub-node, "Art Therapy" that also fits under the new node.*

**Exercises:**

- Instruct the LLM to add a new sub-node under Prescription Drugs
- Change the style of the taxonomy to be comprehensible to a non-expert