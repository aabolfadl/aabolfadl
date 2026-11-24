# Ahmed Abolfadl

**ML Engineer/Data Scientist** with an increasing interest in MLOps, specifically Model Serving.

2026 Computer Engineering graduate of the German University in Cairo with High Honors (top 10% of 550).

📍 Cairo, Egypt **UTC+2** · Open to remote ML/Data roles worldwide
· Languages: Arabic (native), English (fluent), German (B1), French

---

## Start here

Three projects worth your time.

### [kontograph](https://github.com/aabolfadl/kontograph): real-time AML for SEPA Instant payments
*Python · PyTorch Geometric · Kafka · Iceberg · DuckDB · FastAPI · ONNX — 22k LoC, 267 tests*

An end-to-end anti-money-laundering pipeline over **1,562,860** simulated SEPA Instant payments,
built under a self-imposed 200 ms p99 decision budget because EU Regulation 2024/886 removed the
overnight batch window that AML analytics used to run in.

- Decides in **8 ms p99** against that 200 ms budget.
- A temporal graph network with per-account memory lifts PR-AUC from **0.0053** (LightGBM tabular
  baseline) to **0.1717** - **+0.166** absolute, 95% CI [0.105, 0.241] under a day-blocked paired
  bootstrap. Per-node memory alone more than doubles the score.
- Each feature is defined once and compiled to three execution backends, with property-based tests
  that perturb future events to prove no feature can read them. **The suite caught three
  point-in-time leakage violations that code review had passed**, each would have inflated
  reported performance.
- Exporting the tree ensemble to ONNX moved the mean score by **7.4 × 10⁻⁸** and still flipped
  **0.26% of decisions**, inflating alert volume **12%**, because 32-bit accumulation crosses a
  cost-optimal threshold of 3.98 × 10⁻⁴. **A serving-format conversion is a model change until
  measured.**

### [bilingual-hallucination-detector](https://github.com/aabolfadl/bilingual-hallucination-detector): Arabic/English RAG faithfulness
*Qwen2.5 · PEFT · NLI · Hugging Face Inference — 🥇 1st of 22 teams, Unifonic AI Hackathon*

Detects when a retrieval-augmented answer isn't supported by its sources, in Arabic and English,
by stacking an NLI entailment stage under an LLM-as-a-Judge stage. Arabic is the harder half, models are measurably weaker there, which is most of the point.

| Model | Accuracy | Recall | Latency | Size |
|---|---:|---:|---:|---:|
| Qwen2.5-3B-Instruct | 95.3% | **97.3%** | 424 ms/sample | 6.2 GB |
| Qwen2.5-1.5B-Instruct | 94.0% | 94.7% | **251 ms/sample** | 3.1 GB |

Shipped the 1.5B: **1.7× the throughput at half the memory for 2.6 points of recall**, a trade
worth making explicit rather than defaulting to the bigger model. Deployed as a live
Hugging Face inference API. Fine-tuned weights: [balash-faty](https://github.com/aabolfadl/balash-faty)

### [contract-nli](https://github.com/aabolfadl/contract-nli): multi-agent NDA review
*LangGraph · Llama-3.1-8B · ChromaDB · Neo4j · GraphRAG*

Reviews NDAs against the 17 standard hypotheses of the public
[ContractNLI](https://stanfordnlp.github.io/contract-nli/) benchmark, labelling each as
Entailment / Contradiction / NotMentioned. Built as three successive architectures so they can be
compared against each other:

1. A fine-tuned NLI classifier behind a deterministic risk playbook.
2. A conversational agent retrieving evidence over ChromaDB vectors *or* a Neo4j knowledge graph.
3. A LangGraph pipeline of five specialised agents — retrieval, reasoning, legal-expert review,
   evidence verification, playbook — with LettuceDetect hallucination screening and
   schema-validated run traces, so every clause-level verdict ships with checkable supporting
   evidence instead of an unsourced assertion.

---

## Research

I worked on trend forecasting from scientific literature, LLM evaluation, and graph ML for
financial crime.

- **A. Abolfadl.** *KONTOGRAPH: Verified Point-in-Time Feature Consistency and Amortised
  Explanation for Real-Time Anti-Money Laundering under a 200 ms Decision Budget.*
  arXiv preprint, 2026. First author.
  [arXiv](https://arxiv.org/abs/2608.22389)
- **A. Abolfadl** et al. *Forecasting Technological Directions in Wireless Networks and Mobile
  Computing via AutoML Framework.* **IEEE MECOM 2025.** First author.
  [arXiv](https://arxiv.org/abs/2606.27394) · [IEEE Xplore](https://ieeexplore.ieee.org/abstract/document/11439456)
  — 127,820 abstracts embedded with SPECTER, meta-learned clustering, successive-halving
  topic-model selection, ARIMA/STL/Prophet/LSTM forecasting.
- **A. Abolfadl** et al. *AutoCluster, AutoTopicModeling, AutoTrendAnalysis: A Complete AutoML
  Pipeline for Predicting Emerging Trends.* **IEEE ICCA 2025.** First author.
  [arXiv](https://arxiv.org/abs/2607.22641) · [IEEE Xplore](https://ieeexplore.ieee.org/abstract/document/11430858/)

Since May 2025 I've been the only undergraduate in a five-member graduate-level research cluster. Our journal submission is under
review at the *Journal of Machine Learning and Knowledge Extraction (MDPI)*; I own the
fine-tuning track, using curriculum-learning schedules for Flan-T5 topic labelling to replace
non-deterministic LLM labelling with a controllable in-house model.

📚 [Google Scholar](https://scholar.google.com/citations?user=6LwVWkMAAAAJ) ·
🤗 [Hugging Face](https://huggingface.co/aabolfadl)

---

## Also worth a look

- **[ai-agents-for-tourism](https://github.com/aabolfadl/ai-agents-for-tourism)**: 🥈 2nd of 13
  teams, Dell Technologies AI Empower Hackathon. An LLM agent that re-plans a traveler's itinerary
  against live weather and crowding, cascading each change into ride-hailing and restaurant
  bookings. Built in 24 hours with no dataset provided; award presented by Egypt's Minister of
  Communications and IT.
- **[ai-portfolio-manager](https://github.com/aabolfadl/ai-portfolio-manager)** — a
  mixture-of-agents investment simulator where each agent runs a distinct strategy and an
  aggregation layer resolves them into one weekly position.
- **[amazon-replica](https://github.com/aabolfadl/amazon-replica)** — an e-commerce backend
  run as a Kubernetes platform: six services over **polyglot persistence, ten datastores on six
  engines** (PostgreSQL ×5, MongoDB, Cassandra, Redis, Neo4j, Elasticsearch) plus RabbitMQ, all as
  StatefulSets, observed with Prometheus, Loki and Grafana. I built its **GitHub Actions CI/CD**
  (JUnit gate, parallel per-service Docker builds pushed to GHCR) and its **horizontal pod
  autoscaling**. Co-scrum master (one of two) for the 13-engineer team; full marks, shipped
  without an escalation.

---

## Everything else

The remaining repositories are mostly university coursework and early projects (an OS scheduler, a
Tomasulo simulator, a Haskell chess engine, an OpenGL game, a VHDL pet feeder, assorted web apps).
They're public for the record rather than as a portfolio. **The three projects at the top are the
ones that represent how I work now.**

---

## Reach me

📧 [ahmed.a.abolfadl@gmail.com](mailto:ahmed.a.abolfadl@gmail.com) ·
💼 [LinkedIn](https://www.linkedin.com/in/ahmed-abolfadl-bb640624b/)
