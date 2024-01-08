### Chain of Thought

*Chain of thought prompting means asking the LLM to break down a complex problem and tackle it step by step. It is often useful for math problems or other tasks that require complex logic and reasoning. Appending a phrase like “let’s think this step by step” is often enough to substantially improve the LLM output.* 

Example **without** chain of thought:

>**User:** Your department has a budget of $50,000. You spend $10,000 on new software licenses and allocate $15,000 for marketing. You later receive a budget increase of $5,000. What is your remaining budget?

>**LLM [QS-LLM Aligned]:** You have a remaining budget of $20,000 after spending $10,000 on new software licenses, $15,000 on marketing, and taking a $5,000 budget increase.

*Note: the answer is incorrect*

**With chain of thought:**

>**User:**  Your department has a budget of $50,000. You spend $10,000 on new software licenses and allocate $15,000 for marketing. You later receive a budget increase of $5,000. What is your remaining budget? **Let’s think step by step.**

>**LLM [QS-LLM Aligned]:**
>
>Sure, let's break it down step by step:
>
>1. Your department initially has a budget of $50,000.
>
>2. You spend $10,000 on new software licenses.
>
>3. You allocate $15,000 for marketing.
>
>4. So, your original budget is now at $50,000 - $10,000 (software licenses) - $15,000 (marketing) = $25,000 remaining.
>
>5. Then, you receive a budget increase of $5,000.
>
>6. So, your new budget is at $25,000 (original) + $5,000 (budget increase) = $30,000.
>
>Therefore, your department has a remaining budget of $30,000.

*Note: By simply appending “*Let’s think step by step.*” to the end of the prompt, the LLM automatically breaks down the question into steps, which helps it get to the right answer. It decided unprompted to output a list of each stage in its reasoning.*