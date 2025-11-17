QueryFlow AI — Natural Language to SQL Agent (n8n + PostgreSQL)

🚀 Overview

QueryFlow AI is an intelligent SQL Agent built using n8n, PostgreSQL, and an AI model (OpenAI / LLM).
It allows users to ask plain English questions, which are then:

Understood by AI

Converted into PostgreSQL SQL queries

Executed in real-time on your database

Answered back in human language

If the question is unclear → it asks follow-up questions.
If the data doesn’t exist → it clearly responds:

"There is no available data to answer the particular question, but I can help with the following details."

🧠 What It Can Do

✔️ Understand natural language questions
✔️ Read your database schema dynamically
✔️ Create safe Postgres SQL queries
✔️ Execute them live using n8n
✔️ Return answers in readable format
✔️ Ask clarifying questions when needed
✔️ Handle "no-data" cases gracefully

🏗️ Tech Stack

n8n (Orchestration)

PostgreSQL (Database)

OpenAI / LLM (AI reasoning)

Webhook / AI Chat (User input)

JSON-based tool calling (SQL execution workflow)

🔄 Workflow Logic

User sends a natural language question

Agent retrieves database schema

Agent decides:

Is the question answerable?

Is follow-up needed?

If clear → generates valid PostgreSQL SQL

n8n executes query

If results exist → AI summarizes answer

If no data → Responds with fallback message

Returns a friendly, clear response

🗄️ Schema Retrieval SQL
SELECT 
    table_name,
    column_name,
    data_type
FROM information_schema.columns
WHERE table_schema = 'public'
ORDER BY table_name, ordinal_position;

🤖 System Message (Core Instructions for AI)

You are an AI SQL Agent connected to a PostgreSQL database.
Only use tables and columns from the schema.
If unclear — ask follow-up questions.
Use PostgreSQL syntax only (LIMIT instead of TOP).
Never write INSERT / UPDATE / DELETE / DROP.
If no data exists, say:

"There is no available data to answer the particular question, but I can help with the following details."

📸 Workflow Preview

Replace this:

<PLACE_WORKFLOW_IMAGE_LINK_HERE>


With your actual image link, or embed like:

![QueryFlow AI Workflow](https://your-image-host.com/workflow.png)

🧪 Example Queries

"Show me total sales in India for 2023"

"Top 3 customers in USA ordered by revenue"

"How many users signed up last month?"

🔧 How to Run / Use

Import workflow into n8n

Connect PostgreSQL

Connect OpenAI (or LM Studio / Ollama)

Activate workflow

Share your webhook or AI Chat URL

Ask questions → get answers!

👤 Author

Haris Jirati
