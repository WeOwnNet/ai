## Overview

This document serves as a reference for all AI agents and ♾️ WeOwnNet 🌐 Core TEAM members to understand what AnythingLLM **can** and **cannot** do.

**Instance URL:** [ai.weown.agency](https://ai.weown.agency)
**Deployment:** Self-hosted (DigitalOcean droplet - ATL1 data center)
**Version:** AnythingLLM (Docker deployment)

---

## ✅ What AnythingLLM CAN Do

### 🗂️ Document & Knowledge Management
- Upload and embed documents (PDF, TXT, DOCX, MD, etc.)
- RAG (Retrieval Augmented Generation) - query against embedded docs
- Store information in vector database for retrieval
- Multi-modal support (images, audio, video via transcription)
- Web scraping and URL embedding

### 👥 User & Workspace Management
- Multi-user support with role-based access
- User roles: **Admin**, **Manager**, **Default**
- Workspace-level permissions (add/remove users per workspace)
- Separate chat threads per user

### 🤖 AI Agent Capabilities
- Web browsing & search
- Web scraping
- RAG memory (search & store)
- Document summarization
- Chart generation
- File saving
- MCP (Model Context Protocol) tool integration
- Custom agent skills

### 🔌 Integrations & API
- REST API for external access
- MCP server connections (WordPress, FluentCommunity, etc.)
- Compatible with multiple LLM providers (OpenAI, Anthropic, local models, etc.)
- Vector database options (LanceDB, Pinecone, Chroma, etc.)

### 💬 Chat Features
- Persistent chat history per user/workspace
- Thread management
- Slash commands
- @agent mentions for tool invocation
- System prompts per workspace

---

## ❌ What AnythingLLM CANNOT Do

### 🚫 Cross-User Collaboration

| Feature | Status | Workaround |
|---------|--------|------------|
| Approval workflows | ❌ | Use n8n + external notifications |
| Pending task queues | ❌ | Use FluentCommunity or PM tools |
| Cross-user notifications | ❌ | Use email/Discord/Slack via n8n |
| Shared drafts between users | ❌ | Store in wiki.3win.social |
| Real-time collaboration | ❌ | Users work in separate sessions |

### 🚫 Administrative Limitations

| Feature | Status | Notes |
|---------|--------|-------|
| Agent managing user permissions | ❌ | Must be done via Admin UI |
| Agent creating workspaces | ❌ | Must be done via Admin UI |
| Agent inviting users | ❌ | Must be done via Admin UI |

### 🚫 Memory Limitations

| Feature | Status | Notes |
|---------|--------|-------|
| Memory shared across workspaces | ❌ | Each workspace is isolated |
| Memory visible to other users | ❌ | No user-level notifications |
| Persistent tasks/reminders | ❌ | No scheduled task system |

---

## 🔐 User Roles & Permissions

| Role | Capabilities |
|------|--------------|
| **Admin** | Full system access, user management, all workspaces |
| **Manager** | Can manage assigned workspaces, limited admin |
| **Default** | Access only to assigned workspaces |

---

## 🔐 BEST-PRACTICES.md Authorization

Only these AnythingLLM users can approve/modify BEST-PRACTICES.md:

| Username | Core TEAM Member |
|----------|------------------|
| `yonks` | Jason Younker |
| `mrsyonks` | Tyler Younker |
| `yonksteam` | YonksTEAM (org account) |

---

## 🏗️ Default Workspaces (v2.4.2)

| # | Workspace | URL | Purpose |
|---|-----------|-----|---------|
| ⓪ | 🌐︱home | [/workspace/home](https://ai.weown.agency/workspace/home) | Default landing, general assistance |
| ① | 🗂️︱content | [/workspace/content](https://ai.weown.agency/workspace/content) | Content management & creation |
| ② | 📧︱email | [/workspace/email](https://ai.weown.agency/workspace/email) | Email campaigns & FluentCRM |
| ③ | 📆︱events | [/workspace/events](https://ai.weown.agency/workspace/events) | Event planning & scheduling |
| ④ | 🧩︱flows | [/workspace/flows](https://ai.weown.agency/workspace/flows) | 🧩︱flows documentation & automation |
| ⑤ | 👥︱people | [/workspace/people](https://ai.weown.agency/workspace/people) | Team, contacts & CRM |
| ⑥ | 📍︱places | [/workspace/places](https://ai.weown.agency/workspace/places) | Locations & venues |
| ⑦ | 🛠️︱tools | [/workspace/tools](https://ai.weown.agency/workspace/tools) | Tools & integrations |

---

## 🏛️ Architecture

```
┌─────────────────────────────────────────────────────┐
│         ai.weown.agency (AnythingLLM)               │
├─────────────────────────────────────────────────────┤
│  Workspaces (isolated)                              │
│  ├── ⓪︱🌐︱home      ← DEFAULT LANDING             │
│  ├── ①︱🗂️︱content                                 │
│  ├── ②︱📧︱email                                   │
│  ├── ③︱📆︱events                                  │
│  ├── ④︱🧩︱flows                                   │
│  ├── ⑤︱👥︱people                                  │
│  ├── ⑥︱📍︱places                                  │
│  └── ⑦︱🛠️︱tools                                   │
├─────────────────────────────────────────────────────┤
│  Each workspace has:                                │
│  • Own embedded documents                           │
│  • Own RAG memory                                   │
│  • Own chat history (per user)                      │
│  • Shared system prompt                             │
│  • Shared agent configuration                       │
└─────────────────────────────────────────────────────┘
```

---

## 🧩 MCP Tools Connected

| Tool | Purpose |
|------|---------|
| `fmcp-weown` | WordPress & FluentCommunity management |
| `web-browsing` | Search engine queries |
| `web-scraping` | Scrape webpage content |
| `rag-memory` | Store/retrieve from vector database |
| `document-summarizer` | Summarize uploaded documents |
| `create-chart` | Generate chart data |
| `save-file-to-browser` | Download files to user |

---

## 🔄 Workarounds for Missing Features

### Approval Workflows
```
AnythingLLM → n8n webhook → Email/Discord notification → Manual approval → n8n callback
```

### Cross-User Handoffs
```
User A drafts in AnythingLLM → Posts to FluentCommunity → User B reviews → Updates AnythingLLM
```

### Scheduled Tasks
```
n8n scheduled trigger → AnythingLLM API call → Action executed
```

---

## 📚 Official Resources

| Resource | URL |
|----------|-----|
| Documentation | [docs.anythingllm.com](https://docs.anythingllm.com) |
| GitHub | [github.com/Mintplex-Labs/anything-llm](https://github.com/Mintplex-Labs/anything-llm) |
| Discord | [discord.gg/anythingllm](https://discord.gg/anythingllm) |
| API Reference | [docs.anythingllm.com/api](https://docs.anythingllm.com/api) |

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 2.4.2 | 07Jan2026 | Added ⓪︱🌐︱home; 8 workspaces; instance URL; purposes |
| 2.4.1 | 07Jan2026 | Initial creation; docs scrape; limitations documented |

---

## Agent Instructions

When operating in any ♾️ WeOwnNet 🌐 workspace:

1. **Check this document** before promising cross-user features
2. **Do not suggest** approval workflows, notifications, or shared queues natively
3. **Recommend n8n integration** for workflow automation needs
4. **Be transparent** about platform limitations
5. **Suggest workarounds** using the connected tool stack
6. **Reference workspace URLs** when directing users

---

```
♾️ WeOwnNet 🌐 | Know Your Tools | Document → Iterate → Automate
```
