# 🛡️ Prompt Injection Mitigations
A collection of prompt injection mitigation techniques.

---

# 🏷️ Mitigation Categories
It's useful to break down technique traits into categories to better understand how each technique is interacting with the threat as well as the time and cost trade-offs involved.

## 🔁 Active vs 🚦 Passive
Active mitigation techniques involve proactive steps to neutralize a potential attack whereas passive techniques block attacks by simply not allowing them to proceed.

## 🛡️ Preventive vs ⚠️ Reactive
Preventive techniques try to stop an attack before it occurs while reactive techniques respond to an attack after it has happened, mitigating the impacts.

## 🧠 Predictive vs 🪂 Responsive
Predictive techniques rely on modeling and forecasting to spot and stop potential attacks whereas responsive methods respond to a detected threat.

## 📥 Input-focused vs 📤 Output-focused
Input-focused techniques seek to sanitize or control the input to prevent malicious use while output-focused techniques focus on turning manipulated outputs into less valuable ones for attackers.

## 🌐 Generic vs 🔬 Specific
Generic techniques can be applied broadly to tackle different types of attacks while specific techniques specialize in thwarting a particular type of attack.

## 🤖 Automated vs 👥 Manual
Automated mitigation is driven by algorithms and code with little to no human intervention whereas manual mitigation techniques require human intervention, interpretation, or analysis.

---

# Techniques

## 💬 Paraphrasing
Ask an LLM to paraphrase the prompt while retaining as much detail as possible. 
`🔁 Active` `⚠️ Reactive` `📤 Output-focused` `🌐 Generic` `🤖 Automated`

---

## 🕵️‍♂️ Threat Intel Driven Sanitization
Based on threat intel, write code or Regex patterns that match known injection techniques and remove them from the prompt.
`🔁 Active` `🛡️ Preventive` `📥 Input-focused` `🔬 Specific` `🤖 Automated`

---

## 🧬 Mutation & Repair
Randomly remove characters from the input prompt and use an LLM to correct any errors in the text, presuming potential loss of injection-related details.
`🔁 Active` `🛡️ Preventive` `📥 Input-focused` `🌐 Generic` `🤖 Automated`

---

## 🔍 Relevance Filtering
Use an LLM to divide up the content of the prompt into a list of essential details, filtering out irrelevant ones. 
`🔁 Active` `⚠️ Reactive` `📥 Input-focused` `🌐 Generic` `🤖 Automated`

---

## 🚧 Type Enforcement
Validate a strict output format for the LLM prompt, ensuring a specific output format thereby eliminating many loopholes for potential attacks. 
`🚦 Passive` `🛡️ Preventive` `📤 Output-focused` `🔬 Specific` `👥 Manual`

---

## 🎯 Fine-tuned or RAG-assisted Injection Characterization
An LLM prompt containing information about common injection methods can aid in identifying signs of these techniques. 
`🔁 Active` `🧠 Predictive` `📤 Output-focused` `🔬 Specific` `👥 Manual`

---

## 🌈 Model Diversification
Introduce diversity by incorporating different LLM models, and reject the prompt or retry until the outputs are similar. 
`🔁 Active` `⚠️ Reactive` `📤 Output-focused` `🌐 Generic` `🤖 Automated`
