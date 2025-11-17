# QueryFlow AI — Natural Language to SQL Agent (n8n + PostgreSQL)

![AI SQL Agent Workflow](/Workflow.png)

---

## 🚀 Overview

QueryFlow AI is an intelligent SQL Agent built using **n8n**, **PostgreSQL**, and an **LLM (OpenAI or similar)**.

It converts **plain English questions into SQL queries**, executes them, and returns the results — all automatically.

If the question is unclear, it asks follow-up questions.

If no data exists, it responds with:

**"There is no available data to answer the particular question, but I can help with the following details."**

---

## 🧠 Features

- Natural language → SQL conversion  
- Dynamic schema awareness  
- Valid PostgreSQL query generation  
- Automatic SQL execution via n8n  
- Friendly plain-language responses  
- Follow-up question handling  
- Graceful empty-result messaging  

---

## 🏗️ Tech Stack

- **n8n** (automation & orchestration)
- **PostgreSQL** (database)
- **LLM / OpenAI** (AI logic + reasoning)
- **Webhook / AI Chat** (user interface)
- **JSON tool calling** (SQL execution workflow)

---

## 🔄 Workflow Logic

1. User sends question (Webhook or AI Chat)
2. Agent retrieves schema from database
3. Agent determines:
   - Is it answerable?
   - Is clarification needed?
4. If clear → generates safe SQL (PostgreSQL only)
5. n8n runs the query
6. If results exist → AI summarizes answer
7. If empty → returns fallback message
8. User gets clean answer in plain English

---

## 📜 Schema Retrieval Query

```sql
SELECT 
    table_name,
    column_name,
    data_type
FROM information_schema.columns
WHERE table_schema = 'public'
ORDER BY table_name, ordinal_position;
