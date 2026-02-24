# 🛡️ OpsGuardian: The Statistical SRE Agent

> **Built for the Elastic AI Agent Hackathon** 🏆

**OpsGuardian** is an autonomous Site Reliability Engineer (SRE) agent built on the **Elastic Stack**. It bridges the gap between **Deterministic Metrics** and **Unstructured Knowledge**.

Unlike generic chatbots that hallucinate numbers, OpsGuardian uses **ES|QL** for mathematical rigor and relevance-based retrieval to reduce Mean Time To Resolution (MTTR).

![Demo Screenshot](assets/demo_screenshot.png)
*(Place a screenshot of your Kibana Console conversation here)*

## 🚀 The Problem
SREs suffer from "Dashboard Fatigue". When an incident occurs, they have to:
1.  Check Dashboards (Metrics)
2.  Search Logs (Patterns)
3.  Read Wikis (Knowledge)
OpsGuardian unifies this into a single cognitive loop.

## 💡 The Solution: "The Triad of Truth"

OpsGuardian is designed with a strict reasoning framework:

1.  **📊 Mathematical Rigor (The Calculator)**
    *   **Tech**: `ES|QL`, `EVAL`, `STATS`
    *   **Function**: Calculates real-time **Error Rates** directly in the database. It doesn't guess; it proves.
    *   *Tool*: `tool-calc-reliability`

2.  **🔍 Pattern Recognition (The Historian)**
    *   **Tech**: `ES|QL`, `match()`
    *   **Function**: Instantly correlates current incidents with historical log patterns to find "Patient Zero".
    *   *Tool*: `tool-find-patterns`

3.  **📘 Automated Remediation (The Fixer)**
    *   **Tech**: `ES|QL` (Relevance Search)
    *   **Function**: Retrieves the exact Standard Operating Procedure (SOP) to fix the issue.
    *   *Tool*: `tool-search-sops-semantic`

## 🛠️ How to Reproduce

You can deploy OpsGuardian in your own Elastic Cloud Serverless environment in 5 minutes.

### Prerequisites
*   Elastic Cloud Serverless Project
*   Kibana Sample Data: **"Sample Web Logs"** (Load this from the Kibana Home page)

### Step 1: Import Knowledge Base
Copy the content from `data/knowledge_base_bulk.json` and run it in **Kibana Dev Tools**.

### Step 2: Deploy Tools
Open `src/tools/` and copy the JSON content of each tool. Run them as `POST` requests to the Agent Builder API in Kibana Dev Tools.

Example:
```json
POST kbn://api/agent_builder/tools
// ... paste content of tool_calc_reliability.json ...
```

### Step 3: Deploy Agent
Copy the content from `src/agent.json` and run it:

```json
POST kbn://api/agent_builder/agents
// ... paste content of agent.json ...
```

### Step 4: Chat!
Go to the Agent Builder Playground or use the Converse API:
```json
POST kbn://api/agent_builder/converse
{
  "agent_id": "ops-guardian-v3",
  "input": "I see high error rates. Investigate and tell me how to fix."
}
```

## 🔮 Future Roadmap
*   **Upgrade to ELSER**: Migrate the knowledge retrieval tool to use `text_expansion` for true vector search (currently using ES|QL relevance matching for broader compatibility).
*   **MCP Integration**: Expose OpsGuardian as a Model Context Protocol server for IDE integration.

## 📄 License
MIT
