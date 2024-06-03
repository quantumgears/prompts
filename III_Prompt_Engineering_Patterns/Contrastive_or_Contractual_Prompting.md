### Contrastive (or Contrafactual) Prompting

*Give the LLM a negative example (don’t do this…). Prompts including words like “because,” “explain,” and “despite” are often implicitly using this method.*

Example:

User:
```
I work for a healthcare payer. Explain to me how a more efficient prior authorization system would benefit my organization. Don't tell me how it will affect our budget. Instead, focus on how it would improve member experience.
```
>**LLM [QS-LLM Aligned]:**
>
>An efficient prior authorization system in healthcare enhances member experience in several key ways. First, it speeds up access to care, as members receive quicker approvals for treatments and medications, reducing wait times and uncertainty. Second, it simplifies the healthcare journey, cutting down on administrative complexities and frustrations often encountered by members. This streamlined process leads to increased member satisfaction and trust in the healthcare system. Additionally, clearer communication and transparency in the authorization process improve member understanding and engagement, leading to better health outcomes. Overall, a more efficient system contributes to a smoother, more positive healthcare experience for members.

*Note: the LLM did not mention budget*