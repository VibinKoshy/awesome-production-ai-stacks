---
name: "Delivery Hero — Agentic AI Product Knowledge Base (Predefined Workflow)"
category: "Product Data / Catalog Enrichment"
confidence: "Reference"
ori_score: 6.9
---

# Stack Overview

**Use Case:** Automate product catalog enrichment by extracting structured attributes from vendor inputs (title + image) and generating standardized internal product titles. This improves search, filtering, recommendations, analytics, and overall catalog consistency. :contentReference[oaicite:0]{index=0}

**Confidence Level:** Reference (public case study) :contentReference[oaicite:1]{index=1}

## Components

- **LLM (Multimodal):** Used for attribute extraction from vendor product title + image (22 predefined attribute types). :contentReference[oaicite:2]{index=2}
- **LLM (Text):** Used for standardized title generation from extracted attributes. :contentReference[oaicite:3]{index=3}
- **Orchestration:** Predefined agents / workflow (2-step sequence: extract → generate). Chosen for cost, predictability, and debuggability. :contentReference[oaicite:4]{index=4}
- **Additional:**
  - **Prompt Engineering:** Concise prompts to reduce tokens/cost/latency and improve accuracy. :contentReference[oaicite:5]{index=5}
  - **Knowledge Distillation (Teacher → Student):** Teacher model (e.g., GPT-4o) generates dataset; student (e.g., GPT-4o-mini) fine-tuned for cheaper/faster production with shorter prompts. :contentReference[oaicite:6]{index=6}
  - **Confidence Scoring + HITL:** Logits → probabilities; low-confidence outputs routed to human review. :contentReference[oaicite:7]{index=7}

## ORI Breakdown

- **Reliability:** 6.0/10 - HITL gating reduces bad outputs entering the KB, but uptime / incident history not disclosed publicly. :contentReference[oaicite:8]{index=8}
- **Cost Predictability:** 8.5/10 - Fixed 2-step workflow with fewer calls + prompt reduction + distillation explicitly optimized for cost/latency. :contentReference[oaicite:9]{index=9}
- **Debuggability:** 8.0/10 - Predefined workflow is explicitly chosen for “debuggability” and easier tracing than dynamic agents. :contentReference[oaicite:10]{index=10}
- **Scalability:** 6.5/10 - Designed for “vast and growing catalogs,” but throughput/load test numbers not disclosed. :contentReference[oaicite:11]{index=11}
- **Security:** 5.5/10 - No detailed security/compliance specifics provided in the public write-up. (Assumed standard enterprise controls, not verifiable.) :contentReference[oaicite:12]{index=12}

## Performance

- **Latency:** Not disclosed (article emphasizes reducing latency via shorter prompts + distillation). :contentReference[oaicite:13]{index=13}
- **Throughput:** Not disclosed
- **Bottlenecks:**
  - Token-heavy prompts (addressed via prompt engineering + distillation). :contentReference[oaicite:14]{index=14}
  - Edge cases / uncertainty (handled via confidence threshold + human review). :contentReference[oaicite:15]{index=15}

## Cost

- **Monthly Cost:** Not disclosed
- **Cost Drivers:**
  1) LLM calls (multimodal extraction + title generation)
  2) Prompt length / tokens
  3) Human review volume (for low confidence cases)
- **Cost Optimization:**
  - Prompt engineering to reduce tokens and improve correctness. :contentReference[oaicite:16]{index=16}
  - Teacher→Student distillation to enable shorter prompts and cheaper model usage in production. :contentReference[oaicite:17]{index=17}

## Reliability

- **Fallback Strategy:** Confidence gating; low-confidence results routed to human verification instead of auto-publishing. :contentReference[oaicite:18]{index=18}
- **Rate Limiting:** Not disclosed
- **Retry Logic:** Not disclosed
- **Monitoring:** Implied quality control via confidence scoring and review flow; detailed observability stack not disclosed. :contentReference[oaicite:19]{index=19}

## Data & Security

- **Data Isolation:** Not disclosed
- **Retention Policy:** Not disclosed
- **PII Handling:** Not disclosed (inputs are product titles/images; still can contain accidental PII—should be sanitized in real deployments)
- **Compliance:** Not disclosed

## Deployment

- **Deployment Complexity:** Medium
- **Infrastructure:** Not disclosed
- **CI/CD:** Not disclosed
- **Maintenance Burden:** Medium (requires schema maintenance + threshold tuning + HITL ops)

## Evaluation

- **Eval Strategy:** Described as “evaluations” for student-vs-teacher output quality after training cycles; exact methodology not disclosed. :contentReference[oaicite:20]{index=20}
- **Metrics:** Not disclosed (suggested: attribute accuracy, format compliance, review rate, override rate)
- **Tooling:** Not disclosed

## Production Evidence

**Required for Confirmed confidence:**
- [ ] Stack is running in production (>30 days)
- [ ] Handling real user traffic (>100 queries/day)
- [ ] Can provide metrics or incident data
- [ ] Company/product attribution (can be anonymized)

**Optional but helpful:**
- [ ] Architecture diagram
- [x] Blog post / case study :contentReference[oaicite:21]{index=21}
- [ ] Performance benchmarks

## Recommended When

- You have high-volume vendor catalogs with inconsistent titles/metadata
- You can define a stable attribute schema (they use 22 predefined attribute types) :contentReference[oaicite:22]{index=22}
- You need predictable cost/latency and easy debugging (predefined workflow) :contentReference[oaicite:23]{index=23}
- You can support a human-review loop for low-confidence outputs :contentReference[oaicite:24]{index=24}

## Anti-patterns

- Using dynamic/self-looping agents when you primarily need predictable cost/latency for a core pipeline
- Publishing LLM outputs directly to the knowledge base without confidence gating / HITL :contentReference[oaicite:25]{index=25}
- Skipping distillation when prompts must include many examples (you’ll pay repeatedly in tokens/latency) :contentReference[oaicite:26]{index=26}
