# AI Day 1 – Observations

## 10. Observations

| Criterion | Chatbot | Workflow | Agent |
|-----------|---------|----------|-------|
| Q1 correct? | N | Y | Y |
| Q2 correct? | N | Y | Y |
| Q3 correct? | N | N | Y |
| Q4 handled well? | Y | N | Y |
| Challenge question handled? | Y | N | Y |
| Same output on repeat run? | N | Y | N |
| Approximate response time | ~2 sec | Instant | ~3 sec |
| Number of LLM calls per question | 1 | 0 | 1–3 |
| One strength | Natural language | Accurate fee rules | Accurate + reasoning |
| One weakness | Hallucination | Rigid rules | Slower than workflow |
| Best suited for | General Q&A | Fixed business rules | Smart assistants |

## Agent Trace (Question 2)

| Step | Tool called and arguments | Result |
|------|----------------------------|--------|
| 1 | get_course_fee(course_code="CS101") | 12000 |
| 2 | get_course_fee(course_code="AI202") | 18000 |
| 3 | calculator("(12000+18000)*0.9") | 27000.0 |
| 4 | Final answer | Rs. 27,000 |

## 11. Discussion Questions

### 1. Why is a confident wrong answer more dangerous than “I don't know”?

A confident wrong answer can mislead users into believing false information, while “I don't know” encourages verification.

### 2. Why might a company still prefer a workflow over an agent?

Workflows are faster, predictable, and always produce the same result for fixed business rules.

### 3. What problems occur if an agent changes steps between runs?

It reduces consistency, makes debugging difficult, and may produce different outputs for the same question.

### 4. Where would you draw the line between workflow and agent?

Use workflows for repetitive, rule-based tasks and agents for complex questions that require reasoning and tool use.

### 5. Which parts of `agent.py` are the LLM, tools, and loop?

- **LLM:** `client.chat.completions.create()`
- **Tools:** `get_course_fee()` and `calculator()`
- **Loop:** `for step in range(...)`