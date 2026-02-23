# AI Coding Agent Productivity — Research Evidence & Case Studies

---

## Part 1: Three-Finding Framework — Coding Agents vs. E2E Agentic Workflow

---

### Finding 1 — Coding Agents Alone Do NOT Produce Massive Individual Gains

**Source: [METR / arXiv RCT, July 2025 (Becker et al.) — Peer-reviewed](https://arxiv.org/abs/2507.09089)**

A peer-reviewed randomized controlled trial ([arXiv: 2507.09089](https://arxiv.org/abs/2507.09089)) had 16 experienced open-source developers complete 246 real tasks on their own mature codebases — using frontier AI tools including Cursor Pro with Claude 3.5/3.7 Sonnet. Developers *predicted* AI would make them 24% faster. The actual result: AI increased completion time by **19% — it made them slower**.

Even more striking: even after the experiment concluded, developers still *believed* they had been faster when using AI — a stark perception gap documented in the [METR study blog post](https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/) that explains why anecdotal reports of "massive gains" cannot be trusted.

Even the studies that do show positive gains are modest:
- **Google's internal RCT**: ~21% faster task completion
- **Multi-company study (Microsoft, Accenture, Fortune 100)**: 26% productivity gain on average — with junior developers gaining 35–39% but **senior developers only 8–16%**

**Key point:** The evidence ceiling for individual AI coding agent adoption is roughly 20–30% under optimistic conditions — nowhere near 70–80%. For experienced developers on complex legacy codebases, gains can be zero or negative.

---

### Finding 2 — Even Where Individual Gains Exist, Organizational Delivery Does NOT Improve

**Source: [Faros AI Productivity Paradox Report 2025](https://www.faros.ai/blog/ai-software-engineering) + [DORA 2025](https://www.faros.ai/blog/key-takeaways-from-the-dora-report-2025) (10,000+ developers, 1,255 teams)**

Faros AI's 2025 research, drawing on telemetry from over 10,000 developers across 1,255 teams, found that while developers using AI were writing more code and completing more tasks, **organizations saw no measurable improvement in delivery velocity or business outcomes**. AI-augmented code was getting bigger and buggier, simply shifting the bottleneck from writing to code review.

The DORA 2025 report is precise on the root cause:

> "AI acts as an amplifier, not a universal productivity booster — it magnifies the strengths of high-performing organizations and the dysfunctions of struggling ones."

Teams with pre-existing constraints see their individual productivity increases absorbed by downstream bottlenecks. Developers using AI interact with 47% more pull requests daily — but that activity doesn't translate to faster shipping.

**Key point:** Giving developers a coding agent is a *local optimization*. If review, testing, QA, and planning pipelines aren't also transformed, the faster code generation just creates a bigger pile-up downstream. You trade one bottleneck for another.

---

### Finding 3 — End-to-End AI-Augmented Workflow DOES Produce Step-Change Results

**Source: [Bain Technology Report 2025](https://www.bain.com/insights/from-pilots-to-payoff-generative-ai-in-software-development-technology-report-2025/) + [McKinsey PDLC Research 2025](https://www.mckinsey.com/industries/technology-media-and-telecommunications/our-insights/unlocking-the-value-of-ai-in-software-development)**

Bain's 2025 research found a clear bifurcation:

| Approach | Productivity Gain |
|---|---|
| Basic AI code assistants | 10–15% |
| AI + end-to-end process transformation | **25–30%** |

Critically, Bain notes that most of the 10–15% gain from tools alone doesn't even translate to ROI because the time saved isn't redirected to higher-value work.

McKinsey's research on high-performing AI-driven software organizations goes further. The highest performers:
- Embedded AI across the **entire development lifecycle** — design, coding, testing, deployment, and adoption tracking
- Were **six to seven times more likely** to scale to four or more AI use cases
- Saw team productivity and time-to-market improve by **16–30%**, and software quality improve by **31–45%**

**Key point:** The gains aren't in the tool — they're in the *system*. E2E Agentic Agile works because it addresses every stage of the workflow: requirements, sprint planning, code generation, review, testing, and deployment. That converts individual AI assistance into organizational throughput.

---

### Summary Table

| Approach | Individual Gain | Translates to Org Delivery? |
|---|---|---|
| Coding agent for individual dev | 0–26% (often negative for seniors) | No |
| Broad AI tool adoption, unchanged process | 10–15% | Rarely |
| E2E AI-augmented workflow transformation | 25–45% | Yes |

---

---

## Part 2: Inspiration Case Studies

---

### Case Study 1: Microsoft + Bankdata — COBOL Mainframe Modernization
**Source: [Microsoft Azure Dev Blog, July 2025](https://devblogs.microsoft.com/all-things-azure/how-we-use-ai-agents-for-cobol-migration-and-mainframe-modernization/) (official published collaboration)**

**Context:** Bankdata is a technology company established by a consortium of Danish banks collectively representing over 30% of the Danish banking market. They have over **70 million lines of COBOL code** still running on mainframe today. Historically, re-platforming has been "a tremendous manual, time-consuming and costly affair."

**What happened with ad-hoc AI:**
Microsoft and Bankdata began their first experiments in late 2024 using simple GPT-4 chat interactions, later GitHub Copilot. The results were poor:
- Limited token windows caused loss of relevant context
- General LLM understanding of COBOL was very limited
- Results were described as "a good mix of educated guesses and hallucinational gibberish"

**The shift to structured multi-agent architecture:**
The team abstracted a structured set of migration steps across multiple specialized agents:
1. **Reverse engineering** — extracting business logic from code, comments, documentation, and human SMEs
2. **Preparation** — cleaning code for AI consumption, translating COBOL comments
3. **Transformation** — structured agent-to-agent handoffs for code conversion
4. **Validation** — verifying output against original business logic

Key technical finding: when too much context was given to agents, they lost coherence and hallucinated heavily. When context was kept **short and structured**, output quality was "surprisingly good." The hardest challenge was managing COBOL call-chain structure (module-to-module dependencies) — they reached depth level 3 before coherence broke down.

**Relevance to your work:**
- Direct banking + mainframe context, published by Microsoft
- Demonstrates that even the most advanced teams found unstructured AI fails on real COBOL — structured multi-agent approach was the breakthrough
- Open-source framework published at [`Azure-Samples/Legacy-Modernization-Agents`](https://github.com/Azure-Samples/Legacy-Modernization-Agents) on GitHub
- Microsoft is actively inviting bank collaboration

**Narrative use:** *"Even Microsoft failed with ad-hoc AI on real banking COBOL. The breakthrough required moving to a structured, staged, multi-agent architecture — exactly the design philosophy behind Agent Assisted Agile."*

---

### Case Study 2: BMad Method — Agentic Agile Framework
**Source: Community + practitioner evidence (2025) | [GitHub: bmad-code-org/BMAD-METHOD](https://github.com/bmad-code-org/BMAD-METHOD)**

**What it is:**
BMad (Breakthrough Method for Agile AI-Driven Development) is an open-source framework that has gained significant practitioner traction in 2025. It was built specifically to address the failure mode of unstructured AI coding: *"unstructured, prompt-driven AI use is creating 'black box' codebases that are difficult to maintain, audit, and scale — introducing significant business risk."*

**How it works — the agent team:**

| Agent | Role |
|---|---|
| Analyst | Surfaces requirements, constraints, risks — produces project brief |
| Product Manager | Generates PRD with functional/non-functional requirements, epics, user stories |
| Architect | Creates full system design, component map, data flow, integration strategy |
| Product Owner | Runs alignment checklists, resolves spec conflicts before coding starts |
| Scrum Master | Shards epics into granular, context-rich story files with acceptance tests |
| Developer | Implements each story in a dedicated branch with full planning context |
| QA | Multi-agent automated checks, review, and refactoring before merge |

Every artifact, review, and decision is **versioned in Git** — creating a fully auditable history throughout. No code is written until all planning agents have signed off.

**Results (practitioner evidence):**
Enterprise teams using structured AI approaches achieved **12.92% to 21.83% more pull requests per week**, with **96% user adoption rates** among developers who tried structured workflows — compared to unstructured AI tool adoption.

**Honest caveat:**
BMad does not yet have peer-reviewed RCTs. Evidence is from practitioners and community deployments, not academic studies. Use it as an illustration of *what the E2E approach looks like in practice*, not as a benchmarked productivity number.

**Relevance to your work:**
- Mirrors the design philosophy of your Agent Assisted Agile 3-Day Sprint framework
- Validates the role-based, artifact-driven, structured handoff model
- Shows growing enterprise adoption of exactly this architecture

**Narrative use:** *"The industry is independently converging on this model — BMad, Microsoft's Bankdata work, and our own Agent Assisted Agile Sprint all arrive at the same conclusion: role-based agents with structured handoffs and versioned artifacts is what separates real productivity gains from tool-adoption theatre."*

---

### Connecting the Cases to Your Argument

| | Microsoft + Bankdata | BMad Method | Your Framework |
|---|---|---|---|
| **Domain** | Banking COBOL mainframe | General software | Mainframe modernization |
| **Key insight** | Ad-hoc AI fails; structure succeeds | Structured agents = predictable delivery | Domain-specific structure for Z |
| **Evidence type** | Published Microsoft case study | Practitioner + community | Your own pilot KPIs |
| **Narrative role** | "Why structure matters" | "What the structure looks like" | "We've built this for mainframe" |

---

*Research compiled February 2026. Sources: [arXiv 2507.09089](https://arxiv.org/abs/2507.09089), [Faros AI Productivity Paradox Report 2025](https://www.faros.ai/blog/ai-software-engineering), [DORA 2025 via Faros AI](https://www.faros.ai/blog/key-takeaways-from-the-dora-report-2025), [Bain Technology Report 2025](https://www.bain.com/insights/from-pilots-to-payoff-generative-ai-in-software-development-technology-report-2025/), [McKinsey PDLC Research 2025](https://www.mckinsey.com/industries/technology-media-and-telecommunications/our-insights/unlocking-the-value-of-ai-in-software-development), [Microsoft Azure Dev Blog July 2025](https://devblogs.microsoft.com/all-things-azure/how-we-use-ai-agents-for-cobol-migration-and-mainframe-modernization/), [BMad community documentation](https://github.com/bmad-code-org/BMAD-METHOD).*
