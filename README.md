## Design and Implementation of LangChain Expression Language (LCEL) Expressions

### AIM:
To design and implement a LangChain Expression Language (LCEL) expression that utilizes at least two prompt parameters and three key components (prompt, model, and output parser), and to evaluate its functionality by analyzing relevant examples of its application in real-world scenarios.

## PROBLEM STATEMENT:
To create an LCEL chain that accepts two inputs and generates meaningful responses using a language model.

## DESIGN STEPS:

### STEP 1:
Import the required libraries and load the API key.

### STEP 2:
Create a prompt with two parameters and initialize the model and output parser.

### STEP 3:
Connect the components using the LCEL pipe operator (`|`) and execute the chain.

## PROGRAM:
```
import os
import openai

from dotenv import load_dotenv, find_dotenv
_ = load_dotenv(find_dotenv())
openai.api_key = os.environ['OPENAI_API_KEY']

from langchain.prompts import ChatPromptTemplate
from langchain.chat_models import ChatOpenAI
from langchain.schema.output_parser import StrOutputParser

prompt = ChatPromptTemplate.from_template(
    "Suggest a suitable {career} learning roadmap for a student "
    "with an interest in {skill}. Include useful skills and projects."
)

model = ChatOpenAI(model="gpt-4o-mini", temperature=0.7)
output_parser = StrOutputParser()

chain = prompt | model | output_parser

response = chain.invoke({
    "career": "AI Engineer",
    "skill": "Python programming"
})

print("Career Guidance:")
print(response)
```
## OUTPUT:

<img width="1920" height="1080" alt="Screenshot (620)" src="https://github.com/user-attachments/assets/e0df489b-e59b-48f6-9ac2-c77f33bdffec" />


### Real-World Applications:

1. Healthcare Assistance – Summarize medical reports and provide general health information.
2. Legal Document Analysis – Summarize legal documents and identify important clauses.
3. E-commerce Automation – Automatically answer product-related questions and track customer orders.
4. Resume Screening – Analyze resumes and identify candidates based on job requirements.
5. Travel Planning – Generate travel itineraries based on budget, location, and travel dates.

## RESULT:

Thus, the LCEL expression was successfully implemented using two prompt parameters and three key components. The chain generated meaningful responses and demonstrated its applications in real-world scenarios.
