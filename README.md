## Design and Implementation of LangChain Expression Language (LCEL) Expressions

### AIM:
To design and implement a LangChain Expression Language (LCEL) expression that utilizes at least two prompt parameters and three key components (prompt, model, and output parser), and to evaluate its functionality by analyzing relevant examples of its application in real-world scenarios.

### PROBLEM STATEMENT:
This problem  is to create a simple LangChain chain that translates text from one language to another.
A prompt template is used to take the topic and target language as inputs.
The ChatOpenAI model processes the input using the defined prompt.
The output parser then returns the translated text in the desired language.

### DESIGN STEPS:

#### STEP 1:
Import necessary libraries, load the API key, and define the translation prompt template using {topic} and {language}.

#### STEP 2:
Initialize the ChatOpenAI model and output parser to handle responses.

#### STEP 3:
Link the prompt, model, and parser into a simple chain and invoke it with sample inputs for translation.

### PROGRAM:

```

import os
import openai

from dotenv import load_dotenv, find_dotenv
_ = load_dotenv(find_dotenv()) # read local .env file
openai.api_key = os.environ['OPENAI_API_KEY']

from langchain.prompts import ChatPromptTemplate
from langchain.chat_models import ChatOpenAI
from langchain.schema.output_parser import StrOutputParser

prompt = ChatPromptTemplate.from_template(
    "Translate the following {topic} into {language}"
)
model = ChatOpenAI()
output_parser = StrOutputParser()

chain = prompt | model | output_parser

chain.invoke({
    "topic": "Good morning, how are you?",
    "language": "French"
})

```
### OUTPUT:

<img width="242" height="40" alt="image" src="https://github.com/user-attachments/assets/c6cb29d0-a77d-48e9-bec0-7eb8959a29cd" />

### RESULT:

The designed LangChain translation chain executed successfully, taking user input in English and translating it into French.
It demonstrated effective integration of prompt, model, and parser components.
