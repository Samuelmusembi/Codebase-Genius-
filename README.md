An agentic multi-agent system built in Jac that automatically generates clean, structured Markdown documentation for GitHub repositories.

Agents:

🗺️ RepoMapper — Maps and summarizes repository structure
🧠 CodeAnalyzer — Parses files and builds a Code Call Graph (CCG)
✨ DocGenie — Generates Markdown documentation with Mermaid diagrams
⚙️ Setup Instructions
Clone this repository
git clone https://github.com/JayMwakideu/agentic-codebase-genius.git
cd agentic-codebase-genius
Create and activate a virtual environment

bash Copy code python3 -m venv venv source venv/bin/activate # For Linux/Mac

OR
venv\Scripts\activate # For Windows Install dependencies

bash Copy code pip install -r requirements.txt Configure environment variables

bash Copy code cp .env.example .env

Then edit .env and set:
OPENAI_API_KEY=your_key Run the Jac backend

bash Copy code cd backend jac serve main.jac Server will start on http://localhost:8000

🧩 API Usage Endpoint: POST http://localhost:8000/jac/run/walker/gen_docs

Request Body (JSON):

json Copy code { "url": "https://github.com/psf/requests.git" } Response:

json Copy code { "success": true, "output_path": "outputs/requests-docs.md" } Example with curl bash Copy code curl -X POST http://localhost:8000/jac/run/walker/gen_docs
-H "Content-Type: application/json"
-d '{"url": "https://github.com/psf/requests.git"}' �� Sample Output When run on the requests repository: Documentation is generated at: ./outputs/requests-docs.md

Includes:

Repository Overview

Directory Tree

Code Analysis

Mermaid Diagrams

🧠 Extending Codebase Genius

Add better parsing Install Tree-sitter for richer AST parsing:
bash Copy code pip install tree-sitter tree-sitter-python 2. Add support for more languages Edit utils.py to handle additional programming languages.

Build a frontend Create a frontend/ folder with a Streamlit app that calls the Jac API for visual interaction.
🧑‍💻 Agent Overview Agent Role Description CodeGenius (Supervisor) 🧭 Orchestrates workflow between agents RepoMapper 🗺️ Clones repo, maps structure, summarizes README CodeAnalyzer 🧠 Parses files and builds Code Call Graph DocGenie ✍️ Assembles final Markdown with diagrams

🧩 External Dependencies Tool Purpose OpenAI Text summarization Git Repository cloning Python AST Parsing source code

🏁 License MIT © samuel Musembi
