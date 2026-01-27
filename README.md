**1. Title & one‑liner**

Title:
Marketing Analytics Copilot – NL → SQL → Insights (Gemini + SQLite)

One‑liner:
“A multi‑agent analytics chatbot that turns natural‑language questions about marketing campaigns into SQL queries, runs them on SQLite, and returns business‑ready insights and recommendations.”

**2. Problem & motivation**

Example text:

Marketers are surrounded by dashboards but still struggle to get direct answers like “Which channels are wasting budget?” or “What should I do next quarter?”. This project shows how a generative‑AI “copilot” can sit on top of raw campaign data, understand business questions, query the database, and return explainable insights instead of raw tables.

**3. What this project does**

Bullet points work well:

Accepts natural‑language questions about campaign performance (ROAS, CTR, conversion, unsubscribe, etc.).

Uses embeddings + vector search to select the best SQL examples for the question.

Generates SQL queries for a SQLite database containing campaign‑level metrics.

Executes the SQL and returns a clean result table.

Applies a second AI agent to interpret the result in business context and produce recommendations.

Includes a test suite with ambiguous and “tricky” questions to show where NL→SQL can fail and how the system behaves.

**4. Architecture overview**

You can add a small diagram image later; in text:

Agent 1 – Retrieval: Embed predefined question–SQL pairs, run vector search to find the top‑k similar examples for a new question.

Agent 2 – SQL generation: Uses schema + retrieved examples to generate a safe SELECT query over the campaigns table.

Agent 3 – Executor: Executes SQL against a local SQLite database and returns a DataFrame.

**5. Future work**

Short bullets:

Add multi‑table joins (e.g., customers, orders).

Add a lightweight web UI (Streamlit / Next.js) on top of the backend.

Improve robustness using SQL validation and automatic retry strategies.

Add per‑user business context and campaign goals for more personalized recommendations.
Agent 4 – Analyst: Reads the result plus business context and produces human‑readable insights and recommendations.

Mention that you’re using one model for embeddings and another for generation, and that the system is read‑only (no INSERT/UPDATE/DELETE).
