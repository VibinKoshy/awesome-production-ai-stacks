# <Stack Name>

**Category:** <e.g., Product / Revenue / RAG / Support / Voice>  
**Confidence:** 🔍 Confirmed | 🧠 Inferred | 🧪 Reference  
**Readiness:** ✅ Production Ready | ⚠️ Wrapper | ❌ Vaporware (if applicable)

## Problem
Describe the business/technical problem in 3–6 lines.

## Who this is for
- Ideal users / teams
- Org size / maturity
- Data environment (regulated / non-regulated)

## System objective
What success looks like (measurable outcomes).

## Architecture
### Core components
- **LLM:** <model + hosting>
- **Embeddings:** <model>
- **Vector DB / Search:** <tool>
- **Orchestration:** <LangChain/LlamaIndex/custom>
- **App backend:** <FastAPI/Node/etc>
- **Infra:** <Vercel/AWS/etc>
- **Observability:** <LangSmith/OpenTelemetry/etc>
- **Evaluation:** <golden set / offline eval / online metrics>

### Data flow (high level)
1.
2.
3.

## Why this works
Bullet reasons tied to production constraints:
- latency
- cost
- debugability
- reliability
- security

## Known tradeoffs
- What you sacrifice
- What will become painful at scale

## Failure modes
Be explicit:
- What breaks first
- How it fails silently
- How to detect it

## Implementation notes
- Glue code expectations
- Caching strategy
- Rate limiting / retries
- Human-in-the-loop points

## Evaluation & monitoring
- Offline evaluation approach
- Online metrics to track
- Regression checks

## Security & data considerations
- PII handling
- data isolation
- retention and audit logging

## Sources (required for 🔍 Confirmed)
- Link 1
- Link 2

## Change log
- YYYY-MM-DD: Created
