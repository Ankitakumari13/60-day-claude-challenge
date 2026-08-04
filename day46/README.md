# 🤖 Autonomous Agent Studio

### 🚀 ABTalks 60-Day Claude Challenge — Day 46/60

> **Design. Orchestrate. Iterate. Ship.**

**Autonomous Agent Studio** is a multi-agent AI orchestration system designed to plan, execute, evaluate, critique, improve, remember, and repeat until a defined success condition is reached.

The project demonstrates how **agentic AI systems** can move beyond one-shot prompting toward continuous, feedback-driven autonomous workflows.

---

## 🌟 Overview

Traditional AI applications often follow:

```text
User → Prompt → AI → Response
```

Autonomous Agent Studio explores a more advanced architecture:

```text
Goal
  ↓
Planner
  ↓
Executor
  ↓
Evaluator
  ↓
Critic
  ↓
Improver
  ↓
Memory Manager
  ↓
Stop Condition?
  ├── ❌ No → Evaluator → Critic → Improver → Repeat
  └── ✅ Yes → Final Reviewer → Final Result
```

The system continuously evaluates the current output and improves it until the target condition is satisfied.

---

## ✨ Key Features

### 🧠 Multi-Agent Architecture

The application can orchestrate specialized AI agents:

| Agent              | Responsibility                                 |
| ------------------ | ---------------------------------------------- |
| 🗺️ Planner        | Breaks the objective into actionable steps     |
| ⚙️ Executor        | Executes the generated plan                    |
| 📊 Evaluator       | Evaluates the current output against a rubric  |
| 🔍 Critic          | Identifies weaknesses, gaps, and errors        |
| 🚀 Improver        | Refines the output using evaluation + critique |
| 🧠 Memory Manager  | Maintains useful information across iterations |
| 🛡️ Safety Monitor | Monitors safety and guideline compliance       |
| ✅ Final Reviewer   | Performs the final quality review              |

---

## 🔄 Real Autonomous Feedback Loop

The core feature is a genuine iterative loop:

```text
Evaluator
    ↓
Critic
    ↓
Improver
    ↓
    └──────────────→ Evaluator
```

Each iteration makes live model calls rather than relying on predefined or hardcoded results.

The system threads state between rounds:

```text
Previous Evaluation
        +
Previous Critique
        +
Current Draft
        ↓
     Improver
        ↓
   Improved Draft
        ↓
    New Evaluation
```

---

## 🛑 Intelligent Stop Conditions

The system checks stopping conditions after every iteration.

### 1. Plateau Detection

Stops when the score improvement remains below a small delta for consecutive rounds.

```text
Round 1 → 65
Round 2 → 72  (+7)
Round 3 → 72  (+0)
Round 4 → 72  (+0)

→ Plateau detected
```

### 2. Target Threshold

Stops when the evaluation score reaches the target.

```text
Target = 85

Current Score = 87

→ Threshold reached
```

### 3. Hard Safety Cap

A hard iteration limit acts only as a **fallback safety mechanism** to prevent an uncontrolled loop.

The intended stopping mechanism is always the runtime stop check.

---

## 📈 Iteration History

The application maintains a running history containing:

* Round number
* Evaluation score
* Score delta
* Draft
* Critique
* Evaluation
* Stop-check status
* Memory updates

Example:

```text
Round 1
Score: 65

Round 2
Score: 72
Delta: +7

Round 3
Score: 81
Delta: +9

Round 4
Score: 87
Delta: +6

→ Target threshold reached
→ Final Reviewer activated
```

---

## 🧩 Information Flow

The system uses the stop-check to control the information flow between rounds.

```text
             ┌──────────────┐
             │   Planner    │
             └──────┬───────┘
                    ↓
             ┌──────────────┐
             │   Executor   │
             └──────┬───────┘
                    ↓
             ┌──────────────┐
             │  Evaluator   │
             └──────┬───────┘
                    ↓
             ┌──────────────┐
             │    Critic    │
             └──────┬───────┘
                    ↓
             ┌──────────────┐
             │   Improver   │
             └──────┬───────┘
                    ↓
             ┌──────────────┐
             │ Stop Check?  │
             └───┬──────┬───┘
                 NO     YES
                  │       │
                  ↓       ↓
             Evaluator  Final Reviewer
                  │       │
                  └───↺   ↓
                      Final Output
```

---

## 🖥️ Dashboard

The interface provides a real-time orchestration dashboard containing:

* 🔄 Workflow visualization
* 🤖 Active agent indicator
* 🟢 Live system status
* 🔢 Open-ended round indicator
* 📜 Activity log
* 📊 Evaluation reports
* 📈 Score progression
* 🧠 Memory updates
* 🔁 Round-over-round improvements
* 🔄 Retry count
* 📝 Intermediate agent outputs
* 🛑 Stop-condition status
* 🏁 Final summary

The round indicator intentionally uses an open-ended format:

```text
Round 3 — checking stop condition…
```

rather than:

```text
Round 3 of 5
```

because the number of iterations is determined dynamically at runtime.

---

## 🛠️ Technology Stack

* **HTML5**
* **CSS3**
* **Vanilla JavaScript**
* **Claude API**
* **Fetch API**
* **Multi-Agent Orchestration**
* **Agentic Workflow Design**
* **Prompt Engineering**
* **Iterative Evaluation**
* **State & Memory Management**

### No external frontend libraries

The project is designed as a **single self-contained HTML application**.

---

## 📁 Project Structure

```text
Autonomous-Agent-Studio/
│
├── index.html
└── README.md
```

Everything required for the interface and orchestration logic is contained inside the HTML file.

---

## ⚙️ How It Works

### Step 1 — Define the Goal

The user provides an objective for the autonomous system.

### Step 2 — Planning

The Planner analyzes the objective and creates an actionable strategy.

### Step 3 — Execution

The Executor generates the initial output based on the plan.

### Step 4 — Evaluation

The Evaluator scores the current output using the defined rubric.

### Step 5 — Critique

The Critic analyzes weaknesses and identifies opportunities for improvement.

### Step 6 — Improvement

The Improver receives the current draft, evaluation, and critique and creates a better version.

### Step 7 — Memory

Relevant information from the current round is carried forward.

### Step 8 — Stop Check

The system checks:

```text
Plateau?
   ↓
Threshold reached?
   ↓
Safety fallback?
   ↓
Continue or Finish
```

### Step 9 — Final Review

Once a stopping condition is triggered, the Final Reviewer evaluates the final result.

---

## 🔐 Error Handling & Reliability

The application includes mechanisms for:

* API failure handling
* Retry attempts
* Loading states
* Graceful recovery
* Invalid response handling
* Runtime stop protection
* Safety fallback
* Empty-response protection

This prevents the autonomous loop from running indefinitely or failing silently.

---

## 🎯 Project Goals

This project was created to explore:

* How autonomous AI agents communicate
* How specialized agents can collaborate
* How feedback loops improve AI outputs
* How model evaluation can control workflow execution
* How memory can persist context between iterations
* How stopping conditions can govern agent autonomy
* How multi-agent systems can be implemented using frontend JavaScript

---

## 🚀 Future Extensions

Possible improvements include:

### 🔹 Agent Marketplace

Allow users to create and add custom agents.

### 🔹 Persistent Memory

Store long-term memory using IndexedDB or a backend database.

### 🔹 Tool Calling

Allow agents to use:

* Search
* Calculators
* File processing
* Databases
* External APIs

### 🔹 Human-in-the-Loop

Allow users to approve or reject intermediate outputs.

### 🔹 Parallel Agents

Run multiple agents simultaneously:

```text
              ┌── Researcher ──┐
              │                │
Goal ─────────┼── Analyst ─────┼──→ Synthesizer
              │                │
              └── Critic ──────┘
```

### 🔹 Advanced Memory

Introduce:

* Short-term memory
* Long-term memory
* Semantic retrieval
* Context compression
* Memory prioritization

### 🔹 Agent Performance Analytics

Track:

* Average score improvement
* Agent latency
* Retry rate
* Token usage
* Success rate
* Number of iterations
* Stop-condition frequency

---

## 📊 Architecture Overview

```text
                    ┌─────────────┐
                    │    USER     │
                    └──────┬──────┘
                           ↓
                    ┌─────────────┐
                    │   PLANNER   │
                    └──────┬──────┘
                           ↓
                    ┌─────────────┐
                    │  EXECUTOR   │
                    └──────┬──────┘
                           ↓
                ┌─────────────────────┐
                │      EVALUATOR      │
                └──────────┬──────────┘
                           ↓
                ┌─────────────────────┐
                │       CRITIC        │
                └──────────┬──────────┘
                           ↓
                ┌─────────────────────┐
                │      IMPROVER       │
                └──────────┬──────────┘
                           ↓
                ┌─────────────────────┐
                │    STOP CHECK       │
                └───────┬───────┬─────┘
                        │       │
                      CONTINUE  STOP
                        │       │
                        ↺       ↓
                         FINAL REVIEWER
                                ↓
                         FINAL OUTPUT
```

---

## 📌 Important Note

This project is intended as an **educational and experimental demonstration of agentic AI orchestration**.

When connecting a browser application directly to an AI API, API credentials should **not be exposed in production frontend code**.

For a production deployment, use a secure backend or server-side proxy to protect API credentials.

---

## 🧠 What I Learned

Building Autonomous Agent Studio helped me understand that agentic AI is not simply about making an AI model generate content.

The real challenge is designing a system where agents can:

> **Plan → Execute → Evaluate → Critique → Improve → Remember → Decide → Repeat**

This project strengthened my understanding of:

**AI Agents • Multi-Agent Systems • Prompt Engineering • AI Evaluation • Automation • JavaScript • System Architecture**

---

## 🏆 Challenge Progress

### ABTalks 60-Day Claude Challenge

**Day 46/60 ✅**

```text
██████████████████████████████░░░░░░░░░░░░░░░░░░░░░░░░░░░░

46 / 60 Days Completed
```

**14 days remaining. 🚀**

---

## 👩‍💻 Author

**Ankita Kumari**

B.Tech Computer Science & Data Science Student
Interested in **AI • Data Science • Generative AI • Agentic Systems • Software Development**

---

## ⭐ If You Like This Project

If you found this project interesting:

⭐ Star the repository
🍴 Fork it
💡 Experiment with your own agents
🔗 Share your ideas and improvements

---

### 🚀 Autonomous by Design. Intelligent by Loop.

**Day 46/60 — ABTalks Claude Challenge**
