# RAG-ations
To build a production Retrieval-Augmented Generation (RAG) tool for banking (e.g., an automated policy parser or internal financial research assistant), implement a strict security layer.

                  ┌──────────────────────────────────────────────┐
                  │               Security Gateway               │
                  ├──────────────────────┬───────────────────────┤
                  │ 1. PII De-Id (Regex) │ 2. Prompt Guardrails  │
 User Prompt ────►│    Strips Names,     │   Blocks Injection /  ├────► Safe Prompt
                  │    Account Numbers   │     Jailbreaks        │          │
                  └──────────────────────┴───────────────────────┘          │
                                                                            ▼
┌───────────────────────────────────────────────────────────────────────────┴┐
│                           Regulated Sandbox Zone                           │
│                                                                            │
│  ┌───────────────────────┐   Vectors   ┌────────────────────────────────┐  │
│  │   Vector Database     │◄───────────►│       Enterprise LLM           │  │
│  │ (Chroma / pgvector)   │  Retrieval  │ (Llama 3 / Mistral On-Premise) │  │
│  └───────────────────────┘             └────────────────────────────────┘  │
└────────────────────────────────────────────────────────────────────────────┘
