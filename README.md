# N8N PubMed Agent

This project demonstrates how to automate **retrieving PubMed abstracts**, summarizing them using **OpenAI GPT**, and storing results into **Google Sheets** — all orchestrated via **n8n** (workflow automation tool).

**Repository:** https://github.com/aliminagar/n8n-pubmed-agent

It showcases:

- API integration (PubMed E-utilities + OpenAI API)
- Containerized setup using Docker Compose
- Automated workflow with n8n nodes
- Clean final output inside Google Sheets

---

## 🚀 Features

- Fetch PubMed abstracts automatically.
- Summarize abstracts into **3 factual bullet points** with GPT-4o-mini.
- Append new rows into Google Sheets.
- Update existing rows with AI-generated summaries.
- Fully containerized with **Docker Compose**.

---

## 📂 Project Structure

N8N-PUBMED-AGENT/
│── .env # Stores API keys & secrets (not included in repo)
│── .gitignore # Ensures sensitive files like .env are ignored
│── docker-compose.yml # Container setup for n8n
│── README.md # Project documentation
│
├── screenshots/ # Workflow screenshots
│ ├── docker-compose-up.jpg
│ ├── n8n_Workflow_Overview.jpg
│ ├── message_node.jpg
│ ├── Final_Output_in_Google_Sheets.jpg

---

## ⚙️ Setup & Installation

1. **Clone the repo**

   ```bash
   git clone https://github.com/aliminagar/n8n-pubmed-agent.git
   cd n8n-pubmed-agent

   Create .env file
   Store your API keys securely:
   ```

env

OPENAI_API_KEY=your_openai_key_here
GOOGLE_SHEETS_CREDENTIALS=your_google_sheets_json_here
Run with Docker Compose

docker compose up -d
Access n8n at http://localhost:5678.

🔄 How It Works (Workflow Logic)
PubMed API Call

Uses HTTP Request + efetch to fetch PubMed abstracts in XML.

Converts XML → JSON for easier processing.

Data Processing

Code node cleans up the output.

Rows are appended into Google Sheets if they are new.

AI Summarization

Message a Model node (OpenAI GPT) summarizes each abstract.

Outputs exactly 3 factual bullet points per abstract.

Update in Google Sheets

The summaries are mapped to the correct row (using PMID as the identifier).

Final sheet now has PMID, Title, Journal, Year, Abstract, and Summary.

🛠️ Workflow Overview

1. Workflow Diagram

2. Example Node Configuration

3. Running n8n with Docker Compose

4. Final Output in Google Sheets

📊 Final Result
The final Google Sheet includes:

PMID

Title

Journal

Year

Abstract

AI-generated summary (3 bullet points)

📌 Notes
No API keys or secrets are committed to the repo (.env is ignored).

Screenshots are included to demonstrate the workflow without exposing private configs.

This project is for educational/demo purposes — extend it for production workflows.

📜 License
MIT License — free to use and adapt.
