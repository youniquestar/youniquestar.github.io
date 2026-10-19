---
layout: post
title: "LASUSTECH FAQ Chatbot"
description: A lightweight Python chatbot using regex-based NLP to answer frequently asked questions about Lagos State University of Science and Technology, with simulated student academic data retrieval.
skills:
  - Python
  - NLP / Regex
  - Chatbot Design
  - Pattern Matching
  - Education Tech

main-image: /cover.jpg
order: 9
---

## Overview

A **command-line chatbot** built in Python that answers frequently asked questions about Lagos State University of Science and Technology (LASUSTECH). Built early in my programming journey, this project demonstrates core NLP concepts using Python's built-in `re` module — no external ML libraries required.

---

## Features

- **Regex Pattern Matching**: Uses Python's `re` module to identify keywords and phrases in user input, allowing flexible querying without exact string matching
- **FAQ Knowledge Base**: Covers admissions, campus facilities, academic programs, tuition, and student services
- **Student Data Simulation**: Simulates fetching student-specific academic information (grades, enrollment status) based on student ID input
- **Graceful Fallbacks**: When the bot cannot match a query, it suggests related topics or asks for clarification

---

## Technical Approach

Rather than using heavyweight NLP libraries or cloud APIs, this chatbot relies on carefully crafted regex patterns to extract intent from natural language:

```python
# Example: detecting an admissions-related query
pattern = r"\b(how|can|do)\b.*\b(apply|admission|enroll)\b"
if re.search(pattern, user_input, re.IGNORECASE):
    return admissions_response()
```

This approach is:
- **Lightweight**: No dependencies beyond Python standard library
- **Fast**: Pattern matching is O(n) on input length
- **Transparent**: Every response can be traced to a specific pattern rule

---

## What I Learned

This was one of my earliest Python projects and taught me:
- String manipulation and regular expressions
- State management in conversational interfaces
- The importance of edge-case handling in user-facing systems
- How to structure code for maintainability (separate pattern definitions from response logic)

---

## Source Code

🔗 [View on GitHub](https://github.com/youniquestar/school_faq_chatbot)
