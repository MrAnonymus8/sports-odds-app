# ⚽ AI Sports Match & Odds Analyzer (Streamlit Dashboard)

An experimental, single-page analytics platform that bridges real-time sports betting data with Large Language Models (LLMs). It automates bookmaker margin calculation, detects synthetic surebets (arbs), and requests multi-model AI insights on selected betting markets.

## 🚀 Key Features

- **Dynamic League Catalog:** Fetches global football leagues and up-to-date match schedules directly from the data provider.
- **Odds Matrix & Cross-Bookmaker Comparison:** Pivots raw odds data into an interactive, readable outcome-by-bookmaker table.
- **Mathematical Margin Calculator:** Automatically computes individual bookmaker commissions and determines "Synthetic Line Margin" to highlight arbitrage opportunities (negative margin).
- **Persistent Storage:** Local `credentials.json` layer saves your API endpoints and access tokens so you don't have to re-enter them on every launch.
- **Multi-Model AI Verdicts:** Compiles granular match context (team form, missing players, odds distribution) and runs a parallel evaluation via custom LLM configurations (e.g., GPT, Kimi, Grok).

## 🛠️ Architecture & Connectivity Note

This project is built with **modular API adapters**. 

By default, the setup is pre-configured to utilize **SStats.net API** endpoints. This is highly beneficial for developers operating under strict regional network constraints or firewalls (such as in the RU/CIS region), as it completely circumvents Cloudflare geo-blocking and anti-bot filters without requiring complex proxy rotation packages. 

*Architecture Flexibility:* The core data pipeline—managed by the `api()`, `odds_tables()`, and `build_bookmaker_matrix()` functions—is completely decoupled from the UI. You can seamlessly swap the data layer with any standard REST/WebSocket global provider (like *The Odds API*, *OddsPapi*, or first-party sportsbook feeds) by mapping the incoming JSON arrays to the unified Pandas DataFrame structure.

## 📦 Installation & Setup

1. **Clone the repository:**
%%LMDX_PARSER_PROTECT%%   ```bash
   git clone https://github.com/YOUR_USERNAME/your-repo-name.git
   cd your-repo-name
%%LMDX_PARSER_PROTECT%%   ```

2. **Install dependencies:**
%%LMDX_PARSER_PROTECT%%   ```bash
   pip install pandas streamlit openai
%%LMDX_PARSER_PROTECT%%   ```

3. **Run the application locally:**
%%LMDX_PARSER_PROTECT%%   ```bash
   streamlit run match_analysis_fixed.py
%%LMDX_PARSER_PROTECT%%   ```

## ⚙️ Configuration

Open the sidebar panel in your browser to configure your node connections:
- **Sports API Key:** Enter your data provider token (leave blank for default rate-limited anonymous access).
- **AI Provider:** Specify any OpenAI-compatible base URL (e.g., OpenRouter, DeepSeek, Aitunnel) and your secret bearer token.
- Click **"Запомнить ключи на сервере"** to securely cache your configuration to a local `credentials.json` file.

## 🤝 Feedback & Contributions

This dashboard is a personal playground designed for data-driven sports modeling experiments. Feel free to open an **Issue** or start a **Discussion** if you want to suggest:
- Advanced staking calculators (Kelly Criterion, Dutching).
- Custom UI theme wrappers or performance caching optimizations.
- Integration models for additional sports disciplines (Basketball, Esports).
