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
