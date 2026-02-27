# Simple LangChain Tools

This repository contains **simple LangChain-powered tools** integrated with Google Gemini:

1. **Secure Calculator Tool** – deterministic arithmetic using a safe Python engine.  
2. **Simple Search Tool** – web search + Wikipedia summaries with live citations.  

These tools demonstrate how **tool-augmented LLM agents** can produce accurate and reliable outputs.

---

## 1. Simple Calculator Tool

### Overview

The calculator ensures that all arithmetic is evaluated **safely and deterministically** using Python’s `ast` module. The agent **cannot compute math internally** and must call the tool for any calculations.

### Key Features

- Safe arithmetic with `+ - * / // % **`  
- Limits expression length and prevents huge outputs  
- Wrapped as a LangChain tool with `@tool`  
- Tool-calling agent powered by `ChatGoogleGenerativeAI (gemini-2.0-flash)`  
- Converts `^` to `**` and returns numeric results only  

### Sample Questions and Outputs

| Question | LLM Only | Agent with Calculator |
|----------|-----------|----------------------|
| 234 * 19 | 4446 | 4446 |
| (12345*6789)+98765 | 84075680 | 83908970 |
| 13.7% of 12345 + 98.76^2 (round 2 decimals) | 11444.80 | 11444.80 |

---

## 2. Simple Search Tool

### Overview

This agent uses **web search (DuckDuckGo)** and **Wikipedia summaries** to answer factual or recent questions. The LLM **calls tools for any facts, numbers, dates, or latest info**, ensuring accuracy and citations.

### Key Features

- `web_search`: fetches up to 5 results with URLs and snippets  
- `wiki_summary`: short Wikipedia summaries with page URL  
- Agent enforces using tools for citations and avoids hallucinations  

### Example Usage and Output

**1) FIFA World Cup 2022 Winner**

- `web_search`: fetches up to 5 results with URLs and snippets  
- `wiki_summary`: short Wikipedia summaries with page URL  
- Agent enforces using tools for citations and avoids hallucinations  

### Example Usage and Output

**1) FIFA World Cup 2022 Winner**

Argentina won the FIFA Worls Cup 2022[https://en.wikipedia.org/wiki/2022_FIFA_World_Cup_Final]

**2) Retrieval-Augmented Generation (Wikipedia Summary)**

- RAG combines language models with information retrieval for accurate responses.
- Allows models to access external sources for contextually relevant answers.
- Used for various NLP tasks to improve reliability of generated text.

Source:
Title: Retrieval-augmented generation
URL: https://en.wikipedia.org/wiki/Retrieval-augmented_generation

**3) Recent Headlines about Generative AI**

- AI News | Reuters [https://www.reuters.com/technology/artificial-intelligence/]
- Generative AI - HBR [https://hbr.org/topic/subject/generative-ai]
- Artificial intelligence | MIT News [https://news.mit.edu/topic/artificial-intelligence2]


---

## Summary

This repository showcases **tool-augmented LLM agents**:

- Calculator: accurate, safe arithmetic  
- Search: factual, cited responses from live sources  

These tools highlight how **LangChain + Gemini** can enforce reliability, avoid hallucinations, and produce professional outputs.
