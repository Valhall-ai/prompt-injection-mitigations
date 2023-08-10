# Prompt Injection Mitigations

A collection of prompt injection mitigation techniques.

---
# Mitigation Categories

These are not mutually exclusive, meaning one technique can fit into multiple categories of mitigation.

## Disruption

Disruption mitigation techniques deteriorate the attacker's ability to control output state, so that even if the attacker succeeds in subverting the prompt's intended output limitations, the subverted state is less useful to the attacker.

**Reliability:** Exploits that sometimes succeed but fail to work reliably can be undesireable for attackers who wish to avoid failures which might alert defenders to the attack prematurely. Dynamically generated mitigation strategies (per-session) could make it exceptionally difficult to achieve reliable subversion.

**Control:** If injection does achieve some manner of subversion but the outcome isn’t controlled (because of mitigations) the attacker’s desired target state may not be within reach.

## Sanitization

Sanitization mitigation techniques deteriorate the attacker's ability to control the input state, making the likelihood of successful subversion lower. 

**Input:** If the attacker’s input is affected in such a way that certain characters or patterns required for the injection technique never reach any LLM (for example, identification via Regex, traditional NLP, or other code), the attack may fail.

**Intermediate I/O:** Input sanitization, but applied to a multi-step process. Many LLM use-cases involve multi-step processing of text. If output (soon to be next-stage input) is sanitized in some way, this could make it more difficult to achieve the input state necessary to subvert the *next* LLM output in the process.


