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
    Step-4: If you are not absolutely sure about the <Answer>, then use a standard response- "Sorry, I am not familiar with the question. You can try another question or Please check following support pages: xyz.com". 
    
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

### Question Answer Generation Prompting
#### Long QA
```
system_template_long_qa = '''Your role is to generate question answer pairs from given document.'''    

human_template_long_qa = '''Given the [Document], create a set of [Question] and [Answer] pairs that are grounded in the main points of the 
[Document], don't add any additional information that is not in the [Document]. The [Question] is by an information-seeking User and the [Answer] 
is provided by a helping AI Agent. [Document] will be related to xyz domain. Create [Question], where [Answer] requires detailed steps in bullet points explaining process more than 500 words. Number of [Question] [Answer] pair should be determined to cover all the main points in the [Document]. DO NOT repeat [Question]. Keep Output format as below.

<format>
[Question]:
[Answer]:
##
[Question]:
[Answer]:
</format>

[Document] 
{document} 

Output:'''
```

#### Short QA
```
system_template_short_qa = '''Your role is to generate question answer pairs from given procurement document.'''    

human_template_short_qa = '''Given the [Document], create set of 5-10 [Question] and [Answer] pairs that are grounded in the main points of the 
document, don't add any additional information that is not in the document. The [Question] is by an information-seeking User and the [Answer] 
is provided by a helping AI Agent. [Document] will be related to xyz domain. Create [Question] where [Answer] requires long answer (2-6 sentences) amd looking for brief explanation/Yes-No/definition/general information etc. DO NOT REPEAT SIMILAR [Question] to [Previous Questions] list. Create NEW [Question] covering other points and Number of [Question] [Answer] pair should be determined to cover all these other points from the [Document]. Keep Output format as below.

<format>
[Question]:
[Answer]:
##
[Question]:
[Answer]:
</format>

[Document] 
{document} 

[Previous Questions]
{previous_questions}

Output:'''
```
