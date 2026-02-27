# Simple LangChain Tools

This repository contains **simple LangChain-powered tools** integrated with Google Gemini:

1. **Secure Calculator Tool** – deterministic arithmetic using a safe Python engine.  
2. **Simple Search Tool** – web search + Wikipedia summaries with live citations.
3. **Simple Weather Tool** – mock weather updates with concise, human-friendly reports.  

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

## 3. Simple Weather Tool with LangChain and Gemini

### Overview

The agent **calls a `get_weather` tool** to provide concise, human-friendly weather updates. The mock dataset can easily be replaced with a real API.  

---

### Key Features

- Returns weather for a given city: **condition, temperature, humidity, rain chance**  
- Handles unknown or missing cities gracefully  
- LangChain agent enforces rules:  
  - Always call the weather tool  
  - Ask for clarification if the city is missing  
  - Return concise answers  

---

### Example Usage

```python
ask("What’s the weather in Mumbai?")
ask("Weather update for Bengaluru, please.")
ask("What’s the weather like today?")
```

### Sample Output

**Mumbai**
Humid, partly cloudy, 31 °C, 75% humidity, 40% chance of rain.

**Bengaluru**
Mild, cloudy, 26 °C, 65% humidity, 30% chance of rain.

**Unknown city**
Please specify the city you want the weather for.

---

## Summary

This repository showcases **tool-augmented LLM agents**:

- Calculator: accurate, safe arithmetic  
- Search: factual, cited responses from live sources
- Weather: concise, human-friendly updates

These tools highlight how **LangChain + Gemini** can enforce reliability, avoid hallucinations, and produce professional outputs.
