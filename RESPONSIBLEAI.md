# Responsible AI Framework

Canada Works implements a "Safety-First" AI pipeline designed to mitigate bias, hallucination, and opacity in public sector applications.

## 1. Prompt Engineering Guardrails
The following system constraints are injected into every API call to ensure the model adheres to public sector standards:

### A. Gender Neutrality
> **Rule:** "Strictly use gender-neutral language (e.g., use 'they/them' or 'the candidate' instead of 'he/she')."
> *Reasoning:* Mitigates historical gender bias present in legacy job descriptions (e.g., changing "Draftsman" to "Drafter", or "Chairman" to "Chairperson").

### B. Anti-Hallucination
> **Rule:** "Use ONLY information explicitly present in the input text. Do NOT invent responsibilities or benefits."
> *Reasoning:* Prevents the AI from "selling" a job by adding perks or duties that do not exist in the official source text.

### C. Tone Policing
> **Rule:** "Maintain a neutral, factual tone. Avoid promotional language (no 'exciting opportunity', 'great role')."
> *Reasoning:* Ensures government data remains objective and accessible, removing marketing fluff.

## 2. Literacy & Inclusion
The system is designed to translate complexity for diverse audiences. Instead of a single summary, we generate three distinct output tiers:
* **ESL (Grade 5-6):** Short sentences, no idioms. (Tested against Flesch-Kincaid scale).
* **Standard (Grade 8):** General public reading level.
* **Advanced:** Preserves technical jargon for subject matter experts and policy analysts.

## 3. Transparency & Explainability
The application moves beyond the "Black Box" paradigm by implementing a **"Glass Box" User Interface**, ensuring that every AI-generated insight is auditable by the user.

### A. The "How This Was Made" Panel
Every job card includes an expandable telemetry panel that exposes the internal logic of the generation:
* **Full Prompt Disclosure:** Users can view the exact system instructions sent to the LLM (e.g., seeing the specific rules for "Gender Neutrality" or "Reading Level"). This allows policy analysts to audit the AI's instructions for bias.
* **Model & Versioning:** Explicitly lists the model used (e.g., `gpt-4o`) and the timestamp, ensuring accountability for model-specific behaviors.
* **Safety Status Indicators:** A status indicator (Green/Red) explicitly confirms whether the content triggered any Azure AI Content Safety filters (Hate/Self-Harm/Violence) during generation.

### B. Source Anchoring (Anti-Hallucination)
AI insights are strictly coupled with their primary sources. The system never presents a legislative connection without a citation:
* **Legislative Context:** Vector-matched debates include the specific **Committee Name**, **Meeting Number**, and **Session Date** (e.g., *"Source: ENVI Meeting No. 12"*), allowing users to verify the transcript.
* **Territorial Data:** Traditional territory overlays are accompanied by a strictly worded disclaimer regarding legal boundaries, with direct attribution to **Native Land Digital**.

### C. The "Original Source" Toggle
To prevent over-reliance on AI summarization, the interface defaults to the summary but provides a **single-click toggle** to revert the view to the raw, unaltered Job Bank description. This ensures the original government data remains the "Source of Truth."
