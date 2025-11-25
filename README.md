# Agentic AI Portfolio

A collection of production-ready AI agent projects demonstrating expertise across multiple agentic frameworks, patterns, and architectures.

## 🎯 About This Portfolio

This portfolio showcases **senior-level AI engineering skills** through hands-on projects that solve real problems using different agentic AI frameworks. Each project demonstrates distinct patterns and capabilities:

| Project | Framework | Pattern | Status |
|---------|-----------|---------|--------|
| [Career Copilot](#-career-copilot) | Semantic Kernel | Autonomous Tool Orchestration | ✅ Complete |
| [SQL Query Agent](#-sql-query-agent) | LangGraph | Self-Correction Loops | ✅ Complete |
| [Code Review Crew](#-code-review-crew) | AutoGen | Multi-Agent Collaboration | 🔜 Coming Soon |

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
- Microsoft Semantic Kernel
- Azure OpenAI (GPT-4)
- Streamlit
- SQLite
- SerpAPI

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
- LangGraph
- LangChain
- OpenAI GPT-4
- Streamlit
- SQLite
- SQLParse

### Links
- 📁 [View Project](https://github.com/bryan-lolordo/sql-query-agent)
- 📖 [Architecture Docs](https://github.com/bryan-lolordo/sql-query-agent/blob/main/ARCHITECTURE.md)

---

## 👥 Code Review Crew

**Framework:** AutoGen  
**Pattern:** Multi-Agent Collaboration

*🔜 Coming Soon*

A multi-agent code review system where specialized AI agents collaborate to provide comprehensive code analysis.

### Planned Features
- 🔍 **Reviewer Agent** - Finds bugs and logic issues
- 🔒 **Security Agent** - Identifies vulnerabilities
- ⚡ **Performance Agent** - Spots optimization opportunities
- 📝 **Style Agent** - Enforces code standards
- 🎯 **Coordinator Agent** - Synthesizes feedback

### Why AutoGen?
Unlike single-agent systems, AutoGen enables multiple specialized agents to **debate, discuss, and collaborate** - perfect for code review where multiple perspectives improve quality.

---

## 🧠 Framework Comparison

| Aspect | Semantic Kernel | LangGraph | AutoGen |
|--------|----------------|-----------|---------|
| **Best For** | Tool orchestration | Cyclical workflows | Multi-agent teams |
| **Pattern** | Plugin-based autonomy | State machines | Conversations |
| **Strength** | Enterprise integration | Retry/refinement loops | Agent collaboration |
| **Complexity** | Medium | Medium-High | High |
| **Use Case** | Copilots, assistants | Self-correcting agents | Team simulations |

---

## 🎓 Skills Demonstrated

### AI/ML Engineering
- ✅ Multiple agentic AI frameworks (Semantic Kernel, LangGraph, AutoGen)
- ✅ Prompt engineering and optimization
- ✅ State management in AI workflows
- ✅ Error handling and graceful degradation
- ✅ Self-improving AI patterns

### Software Engineering
- ✅ Production-ready code architecture
- ✅ API integration (OpenAI, Azure, SerpAPI)
- ✅ Database design and safe query execution
- ✅ Web application development (Streamlit)
- ✅ Documentation and technical writing

### System Design
- ✅ State machine design
- ✅ Plugin/modular architecture
- ✅ Multi-agent coordination
- ✅ Retry and fallback strategies
- ✅ Quality-based routing

---

## 🚀 Future Projects

### Evaluation Framework
- Agent performance metrics and testing
- A/B testing for prompts and models
- Regression testing for AI quality

### Latency Optimization
- Streaming responses
- Parallel execution
- Smart caching strategies
- Model routing (fast vs. accurate)

### RAG System
- Document Q&A with vector databases
- Retrieval-augmented generation
- Context management

---

## 👨‍💻 About Me

**Bryan LoLordo**

AI Engineer specializing in agentic AI systems and GenAI applications.

- 🔧 **Focus:** Production-ready AI agents
- 🛠️ **Frameworks:** Semantic Kernel, LangGraph, AutoGen
- 💼 **Goal:** Building AI systems that think, learn, and improve

### Connect
- [LinkedIn](https://www.linkedin.com/in/bryanlolordo/)
- [GitHub](https://github.com/bryan-lolordo)

---

## 📄 License

MIT License - See individual project repositories for details.

---

<div align="center">

**Built with ❤️ using Agentic AI patterns**

*Demonstrating enterprise-grade AI agent development* 🎯

</div>
