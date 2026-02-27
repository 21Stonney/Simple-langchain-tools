# Simple-langchain-tools


# 1. Simple Calculator Tool with LangChain Agent (Gemini)
 Overview

This project demonstrates how to build a secure arithmetic calculator tool and integrate it into a LangChain tool-calling agent powered by Google Gemini.

Instead of relying on the LLM to compute math internally, the agent is forced to call a custom calculate tool that safely evaluates expressions using Python’s ast module.

This ensures:

Deterministic results

No hallucinated arithmetic

Secure expression evaluation

Controlled operator usage

🛠 Key Features
 i.) Secure Arithmetic Engine

Uses Python ast parsing

Allows only safe operators:

+ - * / // % **

Blocks unsafe code execution

Limits expression length

Prevents extremely large outputs

 ii.) Custom LangChain Tool

The calculator is wrapped using:

@tool decorator

Returns only numeric output

Handles errors gracefully

  iii.) Tool-Calling Agent (Gemini)

Built using:

ChatGoogleGenerativeAI (gemini-2.0-flash)

create_tool_calling_agent

AgentExecutor

The system prompt enforces strict rules:

Always use the calculate tool for arithmetic

Convert natural language into a valid math expression

Convert ^ into ** for exponentiation

Return only the number when requested

 Experiment: LLM vs Agent with Calculator

To compare performance, I tested:

Plain LLM (no tool)

Agent with calculator tool

Questions Tested

What is 234 * 19?

Compute (12345*6789)+98765

What is 13.7% of 12345 plus 98.76^2? Round to 2 decimals.

 Trial Output

This is the output I obtained during my tests:
— LLM only —
Q1: 4446
Q2: 84075680
Q3: Final Answer: 11444.80

— Agent with calculator —
Q1: 4446
Q2: 83908970
Q3: 11444.80
