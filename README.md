# Simple-langchain-tools

## 1. Simple Calculator Tool with LangChain Agent (Gemini)

### Overview

This project demonstrates how to build a **secure arithmetic calculator tool** and integrate it into a **LangChain tool-calling agent** powered by Google Gemini.

Instead of relying on the LLM to compute math internally, the agent is required to call a **custom calculator tool** that safely evaluates expressions using Python’s `ast` module.

This approach ensures:

- Deterministic results  
- No hallucinated arithmetic  
- Secure expression evaluation  
- Controlled operator usage  

---

### Key Features

#### i. Secure Arithmetic Engine

- Uses Python `ast` parsing  
- Supports only safe operators: `+`, `-`, `*`, `/`, `//`, `%`, `**`  
- Blocks unsafe code execution  
- Limits expression length  
- Prevents extremely large outputs  

#### ii. Custom LangChain Tool

- Calculator is wrapped using the `@tool` decorator  
- Returns only numeric output  
- Handles errors gracefully  

#### iii. Tool-Calling Agent (Gemini)

- Built using:  
  - `ChatGoogleGenerativeAI` (gemini-2.0-flash)  
  - `create_tool_calling_agent`  
  - `AgentExecutor`  
- System prompt enforces strict rules:  
  - Always use the calculate tool for arithmetic  
  - Convert natural language into a valid math expression  
  - Convert `^` into `**` for exponentiation  
  - Return only numeric results when requested  

---

### Experiment: LLM vs Agent with Calculator

To compare performance, the following approaches were tested:

- Plain LLM (no tool)  
- Agent with calculator tool  

#### Questions Tested

1. What is 234 * 19?  
2. Compute `(12345 * 6789) + 98765`  
3. What is `13.7% of 12345 plus 98.76^2`? Round to 2 decimals  

#### Trial Output

**LLM Only** 

Q1: 4446
Q2: 84075680
Q3: Final Answer: 11444.80


**Agent with Calculator Tool**  

Q1: 4446
Q2: 83908970
Q3: 11444.80


The results show that using a **dedicated calculator tool** ensures higher accuracy for complex arithmetic operations compared to relying solely on the LLM.
