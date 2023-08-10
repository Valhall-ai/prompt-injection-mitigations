# :shield: Prompt Injection Mitigations

A collection of prompt injection mitigation techniques.

---

# :file_folder: Mitigation Categories

These are not mutually exclusive, meaning one technique can fit into multiple categories of mitigation.

## :exploding_head: Disruption

Disruption mitigation techniques deteriorate the attacker's ability to control output state, so that even if the attacker succeeds in subverting the prompt's intended output limitations, the subverted state is less useful to the attacker.

📜**Reliability:** Exploits that sometimes succeed but fail to work reliably can be undesireable for attackers who wish to avoid failures which might alert defenders to the attack prematurely. Dynamically generated mitigation strategies (per-session) could make it exceptionally difficult to achieve reliable subversion.

🎮**Control:** If injection does achieve some manner of subversion but the outcome isn’t controlled (because of mitigations) the attacker’s desired target state may not be within reach.

## 🧽 Sanitization

Sanitization mitigation techniques deteriorate the attacker's ability to control the input state, making the likelihood of successful subversion lower. 

🔎**Input:** If the attacker’s input is affected in such a way that certain characters or patterns required for the injection technique never reach any LLM (for example, identification via Regex, traditional NLP, or other code), the attack may fail.

↗️**Intermediate I/O:** Input sanitization, but applied to a multi-step process. Many LLM use-cases involve multi-step processing of text. If output (soon to be next-stage input) is sanitized in some way, this could make it more difficult to achieve the input state necessary to subvert the *next* LLM output in the process.

> <:exploding_head: Disruption> <:sanitization: Sanitization>

## :arrows_counterclockwise: Paraphrasing

Ask an LLM to paraphrase the prompt while retaining as much detail as possible. Although the injection attack may attempt to trick the paraphrasing step into echoing the initial message, the sophistication required for this could potentially conflict with any subsequent injection strategies.

> <:exploding_head: Disruption> <:sanitization: Sanitization>

---

## :cloud_with_lightning: Threat Intel Driven Sanitization

Based on threat intel, write code or Regex patterns that match known injection techniques. Upon detection of matching strings, remove them from the prompt. We should not indicate to the user that the injection has been mitigated as this information could potentially aid attackers.

> <:sanitization: Sanitization>

---

## :dna: Mutation & Repair

Randomly remove characters from the input prompt and use an LLM to correct any errors in the text. Repeat this process N times. Start this process in parallel multiple times. After sufficient iterations, the repaired portions of a prompt might lose any obscure, likely-to-be injection-related details.

> <:exploding_head: Disruption>

---

## :mag_right: Relevance Filtering

Use an LLM to divide up the content of the prompt into a list of details and elucidate its relevance. Filter the elements deemed irrelevant and optionally, confirm whether removing the item would alter the prompt's meaning. The resulting cleaned prompt is effectively a more robust version of the initial one. Applying several layers of these techniques could significantly complicate the task of potential attackers.

> <:exploding_head: Disruption> <:sanitization: Sanitization>

---

## :lock: Type Enforcement

In some cases, we can validate a strict output format for the LLM prompt. Prompt injection attacks often aim to yield remote code execution. Therefore, ensuring a specific output format eliminates many loopholes for potential attackers and limits the attack vectors. 

This technique is particularly useful when translating LLM outputs based on untrusted or tainted inputs into sensitive actions like API calls and commands.

> <:exploding_head: Disruption> <:sanitization: Sanitization>

---

## :dart: Fine-tuned or RAG-assisted Injection Characterization

An LLM prompt containing information about common prompt injection methods can aid in identifying signs of these techniques. Using Retrieval Augmented Generation (RAG) or models fine-tuned for particular techniques can enhance this process. 

> <:sanitization: Sanitization>

---

## :earth_americas: Model Diversification

Introduce diversity by incorporating different LLM models. If two models provide diametrically opposite outputs in sentiment analysis, we can consider rejecting the prompt or retrying until the outputs are similar. This technique can work as a mitigation layer or to improve the other mitigation layers.

> <:exploding_head: Disruption> <:sanitization: Sanitization>
