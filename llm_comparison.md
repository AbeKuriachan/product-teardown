# LLM Comparison — Product Teardown: YouTube Recommendation Feed

## Models Used
| # | LLM Name | Mode (Fast/Standard/Thinking) |
|---|----------|-------------------------------|
| 1 | Claude | Standard 
| 2 | ChatGPT | Standard 
| 3 | Gemini | Standard 

## Layer-by-Layer Comparison

### Layer 1: Data Foundation
| Criteria | Claude | ChatGPT | Gemini | Best? |
|--------------------|--------|--------|--------|-------|
| Specificity (1-5) | 5 | 4 | 4 | Claude |
| Named real tech? | Y (Kafka, BigQuery, Spanner) | Y (Colossus, Beam) | Y (Vitess, Bigtable) | |
| Identified a real engineering challenge? | Y (Low-latency vs long-term) | Y (Exabyte-scale logs) | Y (Petabytes consistency) | |
| Notes: | Claude provided the clearest engineering tradeoff between recent history latency and long-term preference querying. | ChatGPT listed good tech but formatting was slightly messy. | Gemini's mention of Vitess and Bigtable was highly accurate for Google. |

### Layer 2: Statistics & Analysis
| Criteria | Claude | ChatGPT | Gemini | Best? |
|--------------------|--------|--------|--------|-------|
| Specificity (1-5) | 5 | 4 | 3 | Claude |
| Named real tech? | Y (Google Vizier) | N (Generic frameworks) | Y (Beam, Flink, TFX) | |
| Identified a real engineering challenge? | Y (Selection bias/Feedback loops) | Y (Correlation vs causation) | Y (Data drift) | |
| Notes: | Claude brilliantly identified "Selection Bias" (users only see recommended videos) which is the exact right answer here. | Solid concepts, but lacked specific tool names. | Gemini mixed Layer 1/5 tools (Beam, TFX) into the Statistics layer. |

### Layer 3: Machine Learning Models
| Criteria | Claude | ChatGPT | Gemini | Best? |
|--------------------|--------|--------|--------|-------|
| Specificity (1-5) | 5 | 4 | 5 | Tie (Claude/Gemini) |
| Named real tech? | Y (ScaNN, TF) | Y (TF) | Y (ScaNN, Vertex AI) | |
| Named model family?| Y (Two-stage, Wide & Deep) | Y (Two-tower) | Y (Two-tower ANN) | |
| Identified a real engineering challenge? | Y (Cold start, multi-task) | Y (Long-term vs clicks) | Y (Cold start) | |
| Notes: | Both Claude and Gemini accurately described the Two-Stage/Two-Tower ANN architecture using ScaNN. | Good, but slightly less detailed on the retrieval mechanism. | Excellent technical specificity. |

### Layer 4: LLM / Generative AI
| Criteria | Claude | ChatGPT | Gemini | Best? |
|--------------------|--------|--------|--------|-------|
| Specificity (1-5) | 4 | 3 | 4 | Claude |
| Honest if not applicable? | Y | Y | Y | |
| Notes: | Perfectly explained that LLMs are supplementary (metadata/transcripts), not the core engine. | Admitted LLMs are not the core, but lacked specific tooling. | Good mention of safety filtering and Gemini-Flash. |

### Layer 5: Deployment & Infrastructure
| Criteria | Claude | ChatGPT | Gemini | Best? |
|--------------------|--------|--------|--------|-------|
| Specificity (1-5) | 5 | 4 | 2 | Claude |
| Named real tech? | Y (TF Serving, Borg, TPUs) | Y (TF Serving, Borg) | Y (K8s, TF Serving) | |
| Notes: | Nailed the latency budget (<100ms) and canary rollouts. | Good tech named, but less specific on the challenge. | Gemini incorrectly placed the "Ranking Stage" (Layer 3/4 ML concepts) into this infrastructure layer. |

### Layer 6: System Design & Scale
| Criteria | Claude | ChatGPT | Gemini | Best? |
|--------------------|--------|--------|--------|-------|
| Specificity (1-5) | 5 | 3 | 2 | Claude |
| Named real tech? | Y (GKE, Redis/Bigtable) | Y (CDN) | Y (gRPC, Go) | |
| Notes: | Identified the exact system challenge: cross-surface consistency (Home vs Shorts). | Very generic (CDN, caching). | Again, Gemini mixed up layers, putting UI logic/Re-ranking here instead of global scale infrastructure. |

## Overall Verdict
| Dimension | Winner (LLM #) | Why? (1 sentence) |
|------------------------------------|-----------------|--------------------------|
| Most technically specific overall | Claude | Consistently named internal Google/YouTube tools (Borg, ScaNN, Vizier) and precise architectural setups. |
| Best at naming real technologies | Claude | Provided the most accurate stack mapping (Kafka -> BigQuery -> ScaNN -> TF Serving). |
| Least hallucination / made-up info | Claude | Gemini hallucinates the boundaries of the layers, bleeding ML ranking into infrastructure. |
| Best at "hardest problem" insight | Claude | Highlighting "selection bias" in Layer 2 and "cross-surface consistency" in Layer 6 were senior-level insights. |
| Best structured output | Claude | Followed the requested prompt format flawlessly without breaking markdown. |
| Fastest useful response | N/A | (Run times were not recorded in the text) |

## Key Observation
> One thing I noticed about how different LLMs handle the same prompt:
> While all three models understood the basic ML concepts, Gemini struggled significantly to respect the boundaries of the 6 layers, placing ML Ranking into Deployment and UI logic into System Design. Claude was the only model that strictly obeyed the layer definitions while providing bleeding-edge technical specificity and non-obvious engineering challenges like selection bias.
