# 🤖 AI Multi-Agent Research System

A powerful research automation system built with **n8n** and **Google Gemini** where **5 specialized AI agents work together** to research any topic and generate a comprehensive intelligence report in under 2 minutes.

This is not just a chatbot. It is a full **multi-agent pipeline** where each agent has a specific role, passes data to the next agent, and the final analyst synthesizes everything into a professional research report.

---

## 🎯 How It Works

```
You type any research topic
           │
           ▼
┌─────────────────────┐
│  ORCHESTRATOR AGENT │  Plans the research
│  Analyzes intent    │  Identifies key aspects
│  Creates strategy   │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│    SEARCH AGENT     │  Deep facts and data
│  Core facts         │  Key statistics
│  Background context │  Technical details
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│     NEWS AGENT      │  Latest developments
│  Top headlines      │  Breaking news
│  Impact analysis    │  What to watch
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│  COMPETITOR TREND   │  Market intelligence
│  Market landscape   │  Competitive analysis
│  Trends and gaps    │  Winner prediction
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│   ANALYST AGENT     │  Final synthesis
│  Combines all data  │  Creates full report
│  Actionable insights│  Recommendations
└──────────┬──────────┘
           │
           ▼
  COMPREHENSIVE RESEARCH REPORT
  with 9 structured sections
```

---

## 📊 What the Report Contains

Every research report includes these 9 sections:

| Section | What You Get |
|---------|-------------|
| **Executive Summary** | 3-4 sentence overview of critical findings |
| **Deep Research Findings** | Comprehensive facts with specific numbers |
| **Latest News and Developments** | Current events and breaking developments |
| **Competitive Landscape** | Market players, trends and analysis |
| **Top 7 Key Insights** | Non-obvious valuable insights |
| **Risks and Challenges** | Main risks identified |
| **Opportunities and Recommendations** | 3-5 actionable opportunities |
| **Key Statistics at a Glance** | 8-10 specific numbers and stats |
| **What to Watch Next** | 4-5 things to monitor |

---

## 🛠️ Tools and Technologies

| Tool | Purpose |
|------|---------|
| **n8n** | Workflow automation and agent orchestration |
| **Google Gemini API** | AI brain for all 5 agents |
| **Python + Flask** | Optional backend server for API access |
| **chainLlm nodes** | Reliable LLM chains without ReAct overhead |

---

## 🚀 Quick Start — n8n Version

### Prerequisites
- n8n installed (cloud or self-hosted)
- Google Gemini API key (free at [aistudio.google.com](https://aistudio.google.com))

### Get Free Gemini API Key
1. Go to [aistudio.google.com](https://aistudio.google.com)
2. Sign in with Google account
3. Click **Get API Key** then **Create API Key**
4. Copy the key ✅

### Import and Run
1. Clone this repo
   ```bash
   git clone https://github.com/Thrishanth28/AI-Multi-Agent-Research-System.git
   ```

2. Open n8n dashboard

3. Go to **Workflows** then **Import from File**

4. Select `Multi_Agent_Research_V3_FINAL.json`

5. Connect **Google Gemini credentials** to all 5 Gemini nodes:
   - Gemini — Orchestrator
   - Gemini — Search
   - Gemini — News
   - Gemini — Competitor
   - Gemini — Analyst

6. Click **Chat** button at the bottom left

7. Type any research topic and get your report! ✅

---

## 🐍 Quick Start — Python Version

```bash
# Clone repo
git clone https://github.com/Thrishanth28/AI-Multi-Agent-Research-System.git
cd AI-Multi-Agent-Research-System

# Install dependencies
pip install -r requirements.txt

# Set environment variables
export GEMINI_API_KEY=your_gemini_api_key_here
export SERPAPI_KEY=your_serpapi_key_here  # Optional

# Run the server
python main.py

# Test the API
curl -X POST http://localhost:5000/research \
  -H "Content-Type: application/json" \
  -d '{"query": "India startup ecosystem funding trends"}'
```

---

## 🧪 Example Topics to Research

```
→ India startup ecosystem funding trends
→ ChatGPT vs Gemini vs Claude comparison
→ n8n vs Zapier automation market 2025
→ Tesla vs EV market competitors
→ AI prompt engineering career opportunities
→ Remote work tools market analysis
→ India edtech sector growth
→ Generative AI startups to watch
```

---

## 📸 Sample Output

When you type: `India startup ecosystem funding trends`

You get a report like this:

```
# MULTI-AGENT RESEARCH REPORT
Topic: India startup ecosystem funding trends
Agents Used: Orchestrator, Search, News, Competitor Trend, Analyst

## EXECUTIVE SUMMARY
The Indian startup ecosystem experienced significant
funding contraction from 2022 to 2024, with total
funding dropping 80% from its 2021 peak of $42 billion.
However, early 2025 signals show cautious recovery...

## DEEP RESEARCH FINDINGS
CORE FACTS:
- India is the third-largest startup ecosystem globally
- 115,000+ startups registered with DPIIT as of 2024
- 100+ unicorns produced — only US and China have more
- Funding dropped from $42B in 2021 to $7B in 2023

KEY STATISTICS:
- 80% reduction in funding from 2021 peak
- 1,535 deals in 2023 vs 1,540 in 2022
- Seed-stage funding held at 35-40% of total deals...

## LATEST NEWS AND DEVELOPMENTS
TOP HEADLINES:
1. Zepto raised $665M in 2024 — largest India round
2. Quick commerce sector seeing renewed investor interest
3. B2B SaaS companies gaining traction with global clients...

## COMPETITIVE LANDSCAPE
MARKET LANDSCAPE:
Top investors: Peak XV Partners, Accel, Lightspeed,
Blume Ventures, Matrix Partners India...

## TOP 7 KEY INSIGHTS
1. Profitability over growth is the new investor thesis
2. B2B SaaS outperforming B2C consumer plays
3. Tier 2 and 3 city startups gaining traction...
```

---

## 🏗️ Project Structure

```
AI-Multi-Agent-Research-System/
├── Multi_Agent_Research_V3_FINAL.json   ← n8n workflow
├── main.py                              ← Python Flask server
├── requirements.txt                     ← Python dependencies
└── README.md
```

---

## 🔧 Why chainLlm Instead of conversationalAgent

This system uses `chainLlm` (Basic LLM Chain) nodes instead of `conversationalAgent` nodes for a critical reason:

`conversationalAgent` wraps all output in ReAct JSON format:
```json
{
  "action": "Final Answer",
  "action_input": "## MARKET LANDSCAPE..."
}
```

This causes `Cannot assign to read only property 'name'` errors in downstream code nodes.

`chainLlm` returns **pure text output** — clean, reliable and immediately usable by the next node in the pipeline.

---

## 📡 Python API Endpoints

If running the Python server:

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/research` | POST | Run full 5-agent research |
| `/health` | GET | Check server status |
| `/agents` | GET | List all 5 agents and their roles |

---

## 💡 Real World Use Cases

- 🏢 **Startups** — Research competitors and market opportunities
- 📊 **Investors** — Quick due diligence on sectors or companies
- 🎓 **Students** — Research any academic topic deeply
- 💼 **Consultants** — Generate client-ready research reports
- 📰 **Journalists** — Background research on any story
- 🚀 **Product Managers** — Market analysis before building

---

## 🔐 Security Note

Never commit real API keys to GitHub.
All credentials are configured inside n8n credential manager.
Use environment variables for the Python version.

---

## 🙋‍♂️ Built By

**S. Thrishanth Reddy** — AI Automation Developer

2nd year B.Tech CSE student at SRM University Haryana.
Specializes in building AI automation agents using n8n and Google Gemini.
Built 13+ real-world AI automation projects in 3 weeks.

Skills: n8n · Google Gemini API · Prompt Engineering · Python · JavaScript · HTML · CSS · SQL

📎 [LinkedIn](https://linkedin.com/in/thrishanth-reddy) | 🔗 [GitHub](https://github.com/Thrishanth28)

---

## 📄 License

MIT License — free to use, modify and share!
