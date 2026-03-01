# LLM Selection Decision

| Decision Factor                 | My Choice | Reason (1 sentence) |
|---------------------------------|-----------|---------------------|
| Which LLM followed my prompt structure most faithfully? | Claude | It output exactly the requested headers and bullet points without adding unsolicited diagrams or breaking markdown formatting like ChatGPT and Gemini did [1-3]. |
| Which LLM was most technically accurate (least hallucination)? | Claude | It correctly identified internal Google tech like Borg, ScaNN, and Vizier, and strictly respected the definitions of the architectural layers, whereas Gemini blurred them by putting ML Ranking into the Deployment layer [4-6]. |
| Which LLM's output was most readable and well-organized? | Claude | Its clean separation of "What's happening", "Key technologies", and "Honesty checks" using the exact requested bullet points made it highly scannable [1, 4, 7]. |
| Which LLM handled the "honesty check" best (admitting when a layer doesn't apply)? | Claude | It provided excellent nuance, correctly noting that Layer 2 happens mostly offline and Layer 4 (LLMs) is purely supplementary rather than the core engine [4, 8]. |

**Selected LLM for final tool:** Claude
**Why:** Claude followed the constraints perfectly and provided the most senior-level engineering insights, such as identifying selection bias [4, 9]. It also strictly respected the boundaries of the six architectural layers, whereas the other models incorrectly bled machine learning concepts into the infrastructure and statistics layers [6, 10].
