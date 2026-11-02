# Human oversight in applied LLM evaluation

**Period:** March–June 2026  
**Theme:** applied evaluation, reliability, human review

I worked on an applied evaluation workflow for a private organization. The project involved using language models to help assess submitted material against a rubric. I can't publish the organization's identity, its rubric, prompts, records, operating statistics, or implementation details, so this entry stays at the level of lessons I can safely discuss.

The experience changed the way I define an evaluation system. It is tempting to focus on the model's final judgment: Was the score reasonable? Was the explanation well written? But a judgment is only as useful as the evidence that reached the model and the process that happens after it responds.

I became much more attentive to the full decision path: whether the input was captured correctly, whether the model was applying the intended criteria, whether a second opinion actually added independent value, whether generated feedback matched the underlying judgment, and whether a human had a meaningful opportunity to intervene. A successful technical request also isn't the same as proof that the intended record changed; verification matters at the end of the workflow too.

A few lessons stayed with me:

1. **Input quality is part of model quality.** Missing or incorrectly captured evidence can look like poor reasoning. Before adding another model or agent, check what the first one actually received.
2. **A second model is not automatically an independent source of truth.** Review stages can introduce their own bias, including over-correction. Disagreement needs to be examined rather than resolved by blindly trusting the second answer.
3. **Splitting tasks changes the failure modes.** Separating structured assessment from user-facing writing can reduce one kind of leakage, while making it harder for the writing stage to verify every claim against the original evidence.
4. **Human review should be part of the design.** In this context, the model supported a person's decision; it did not own the final decision.
5. **Verify the action, not just the response.** A workflow should check that the intended result was saved to the intended place.

I don't present this as formal AI-safety research or as evidence that the resulting judgments were objectively correct. It was applied work, and its value to me was learning how much reliability depends on the surrounding process—not just the model call.

More project detail may be added only if disclosure permission allows it.
