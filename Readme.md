
---

# 🧠 ScRag_powered-Text-to-SQL

An end-to-end **Text-to-SQL system** that allows users to query a relational database using **natural language**, built using a **Retrieval-Augmented Generation (RAG)** architecture and evaluated with **RAGAS**.

---

## 📌 Overview

Databases store critical business data, but accessing this data usually requires SQL expertise.
This project bridges that gap by enabling **natural language querying of a SQL database**, automatically generating and executing SQL queries, and returning **business-friendly answers**.

The system is designed to be **schema-aware**, **hallucination-resistant**, and **evaluation-ready**, making it suitable for real-world GenAI applications.

---

## 🏗️ Architecture

```

User Question
     ↓
Schema Retrieval (RAG)
     ↓
LLM-Generated SQL Query
     ↓
SQL Execution on Database
     ↓
Post-Query RAG
     ↓
Natural Language Answer

```

### Key Design Choices

* **Pre-SQL RAG** ensures correct table and column usage
* **Database execution** guarantees factual correctness
* **Post-SQL RAG** converts raw results into human-readable insights
* **RAGAS** is used for offline evaluation of answer quality

---

## ⚙️ Tech Stack

* **Python**
* **LangChain (LCEL)**
* **Google Gemini (LLM)**
* **MySQL**
* **SQLAlchemy**
* **RAGAS (Evaluation Framework)**
* **python-dotenv**

---

## ✨ Features

* 🔍 Schema-aware SQL generation using RAG
* 🔐 Secure handling of credentials using environment variables
* 🧠 Accurate JOINs, filters, and aggregations
* 📊 Conversion of raw SQL results into business-friendly answers
* 🧪 Offline evaluation using RAGAS metrics
* 🛡️ Safe and defensive handling of SQL execution outputs

---

## 🧠 Example

**Input (Natural Language):**

```
What is the total Line Total for Geiss Company?
```

**Generated SQL:**

```sql
SELECT SUM(T2.`Line Total`)
FROM customers AS T1
JOIN sales_order AS T2
ON T1.`Customer Index` = T2.`Customer Name Index`
WHERE T1.`Customer Names` = 'Geiss Company';
```

**Final Answer:**

```
The total Line Total for Geiss Company is 5,516,847.00.
```

---

## 🔎 Evaluation with RAGAS

The project integrates **RAGAS** to evaluate the quality of the RAG pipeline using the following metrics:

* **Faithfulness** – Is the answer grounded in retrieved data?
* **Answer Relevancy** – Does the answer address the user’s question?
* **Context Precision** – Is the retrieved context relevant and sufficient?

---

## 🚀 How to Run

1. Clone the repository
2. Create and activate a virtual environment
3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```
4. Create a `.env` file using `sample.env` as reference
5. Run the notebook or pipeline script

---


## 🔐 Environment Variables

Create a `.env` file in the project root with the following variables:

```env
GOOGLE_API_KEY=your_gemini_api_key_here
DB_HOST=localhost
DB_PORT=3306
DB_USER=your_database_user
DB_PASSWORD=your_database_password
DB_NAME=text_to_sql
```

---

## 📊 RAGAS Evaluation Notes

This project integrates **RAGAS** as an **offline evaluation layer** to assess the quality of the Retrieval-Augmented Generation pipeline.

RAGAS is used to measure:

* Faithfulness of generated answers to database results.
* Relevance of answers to user questions.
* Precision of retrieved context used for generation.

---

## 📁 Project Scope & Design Decision

* ✅ Core backend pipeline fully implemented
* ✅ End-to-end Text-to-SQL → Database → Answer flow completed
* ✅ Evaluation layer (RAGAS) integrated

---

## 📜 License

This project is released under the **MIT License**.

---

🙌 Acknowledgements

* LangChain Documentation
  (https://docs.langchain.com/)

* Google Gemini API
  (https://ai.google.dev/gemini-api)

* RAGAS Evaluation Framework
  (https://github.com/explodinggradients/ragas)

---



