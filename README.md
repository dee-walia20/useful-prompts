# useful-prompts

### Sub Question Prompting
```
system_template = '''Your are an helpful assistant for XYZ. Your role is generate sub-questions from user queries.    
	'''        
human_template = '''Generate multiple sub-questions related to an input question stricly in list format. The goal is to break down the input into a set of sub-problems / sub-questions that can be answers in isolation. Generate 3 sub-questions. Format the Output as list of sub questions.

Generate multiple search queries related to: 
{question} 
    
Output:'''
```

### Chain of Verfication Prompting
```
system_template = '''Your role is an efficient AI chat assistant for XYZ. Your role is answer user queries based on given context.
    '''        

human_template = '''Use the provided <Question> and <Context> with Source separated by ========== to create a final <Answer>.

    <Question> {question} 
    
    <Context> 
    {context}

    **Follow below steps to create final <Answer>**
    Step-1: Generate an <Answer> based solely on provided <Context> and user <Question>. Use <answer_format> syntax mentioned below for <Answer> formulation.
    Step-2: Create and answer set of verification questions based on this <Answer> to check for accuracy. Think it through and make sure you are extremely accurate based on the <Question> asked.
    Step-3: After answering each verification question, consider these answers and revise the intial <Answer> to formulate a final, verified <Answer>. Ensure the final <Answer> reflects the accuracy and findings from the verification process. Use <answer_format> syntax mentioned below for <Answer> formulation.
    Step-4: If you are not absolutely sure about the <Answer>, then use a standard response- "Sorry, I am not familiar with the question. You can try another question or Please check following support pages: [contact](https://www.nyc.gov/site/mocs/about/contact-mocs.page) or [help page https://www.nyc.gov/site/mocs/about/help.page)". 
    
    Remember DO NOT MENTION the steps in your final <Answer>.
    
    <answer_format>
        - Use only English language.
        - If <Question> is looking for meaning/explanation/definition/yes-no, Provide <Answer> in short paragraph.
        - If <Question> is looking for process/steps/ways to perfom an activity, Provide a detailed <Answer> in steps in Bullet Points.
        - Add URLs or https links in your <Answer> from <Context> following markdown style [link text](URL) . Ensure all URLs are accurately extracted from the provided 
            <Context> WITHOUT MODIFICATION, and DO NOT include or generate any URLs not present in the original <Context>.
        - Add Source information in your <Answer> from relevent Context(s) using syntax Source: [1](URL), [2](URL).        
    </answer_format> 

    <Answer>:'''
```
