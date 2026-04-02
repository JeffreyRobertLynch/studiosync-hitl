# StudioSync: LLM Decision Support & Evaluation System

## Executive Summary
StudioSync is a **model-agnostic, multi-rubric LLM system** designed to evaluate custom batches of input documents (pitches) vs. policy documents (mandates), providing multi-criteria scores reflecting alignment with business priority rubrics. The system automates screening, ranking, and routing proposal batches to end users where business needs align. Due to the model-agnostic architecture, StudioSync also functions as an automated utility for deriving metrics from various A/B tests. 

StudioSync has been tested with a variety of local (Qwen, GPT, Gemma, Deepseek, Llama) and cloud (GPT, Gemini, Claude) models. Model Qwen3:8b will be used throughout this demo for cohesion and to show how well smaller, cost-effective models can perform on complex but discrete tasks with appropriate scaffolding. Qwen3:8b is known to perform well within this system as it was the primary model used for development and testing to reduce costs.

A sanitized dataset and use case are provided for demo. The dataset is small (10 TV show pitches and 3 Studio mandates) but complex, feature-rich, and designed to provide a suitable demonstration. 

---

## Custom Batch UI - 10 Model x 10 Pitch x 3 Studio Mandate x 8 Adjustable Section Weights

![Batch Builder](output/batch_builder.png)

![HITL Weights](output/hitl_weights.png)

---

## System Overview

- **Model-Agnostism:** Local (Qwen3, GPT, Gemma, Deepseek, Llama) and cloud-based (GPT, Gemini, Claude) LLMs supported.
- **Leaderboard Population:** Ingestion -> Custom Batch -> Batch Inference -> Model Output -> JSON Parsing -> Weight Application -> CSV Parsing -> Final Leaderboard Display.
- **Model Output Parsing:** The system enforces a JSON schema for model output with error handling and resend/retry logic. 
- **Auditing:** Raw model output is saved prior to weight application to preserve output at time of inference and can be viewed in UI.
- **Tracing:** A Run Manager wraps the entire process, embedding run metadata into all documents and model outputs for deriving metrics and reproducibility.
- **Streamlit Interface:** Enables ingestion, running custom batches, section weight adjustments, leaderboard display, and viewing raw model output with metadata.
- **Test Support:** The system's flexibility, structure, auditing, and tracing support deriving metrics from A/B Testing: Counterfactual, Superlative Stuffing, Doc Format/Version, Model Config, Prompt, etc.

---

## Generalizability

Highly Generalizable to other sectors where **priority alignment** or **resource allocation** is key, including:

- **Legal Documents**
- **Healthcare Operations**
- **Marketing Campaigns**
- **Business Proposals** 
- **Brand Communication Guidelines**
- **Organization Policies**
- **Manufacturing Processes**
- **Team-building & Skills Coverage**

---

## Use Case: Document Design

The pitch set consists of **10 high-quality TV show pitches**, carefully designed to isolate alignment with specific mandates rather than overall quality. 

No pitch is "bad", but each is designed to adhere to a **specific genre/sub-genre**. Each is well-defined and many are experimental, odd genre mashups, or niche. This creates **one perfect/near-perfect fit per studio** (A-Tier), **two curve balls per studio** that intentionally violate key studio priorities (B-Tier and C-Tier), and one **universal control pitch** (Control_F) that **strongly misaligns with the business needs of all 3 studios**. 

Each pitch is evaluated across **3 distinct studio mandates** with **highly divergent priorities** and **deviation tolerances**.

---

<details>
<summary>
  
**Studio Mandate Summaries (Click to Expand)**

</summary>

| Studio     | Base Genre      | Budget Category | Production Timeline | Episode Length | Season Length | Additional Priorities |
| ---------- | --------------- | --------------- | --------------- | ------------ | ------------ | ------------ |
| Studio Dark     | Horror      | Mid             | Mid | Mid | Short | No comedy-horror, slasher, gorefest, monster of the week, or true story human exploitation; Rich world-building & mythology; horror-aligned themes & symbolism |
| Studio Fun      | Comedy       | Low             | Fast | Short | Long | Formulaic episode structure; merchandising opportunities; minimal sets; character-driven humor; repeatable gags; younger audience |
| Studio Prestige | Drama        | High            | Slow | Long | Mid | Open to cross-genre; experimental over formulaic; character depth; cinematic quality; A-list talent required; older audience |

</details>

---

<details>
<summary>

**Pitch Summaries (Click to Expand)**

</summary>

| Pitch Name | Sub-Genre           | Title          | Summary/Logline |
| ---------- | --------------- | ------------- | --------------- |
| Comedy_A   | Ensemble Sitcom | Gigged Out    | Six gig-workers with dubious skills, all strangers, pool their resources to lease a shared office space but are mistaken for a legit consulting firm. **The Office** meets **Three's Company** with more incompetence. |
| Comedy_B   | Cynical Mockumentary | Benchford University  | Six professors at a low prestige university enact schemes to advance their careers while scheming to prevent rivals from advancing their own careers. **Parks & Recreation** meets **A.P. Bio** with a card battling system. |
| Comedy_C   | Absurdist Animation   | The Breakfast Brigade  | The "Breakfast Brigade", an international paramilitary team of anthropomorphic breakfast foods, fight to protect breakfast from the villainous group, "The Process". **G.I. Joe** meets **Archer** with more food puns. |
| Control_F  | Sport Academia        | Grains of Truth: Competitive Sand Counting | A sincere attempt to capture the niche academic sport of competitive sand counting as never seen before on TV. **C-Span** meets **Dry Instructional Films** with coarse, rough, irritating sand that gets everywhere. | 
| Drama_A    | Political Thriller    | Wolf Mountain Divide | A retired city lawyer, now mayor of a remote Appalachian town, reawakens her ambition when a corporation sets their sights on her domain. **Succession** meets **Yellowstone** with Kathy Bates and Toby Maguire. |
| Drama_B    | Social Realism Dance           | Westville Backup | Three third-tier backup dancers support each other while working mundane day jobs, striving for the chance to catch an occasional glimpse of the spotlight. **Fame** meets **Euphoria** with more duality. |
| Drama_C    | Period Crime Romance          | Bluefield Cycle    | In the 90s, a failed competitive cyclist and her mechanic boyfriend embark on a thrilling crime spree, with a predictably tragic resolution. **The Basketball Diaries** meets **Halt and Catch Fire** with cycling crimes. |
| Horror_A   | Supernatural Psychological     | Bastion on the Endless Sea | The crew of a fishing vessel, lost at sea, find themselves adrift in a liminal space where they encounter ghosts of the past and maritime myths. **The Terror** meets **Lost** with descent into maritime madness. |
| Horror_B   | Western Rock Opera        | Cleave Land: A Post-Apocalyptic Rock Opera | Daisy and her companions brave raiders, monsters, and the post-apocalyptic Dust Bowl to reach the fabled Great Lakes and civilization. **Bone Tomahawk** meets **Fallout** with Ferrymen slinging power ballads. |
| Horror_C   | Dark Fantasy Adventure | Carter vs. the Black Plague  | Carter and his band of righteous outlaws defy the odds, and the law, to distribute a cure across a medieval world plagued by monsters and corruption. **Robin Hood** meets **Ash vs. Evil Dead** with a road-trip vibe. |

</details>

---

## Generalizability

Highly Generalizable to other sectors where **priority alignment** or **resource allocation** is key, including:

- **Legal Documents**
- **Healthcare Operations**
- **Marketing Campaigns**
- **Business Proposals** 
- **Brand Communication Guidelines**
- **Organization Policies**
- **Manufacturing Processes**
- **Team-building & Skills Coverage**

---

## Use Case: Results

Qwen3:8 performs admirably on this task. Scoring changes slightly across runs, but Qwen3:8b reliably ranks all pitches in order according to their respective genre studio across 10 runs.

- A, B, and C pitches are appropriately ranked relative to each studio's priorities. 
- **Pitch: Control_F_Sport_Academia** is appropriately ranked very low for all three studios.
- Text justifications provide excellent context and **references relevant studio mandate sections specifically**.
- **Objective quantitative metrics** (Budget, Production Timeline, Episode Count, Episode Length, Primary Cast Size, etc.) are **referenced and judged accurately**, with **one minor exception** out of 30 inferences. This could potentially be remedied by revisiting prompt engineering or doc structure.
- **Subjective qualitative metrics** (Sub-Genre, Cross-Genre, Tone, Style Influences, Premise, Themes, etc.) are **referenced and judged accurately**, though not penalized harshly enough in some cases. This could potentially be remedied by revisiting prompt engineering or doc structure.
- Even more interesting, the evaluation of misaligned genre pitches (Comedy Pitch vs Horror Studio Mandate, et al.) is **nuanced and accurate**. Studio Prestige (Drama) and Studio Dark (Horror) have no interest in formulaic comedy pitches, even if well-constructed. **Scoring here is highly appropriate**.
- Likewise, Studio Prestige (Drama) and Studio Dark (Horror) have many **overlapping priorities** (darker tone, strong themes, symbolism, world-building, etc.). It is **perfectly appropriate** that **Pitch: Horror_B_Western_Rock_Opera (an experimental premise with a unique artistic vision)** scores highly with both **Studio Dark** (for horror mythos, originality, world-building, strong themes, budget, etc.) and **Studio Prestige** (for originality, world-building, strong themes, experimental storytelling, unique artistic vision, etc.).
- Further, **Pitch: Horror_C_DarkFantasy_Adventure (a wide genre mashup of horror, adventure, action, fantasy, and comedy)** is the highest-scoring non-comedy pitch with **Studio Fun**. This is also **perfectly appropriate** because this pitch contains the most comedy beats outside of the three dedicated comedy pitches.   

---

## Batch Run & Leaderboard Results - Qwen3:8b - 3 Mandates - 10 Pitches - Default Section Weights

Processing this batch **(1 model x 3 mandate x 10 pitches x default section weights)** takes **~7 minutes** on **modest hardware (single RTX 4080 GPU/16 GB VRAM**). It produces **3 CSV files**, one for each **1 model x 1 mandate x 10 pitch** grouping, for comparative display. It also generates **30 separate JSON files** **(1 model x 1 mandate x 1 pitch)** of raw model scores and text justifications, pre-HITL weighting, for display and full transparency. 

---

<details>
<summary>
  
**Visuals - Batch Builder, HITL Weights, and Leaderboard Results (Click to Expand)**

</summary>
  
### Batch Builder

Build a batch with any combination of models, mandates, pitches, and section weights.

![Batch Builder](output/batch_run_qwen38b_3x10.png)

---

### HITL Weights

Fully adjustable section weighting via sliders.

![HITL Weights](output/hitl_weights.png)

---

### Leaderboard Results

Clear display of pitch rankings for every model x mandate pairing with HITL section weights applied to raw model output.

![Leaderboard Results](output/leaderboard_qwen38b_3x10.png)

</details>

---

## Raw Model Output with Scoring Justification

Raw model output is parsed into JSON and saved before applying HITL weights. These files can be retrieved for easy human-readable display within the dashboard. The default token limit for a model's raw scoring and text justifications is 512 tokens, but this can be adjusted. A smaller token limit can speed up batch processing considerably if the user does not need the section-by-section text justifications. A larger token limit can offer more context for the model's decisions, and allow the model to fully expound on how the pitch aligns or misaligns with each section of the studio mandate.

---

<details>
<summary>

**Visuals - Studio Dark - Horror A, B, C (Click to Expand)**

</summary>

---

### Qwen3:8b - Horror A - Supernatural Psychological - Bastion on the Endless Sea

![Bastion on the Endless Sea](output/qwen38b_dark_horror_A.png)

---

### Qwen3:8b - Horror B - Western Rock Opera - Cleave Land: A Post-Apocalyptic Rock Opera

![Cleave Land: A Post-Apocalyptic Rock Opera](output/qwen38b_dark_horror_B.png)

---

### Qwen3:8b - Horror C - Dark Fantasy Adventure - Carter vs. the Black Plague

![Carter vs. the Black Plague](output/qwen38b_dark_horror_C.png)

</details>

---

<details>
<summary>
  
**Visuals - Studio Fun - Comedy A, B, C (Click to Expand)**

</summary>

### Qwen3:8b - Comedy A - Ensemble Sitcom - Gigged Out

![Gigged Out](output/qwen38b_fun_comedy_A.png)

---

### Qwen3:8b - Comedy B - Cynical Mockumentary - Benchford University

![Benchford University](output/qwen38b_fun_comedy_B.png)

---

### Qwen3:8b - Comedy C - Absurdist Animation - The Breakfast Brigade

![The Breakfast Brigade](output/qwen38b_fun_comedy_C.png)

</details>

---

<details>
<summary>
  
**Visuals - Studio Prestige - Drama A, B, C (Click to Expand)**

</summary>

### Qwen3:8b - Drama A - Political Thriller - Wolf Mountain Divide

![Wolf Mountain Divide](output/qwen38b_prestige_drama_A.png)

---

### Qwen3:8b - Drama B - Social Realism Dance - Westville Backup

![Westville Backup](output/qwen38b_prestige_drama_B.png)

---

### Qwen3:8b - Drama C - Period Crime Romance - Bluefield Cycle

![Bluefield Cycle](output/qwen38b_prestige_drama_C.png)

</details>

---

## Future Enhancements

- To better support automated benchmarking and derive comparative performance metrics, the Run Manager's metadata embedding should be revisited to add relevant info.
- A system for tracking groups of looped runs should be established for tracking variation over multiple run iterations. Run queues would also be a useful addition.
- The system currently supports A/B testing, but adding an additional interface to display this in UI would be beneficial, like the JSON viewer, instead of extracting values embedded in files.
- A RAG system is under development downstream of evaluation. This would support routing pitches to appropriate studios. If a scoring threshold is achieved relative to a studio, the pitch passes through a quality gate and becomes part of a multi-tenant vector DB. Afterwards, each studio's chatbot can answer queries about pitches relevant to their business needs.   

---

## Connect & Contact

Available for live walkthroughs, Q&A, and technical deep dives on this project.

**Jeffrey Robert Lynch** [LinkedIn](https://www.linkedin.com/in/jeffrey-lynch-350930348)

(Demo access, source code discussions, and use-case exploration available upon request.)

---

## License

© 2025 Jeffrey Robert Lynch

This project, including all source code, documentation, and related materials, is provided strictly for personal, educational, and portfolio review purposes.

No part of this codebase may be copied, modified, distributed, published, or used for commercial purposes without the author's explicit written permission.

All rights are reserved by the author. No licenses or permissions are granted beyond personal, non-commercial viewing.

