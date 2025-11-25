# Agentic AI Portfolio

A collection of production-ready AI agent projects demonstrating expertise across multiple agentic frameworks, patterns, and architectures.

## 🎯 About This Portfolio

This portfolio showcases **senior-level AI engineering skills** through hands-on projects that solve real problems using different agentic AI frameworks. Each project demonstrates distinct patterns and capabilities:

| Project | Framework(s) | Pattern | Status |
|---------|--------------|---------|--------|
| [Career Copilot](#-career-copilot) | Semantic Kernel | Autonomous Tool Orchestration | ✅ Complete |
| [SQL Query Agent](#-sql-query-agent) | LangGraph | Self-Correction Loops | ✅ Complete |
| [Code Review Crew](#-code-review-crew) | AutoGen + LangGraph | Multi-Agent + Iterative Fixing | ✅ Complete |

---

## 🤖 Career Copilot

**Framework:** Microsoft Semantic Kernel  
**Pattern:** Autonomous Tool Orchestration + Conversation Memory

An intelligent agentic AI system that autonomously helps users find jobs, match resumes to opportunities, and manage job searches through natural language conversations.

### Key Features
- 🧠 **Autonomous Decision Making** - AI selects tools without hardcoded commands
- 💬 **Multi-Turn Context** - Maintains conversation state across interactions
- 🔄 **Self-Improvement** - AI critiques and refines its own outputs
- 🛡️ **Safe Code Generation** - Natural language to SQL with injection prevention
- 🔌 **Plugin Architecture** - Modular, extensible design

### Architecture
```
┌─────────────────────────────────────────────────────────┐
│              Azure OpenAI (GPT-4)                       │
│              Semantic Kernel Agent                      │
└───────────────────────┬─────────────────────────────────┘
                        │
        ├─> JobPlugin (SerpAPI integration)
        ├─> ResumeMatchingPlugin (AI scoring)
        ├─> QueryDatabasePlugin (NL to SQL)
        ├─> ResumeTailoringPlugin (Content optimization)
        ├─> SelfImprovingMatchPlugin (Iterative refinement)
        └─> ResumePreprocessorPlugin (Text extraction)
```

### Tech Stack
`Semantic Kernel` `Azure OpenAI` `GPT-4` `Streamlit` `SQLite` `SerpAPI`

### Links
- 📁 [View Project](https://github.com/bryan-lolordo/career-copilot)
- 📖 [Architecture Docs](https://github.com/bryan-lolordo/career-copilot/blob/master/ARCHITECTURE.md)

---

## 🔍 SQL Query Agent

**Framework:** LangGraph  
**Pattern:** Self-Correcting Loops + Iterative Refinement

A self-correcting SQL query agent that converts natural language to SQL, executes queries, and automatically fixes errors through iterative refinement loops.

### Key Features
- 🔄 **Self-Correction** - Automatically fixes errors and retries
- 🧠 **Learns from Mistakes** - Each retry includes context from previous failures
- 🛡️ **Safe Execution** - Read-only queries with SQL injection prevention
- 📊 **Interactive UI** - Streamlit interface with real-time feedback
- 🎯 **Quality-Based Routing** - Smart decisions on when to retry vs. clarify

### Self-Correction in Action

```
User: "Show me employee salary percentiles by department"

❌ Attempt 1:
   SELECT * FROM employees...
   Error: no such table: employees

🧠 Analyzing error...

✅ Attempt 2:
   SELECT * FROM customers...
   Success! (mapped to closest matching table)
```

### Architecture
```
┌─────────────────────────────────────────────────────────────┐
│                    LangGraph State Machine                   │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  START → Parse Intent → Generate SQL → Validate SQL         │
│                                            ↓                │
│                                      Execute SQL            │
│                                            ↓                │
│                         Success? ─┬─ Yes → Format → END     │
│                                   ↓                         │
│                            Analyze Error                    │
│                                   ↓                         │
│                    Attempts < 3? ─┬─ Yes → Generate SQL     │
│                                   ↓        (retry loop)     │
│                          Ask Clarification → END            │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Tech Stack
`LangGraph` `LangChain` `OpenAI GPT-4` `Streamlit` `SQLite` `SQLParse`

### Links
- 📁 [View Project](https://github.com/bryan-lolordo/sql-query-agent)
- 📖 [Architecture Docs](https://github.com/bryan-lolordo/sql-query-agent/blob/main/ARCHITECTURE.md)

---

## 👥 Code Review Crew

**Frameworks:** AutoGen + LangGraph  
**Pattern:** Multi-Agent Collaboration + Iterative Fixing Workflow

A multi-agent AI code review system that combines AutoGen's multi-agent collaboration with LangGraph's iterative fixing workflows. Get production-ready code reviews from specialized AI agents, then watch as issues are automatically fixed.

### Key Features
- 🤖 **6 Specialized Agents** - Each focused on a specific review domain
- 🔧 **Hybrid Fixing** - Pattern-based (fast, free) + LLM fallback (smart, adaptive)
- 🔄 **Iterative Workflow** - Fixes issues one-by-one with testing after each change
- 📊 **Real-time Progress** - See each iteration, pattern match, and fix applied
- 🔍 **Code Comparison** - Side-by-side original vs. fixed code view

### Specialized Agents
| Agent | Role |
|-------|------|
| 🔍 **CodeAnalyzer** | Identifies code smells, anti-patterns, PEP 8 violations |
| 🔒 **SecurityReviewer** | Detects SQL injection, XSS, weak crypto, hardcoded secrets |
| ⚡ **PerformanceOptimizer** | Analyzes complexity, finds bottlenecks |
| 🧪 **TestGenerator** | Recommends comprehensive test cases |
| 🎯 **ReviewOrchestrator** | Coordinates workflow and synthesizes feedback |
| 🐳 **CodeExecutor** | Safely executes code in Docker sandbox |

### Before & After Example

**Input Code:**
```python
def get_user(username):
    query = f"SELECT * FROM users WHERE name = '{username}'"
    return db.execute(query)

def hash_password(password):
    import hashlib
    return hashlib.md5(password.encode()).hexdigest()

API_KEY = "sk-1234567890abcdef"
```

**Issues Found:**
- ❌ SQL Injection vulnerability (Critical)
- ❌ Weak MD5 cryptography (Critical)  
- ❌ Hardcoded API key (High)
- ❌ Import inside function (Medium)

**Fixed Code:**
```python
import hashlib
import os

def get_user(username):
    query = "SELECT * FROM users WHERE name = ?"
    return db.execute(query, (username,))

def hash_password(password):
    return hashlib.sha256(password.encode()).hexdigest()

API_KEY = os.getenv("API_KEY")
```

### Architecture
```
┌─────────────────────────────────────────────────────────────┐
│                     STAGE 1: AUTOGEN REVIEW                  │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  User Code → ReviewOrchestrator → CodeAnalyzer              │
│                                 → SecurityReviewer          │
│                                 → PerformanceOptimizer      │
│                                 → TestGenerator             │
│                                 → Final Report              │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│                    STAGE 2: LANGGRAPH FIXING                 │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  Issues → [Fix Issue → Test Code → Route] → Fixed Code      │
│               ↑                      ↓                      │
│               └────── Continue ──────┘                      │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Hybrid Fixing Approach
| Fix Type | Speed | Cost | Success Rate |
|----------|-------|------|--------------|
| Pattern-Based | ~0.1s/issue | $0 | 100% (matched patterns) |
| LLM Fallback | ~2-5s/issue | ~$0.01-0.03 | ~85% first attempt |
| **Overall** | ~30-60s (10 issues) | ~$0.05-0.15 | **~90%** |

### Tech Stack
`AutoGen` `LangGraph` `OpenAI GPT-4` `Streamlit` `Docker` `Python AST`

### Links
- 📁 [View Project](https://github.com/bryan-lolordo/code-review-crew)
- 📖 [Architecture Docs](https://github.com/bryan-lolordo/code-review-crew/blob/main/ARCHITECTURE.md)

---

## 🧠 Framework Comparison

| Aspect | Semantic Kernel | LangGraph | AutoGen |
|--------|----------------|-----------|---------|
| **Best For** | Tool orchestration | Cyclical workflows | Multi-agent teams |
| **Pattern** | Plugin-based autonomy | State machines | Agent conversations |
| **Strength** | Enterprise integration | Retry/refinement loops | Agent collaboration |
| **Complexity** | Medium | Medium-High | High |
| **Use Case** | Copilots, assistants | Self-correcting agents | Team simulations |

### Why Different Frameworks?

Each project was built with the **right tool for the job**:

- **Career Copilot** → Semantic Kernel: Needed plugin architecture and Azure integration
- **SQL Query Agent** → LangGraph: Needed cyclical retry loops with state
- **Code Review Crew** → AutoGen + LangGraph: Needed both multi-agent debate AND iterative fixing

---

## 🎓 Skills Demonstrated

### AI/ML Engineering
- ✅ Multiple agentic frameworks (Semantic Kernel, LangGraph, AutoGen)
- ✅ Multi-agent system design and coordination
- ✅ Prompt engineering and optimization
- ✅ State management in AI workflows
- ✅ Hybrid AI approaches (pattern-matching + LLM)
- ✅ Self-improving and self-correcting AI patterns

### Software Engineering
- ✅ Production-ready code architecture
- ✅ API integration (OpenAI, Azure, SerpAPI)
- ✅ Database design and safe query execution
- ✅ Web application development (Streamlit)
- ✅ Docker containerization for code execution
- ✅ Comprehensive documentation

### System Design
- ✅ State machine design (LangGraph)
- ✅ Plugin/modular architecture (Semantic Kernel)
- ✅ Multi-agent coordination (AutoGen)
- ✅ Retry and fallback strategies
- ✅ Quality-based routing
- ✅ Two-stage pipeline architecture

---

## 🚀 Future Projects

### Agent Evaluation Framework
- Performance metrics and testing harness
- A/B testing for prompts and models
- Regression testing for AI quality
- Success rate tracking over time

### Latency Optimization System
- Streaming responses for real-time UX
- Parallel execution strategies
- Smart caching with TTL
- Model routing (fast vs. accurate paths)

### RAG System
- Document Q&A with vector databases
- Retrieval-augmented generation
- Context window management
- Multi-document synthesis

---

## 📊 Portfolio Stats

| Metric | Value |
|--------|-------|
| **Frameworks Mastered** | 3 (Semantic Kernel, LangGraph, AutoGen) |
| **Total Projects** | 3 |
| **Unique Patterns** | 5+ (tool orchestration, self-correction, multi-agent, hybrid fixing, state machines) |
| **Lines of Code** | ~5,000+ |
| **Documentation** | Full architecture docs for each project |

---

## 👨‍💻 About Me

**Bryan LoLordo**

AI Engineer specializing in agentic AI systems and GenAI applications.

- 🔧 **Focus:** Production-ready AI agents
- 🛠️ **Frameworks:** Semantic Kernel, LangGraph, AutoGen
- 🎯 **Expertise:** Multi-agent systems, self-correcting AI, tool orchestration
- 💼 **Goal:** Building AI systems that think, learn, collaborate, and improve

### Connect
- [LinkedIn](https://www.linkedin.com/in/bryanlolordo/)
- [GitHub](https://github.com/bryan-lolordo)

---

## 📄 License

MIT License - See individual project repositories for details.

---

<div align="center">

**Built with ❤️ using Agentic AI patterns**

*Demonstrating enterprise-grade AI agent development across multiple frameworks* 🎯

</div>
