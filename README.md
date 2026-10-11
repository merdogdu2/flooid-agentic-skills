# 🧠 Flooid Demo: Embedding GCP Best Practices ("Skills") into Agentic Workflows

**Track 4: Agentic Context Engineering**

This directory demonstrates how Flooid can bridge its "Flow Next" factory, Cursor, and Google Antigravity by providing codified GCP standards directly to autonomous AI agents.

## 🎯 The Core Concept
Generic AI coding assistants write *generic* code. By embedding a `SKILL.md` file in your repository, you provide **Context Engineering**. The AI agent reads these rules before it starts typing, ensuring that the generated code is instantly compliant with Flooid's proprietary standards.

## 📦 What's Included
* **`SKILL.md`**: The actual configuration file that governs the AI's behavior. It explicitly defines:
  1. **Strict Tenant Isolation:** Rules for Workload Identity and RBAC.
  2. **Security:** Mandatory Wiz labels and private endpoint requirements.
  3. **Tokenomics:** Guidelines for routing tasks between Gemini Flash (speed/cost) and Gemini Pro (complex reasoning).
  4. **Sandpit Rules:** Automated TTLs and cost-effective sizing for ephemeral environments.

## 🚀 How to Demo This Tomorrow

1. **Show the `SKILL.md` file**: Open the file in your IDE and walk through the rules. Explain that this acts as the "Brain" for Cursor or Antigravity.
2. **The "Wow" Statement**: *"If I don't use this skill and ask an AI to create a database, I get a generic database. But if I load this skill and say 'Create a sandpit database for client A', the AI automatically adds the Wiz security tags, disables public IPs, sizes it to a cost-effective tier, and sets a 12-hour TTL. It shifts security and compliance entirely to the left—before the code is even written."*
3. **Connect to Tokenomics**: Highlight Section 3. Explain how this skill repo teaches the agent *when* to spend tokens efficiently across the Gemini models.
