# Best-Parts Map

| Layer | Best LLM for This Layer | What to Extract (copy the key paragraph/section) |
|-------|------------------------|--------------------------------------------------|
| Layer 1: Data Foundation | Claude | "Maintaining low-latency access to a user's recent history while querying long-term preference signals." |
| Layer 2: Statistics & Analysis | Claude | "Selection bias — users only see recommended videos, so observed engagement is not a random sample. Correcting for this to avoid feedback loops is non-trivial." |
| Layer 3: ML Models | Gemini / Claude | "Candidate Generation — a neural network retrieves ~100–500 videos from millions using approximate nearest neighbor search (ScaNN) on learned embeddings." |
| Layer 4: LLM / Generative AI | Claude | "Honesty check: LLMs are supplementary, not the recommendation engine itself. The core ranking is classical deep learning." |
| Layer 5: Deployment & Infra | Claude | "Model freshness — retraining and deploying updated ranking models frequently without downtime or quality regression." |
| Layer 6: System Design & Scale | Claude | "Consistency — a video deduplication filter needs to know what was shown across multiple surfaces (Home, Shorts, Up Next) in real time." |
| Overall Analysis / Hardest Problem| Gemini | "If the retrieval layer fails to find the right 400 videos from the 10-billion-video haystack, the most expensive Ranker in the world will still only show you garbage." |
| Writing Style / Structure | Claude | Strict adherence to the requested headers, bullet points, and formatting structure. |
