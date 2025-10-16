# Prompt Engineering Techniques: A Technical Guide

## Table of Contents
- [Introduction](#introduction)
- [Zero-Shot Prompting](#zero-shot-prompting)
- [Few-Shot Prompting](#few-shot-prompting)
- [Chain-of-Thought Prompting](#chain-of-thought-prompting)
- [Role Prompting](#role-prompting)
- [Self-Consistency Prompting](#self-consistency-prompting)
- [Reflexion / Critique Prompting](#reflexion--critique-prompting)
- [Conclusion](#conclusion)
- [References](#references)

---

## Introduction
Prompt engineering is the craft of designing prompts to elicit desired behavior from large language models (LLMs). Advanced users leverage various techniques to improve model performance on different tasks, especially as raw instructions may not always yield the best results. This guide covers several key prompt engineering techniques – **Zero-Shot**, **Few-Shot**, **Chain-of-Thought**, **Role Prompting**, **Self-Consistency**, and **Reflexion/Critique** prompting – explaining how they work and when to use them. Each technique is illustrated with explanations and examples to help experienced users refine their prompts for optimal results.

---

## Zero-Shot Prompting
Zero-shot prompting is the simplest approach: you give the model a direct instruction to perform a task **without providing any examples**.

**Example:**
```text
Prompt: "Classify the sentiment of the following text as positive, negative, or neutral.
Text: I think the vacation was okay.
Sentiment:"
````

**Output:**

```text
Neutral
```

✅ Use cases: common NLP tasks, straightforward classification, text summarization
⚠️ Limitations: often fails on complex or ambiguous tasks without guidance

---

## Few-Shot Prompting

Few-shot prompting improves performance by providing **input-output examples** in the prompt before the actual query.

**Example:**

```text
A "whatpu" is a small, furry animal native to Tanzania.
An example of a sentence that uses the word "whatpu" is:
We were traveling in Africa and we saw these very cute whatpus.

To do a "farduddle" means to jump up and down really fast.
An example of a sentence that uses the word "farduddle" is:
```

**Output:**

```text
When we won the game, we all started to farduddle in celebration.
```

✅ Use cases: structured outputs, uncommon tasks, custom formatting
⚠️ Limitations: prompt length grows with more examples; example choice is critical

---

## Chain-of-Thought Prompting

Chain-of-Thought (CoT) prompting encourages the model to **generate intermediate reasoning steps**.

**Example (Zero-shot CoT):**

```text
I have 3 apples and buy 5 more, then give away 2. How many apples do I have left?
Let’s think step by step.
```

**Output:**

```text
First, you start with 3 apples. You buy 5 more, so 3 + 5 = 8.
Then you give away 2, so 8 - 2 = 6.
Answer: 6
```

✅ Use cases: arithmetic, logical reasoning, multi-hop QA
⚠️ Limitations: smaller models may hallucinate steps; works best on large LLMs

---

## Role Prompting

Role prompting instructs the model to **adopt a persona or point of view** to guide tone, depth, and style.

**Example:**

```text
You are an experienced software engineer. Explain how a blockchain works.
```

✅ Use cases: domain-specific explanations, stylistic control, roleplay
⚠️ Limitations: affects style, not knowledge accuracy

---

## Self-Consistency Prompting

Self-consistency improves reliability by **sampling multiple reasoning paths** and selecting the majority answer.

**Example (Age puzzle):**

> “When I was 6 my sister was half my age. Now I’m 70, how old is my sister?”

* Run 1 → 67
* Run 2 → 67
* Run 3 → 35 (incorrect)

**Final Answer (by majority):** 67 ✅

✅ Use cases: arithmetic, commonsense reasoning, tasks prone to varied reasoning
⚠️ Limitations: requires multiple runs, more computational cost

---

## Reflexion / Critique Prompting

Reflexion and critique prompting have the model **analyze and improve its own response**.

**Example (code debugging):**

```text
Write Python code to compute factorial.
```

*Model produces buggy code.*

```text
Now check the above code for mistakes and correct them.
```

*Model revises and fixes the code.*

✅ Use cases: code generation, reasoning-heavy tasks, fact-checking
⚠️ Limitations: critique quality depends on the model; may miss subtle errors

---

## Conclusion

* **Zero-Shot** → fast, works for simple tasks
* **Few-Shot** → shows patterns with examples
* **Chain-of-Thought** → explicit reasoning for complex queries
* **Role Prompting** → controls style/persona
* **Self-Consistency** → improves correctness via multiple outputs
* **Reflexion/Critique** → iterative self-improvement

These techniques can be **combined** for maximum effect. For example: *few-shot + CoT + reflexion* often yields strong results in reasoning tasks.

---

## References

* Wei et al. (2022). *Chain-of-Thought Prompting Elicits Reasoning in Large Language Models*
* Kojima et al. (2022). *Large Language Models are Zero-Shot Reasoners*
* Wang et al. (2022). *Self-Consistency Improves Chain-of-Thought Reasoning in Language Models*
* Shinn et al. (2023). *Reflexion: Language Agents with Verbal Reinforcement Learning*
