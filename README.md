# StudioSync: Multi-LLM HITL System for Narrative Intelligence

A solo-built multi-LLM system for evaluating pitches vs. multi-studio reference docs with structured output, comparative benchmarking, batch processing, and human-in-the-loop integration.

---

## System Overview

- **Models**: Qwen3:8b, GPT-4o, Gemini 1.5 Pro, Claude 3.5 Sonnet
- **RAG Documents**: Studio Mandates from multiple studios, aligned with business goals  
- **Input Documents**: TV series pitches for potential programs with varied genres, target audiences, budgets, episode structures, etc.
- **Granular vs. Global Evaluation**: Pitches are transparently evaluated across clear scoring rubrics, with short score justifications, then human-designated section weights are applied, resulting in a final global score for each pitch according to each studio's reference mandate 
- **Model-agnostic** pipelines support easy model switching (local and API) with unified prompt engineering and configuration for all models
- **HITL integration** for applying variable weights to model evaluation output by section for customized scoring and ranking based on human-defined goals
- **Structured output parsing** for reliable scoring, structured weighting, dashboard display population, and metric comparisons
- **Batch processing** supports ranking pitch batches according to suitability based on the requirements of multiple studios 
- **Streamlit dashboard** enables easy HITL interaction, model transparency, weight adjustment, pitch loading, mandate loading, batch processing, and robust display 

---

## Generalizability

System structure, model transparency, evaluation methods, and HITL integration generalize any sector where priority alignment or resource allocation is key:

- Healthcare Operations
- Marketing Campaigns
- Business Proposals 
- Communication Guidelines
- Organization Policies

---

## System Features

| Feature                           | Description                                                           |
| --------------------------------- | --------------------------------------------------------------------- |
| **LLM-Agnostic Architecture**  | Local or API-hosted models all run through the same unified interface |
| **Batch Evaluations**          | Run all pitches across one or more studio mandates                 |
| **Model Comparison**           | Compare multiple models side-by-side on identical tasks               |
| **Weighted Scoring Engine**    | 8 evaluation categories with tunable weights                          |
| **Explainable Justifications** | Each score includes a concise rationale from the model                |
| **Interactive Dashboard**     | Streamlit UI with data export and visual comparison                   |
| **Extensible Design**          | Swap in fine-tuned, LoRA, or cloud API models with one line of config   |
| **Simple Input**              | Add new pitches, or studio mandates, for the system to use in evaluation |
---

## Basic Evaluation Output: Qwen3: 8B (Local Model) 

Basic text output using an effective, but relatively small, LLM model running on local hardware. Text generation is real-time, ~70 words per second with a reasoning time of ~5 seconds. Below is this model's evaluation output across various pitches.

<details>
<summary>Perfect Pitch - Bastion on the Endless Sea (Atmospheric Horror Pitch) vs. Studio Dark (Horror Studio Mandate)</summary>

This pitch was designed for perfect alignment with the business needs of Studio Dark, a mid-budget horror studio, across all elements of the rubric.

</details>

<details>
<summary>Good Pitch - Cleave Land: A Horror Rock Opera (Experimental Horror Pitch) vs. Studio Dark (Horror Studio Mandate)</summary>

This pitch was designed for excellent alignment with the business needs of Studio Dark. It fits most elements of the rubric perfectly. Its major deviations are that it is an experimental horror rock opera, relies heavily on gore as opposed to atmospheric horror tones, and requires a music licensing budget beyond what Studio Dark is typically comfortable with.

</details>

<details>
<summary>Decent Pitch - Carter Versus The Black Plague (Horror Adventure Comedy Pitch) vs. Studio Dark (Horror Studio Mandate)</summary>

This pitch was designed for decent alignment with the business needs of Studio Dark. It fits many elements of the scoring rubric. However, it is a synthesis of Mad Max, Robin Hood, and Ash vs. Evil Dead. It leans more towards light-hearted adventure, with comedy beats, and only a facade of horror elements. Additionally, it is set in the medieval era and requires extensive on location filming. Thus, the costume and location budget is much too high for Studio Dark, a mid-budget horror studio. 

</details>

<details>
<summary>Misaligned Drama Pitch - Wolf Mountain Divide (Prestige Drama Thriller Pitch) vs. Studio Dark (Horror Studio Mandate)</summary>

This is a well-constructed, solid pitch for Studio Prestige, a high-budget prestige drama studio. It is mostly inappropriate for Studio Dark, but some elements of the rubric align due to the morally ambiguous characters, slowly building dread, and thriller elements. However, the series requires recognizable, high-caliber talent, so the budget is much too high for Studio Dark.

</details>

<details>
<summary>Misaligned Comedy Pitch - Benchford University (Satirical Workplace Mockumentary Pitch) vs. Studio Dark (Horror Studio Mandate)</summary>

This is a well-constructed, solid pitch for Studio Fun, a low-budget comedy studio. However, it is completely inappropriate for Studio Dark. 

</details>

<details>
<summary>Boring Control Pitch - Grains of Truth: Competitive Sand Counting (Pitch) vs. Studio Dark (Horror Studio Mandate)</summary>

This is a control pitch, purposefully designed to align with the needs of no studio. A dry documentary on competitive sand counting with no creative angle, human interest depth, or clever subversion. It should appeal to practically no audience or studio. 

</details>

---

## Structured Evaluation Output: Qwen3: 8B (Local Model)

---

## 


## Tech Stack

| Component           | Technology                                                          |
| ------------------- | ------------------------------------------------------------------- |
| Frontend            | **Streamlit**                                                       |
| Core Logic          | **Python 3.11**                                                    |
| Model Orchestration | **Custom LLM_Interface Class**                                             |
| Local Inference     | **Ollama**                  					 |
| Local Models        | **Qwen3:8b**                  					 |
| Cloud APIs          | **GPT-4o, Gemini 1.5 Pro, Claude 3.5 Sonnet** |
| Data                | Markdown, CSV, JSON                             |
| Visualization       | Streamlit tables				                        |

---

## Future Enhancements

| **Stage**   | **Development Phase**                                          | **Focus & System Contribution**                                                                                                                                                                                                                                                                                                                |
| ----------- | -------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Stage 1** | **Early Development – Ideation & Pitching (Complete)**                    | The system evaluates pitches for alignment with studio priorities. It flags mismatches in tone, premise, audience targeting, and provides an appropriate score. <br><br>**System Value:** Studio alignment, submission readiness, tone/genre/audience cohesion.                                           |
| **Stage 2** | **Mid Development – Writers’ Room & Series Design**            | Writers expand on the concept with character bibles, episode plans, and episode outlines. The system ensures internal consistency, character motivation, world rules, and structure. <br><br>**System Value:** Cross-doc consistency, dynamic role tracking, pilot structure analysis, creative rule enforcement.                              |
| **Stage 3** | **Late Development – Drafts & Season-Level Cohesion**          | With a full season arc emerging, the system checks for arc progression, setup/payoff resolution, tonal drift, and emerging redundancies. Initial drafts are stress-tested for alignment and depth. <br><br>**System Value:** Season-level evaluation, redundancy detection, thematic cohesion, relationship development.                           |
| **Stage 4** | **Finalization – Table Reads & Locked Scripts**                | StudioSync helps track changes during finalization. As late-stage rewrites, table read feedback, and scene swaps occur, the system checks for unintended narrative damage (e.g., dropped setups or tonal mismatches). <br><br>**System Value:** Regression detection, script polishing support, dialogue-level feedback, micro-iteration. |
| **Stage 5** | **Season 2 & Beyond – Narrative Continuity & Future Planning** | StudioSync surfaces unresolved threads, long-term growth potential, and timeline conflicts to support new season planning. Past materials act as high-fidelity memory to inform future drafts. <br><br>**System Value:** Continuity recall, multi-season arc tracking, future-proofing, opportunity discovery. 

---

## Connect & Contact

Available for live walkthroughs, Q&A, and technical deep dives on this project.

**Jeffrey Robert Lynch** [LinkedIn](https://www.linkedin.com/in/jeffrey-lynch-350930348)

(Demo access, source code discussions, and use-case exploration available upon request.)

