## IV. Tips

Below are some general tips to keep in mind that may improve LLM output

1. Encourage the LLM (“this is important,” “feel free to be creative”)
2. They are open to correction (“I don’t think you understood what I wanted; let me rephrase…”)
3. Ask it to self-check (“are you sure? Couldn’t it be…?”)
    1. Although sometimes an LLM will overcorrect itself, going from a good answer to a worse one
4. Context helps (“You are writing an email to a member…”)
    1. If stuck, try starting with broader context, getting a general response, then iteratively improving on it as you layer in more context.
    2. Provide the LLM with an example of the kind of response you want
5. Provide positive and negative instructions (“Instead of X, do Y”)
6. Specify the length of the output (“keep your summary to about 100 words”) 
7. Clearly separate instruction and context
    1. Possibly putting context in between block quotes or some other demarcation symbol as applicable
        
        Example:
        
        >User: Please summarize this text: {text}
        
        >LLM: {summary}
        
        ---
        
        >User: Please summarize this text between the block quotes:
        >
        >‘ ‘ ‘
        >
        >{text}
        >
        >‘ ‘ ‘
        
        >LLM: {better summary}
        
8. Specify the intermediate steps (“first calculate X, then use X to find Y”)
