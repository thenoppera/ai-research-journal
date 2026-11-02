# Testing an LLM reviewer

**Period:** September–October 2026  
**Theme:** LLM-as-judge evaluation, adversarial testing, false positives

I wanted to understand whether an LLM-based reviewer could inspect changes to instruction files, identify genuine problems, and avoid inventing issues. I didn't want to judge it by how convincing its review sounded. I wanted a test where I already knew what was wrong and could also see whether it would complain about changes that were actually fine.

I built a small, self-designed adversarial test. It included planted flaws with a separate answer key, alongside legitimate or clean changes. I compared different review instructions and repeated runs, looking at both missed issues and unsupported claims. I also changed the setup after noticing that a reviewer could discover fixture details if the answer key was left in a place it could search. That was a useful reminder that test design can leak the answer and make a result look stronger than it is.

The most useful change was to make the reviewer verify each claim against the files as they existed on disk and the relevant history, then give a clear verdict for each change. That made the task more concrete than asking for a general review of whether something looked correct.

## What I learned

- **Measure false positives as well as detections.** A reviewer that finds every planted issue but invents problems in clean changes is not necessarily useful.
- **Keep ground truth separate.** A test is compromised if the model can discover the answer key in the material it is reviewing.
- **Make claims checkable.** Asking for a verdict tied to the actual file and history is more useful than inviting a broad, confident-sounding critique.
- **Repeat the test.** One run can be misleading. Repeated runs help reveal instability, although a small number of repetitions is still weak evidence.
- **Keep the scope honest.** The test is narrow, built by me for a particular review workflow, and not an external benchmark or a general measure of model capability.

I have not published the fixtures, answer key, private review transcripts, or configuration files. The point of this entry is the evaluation method and the reasoning behind it, not the reproduction of my private environment.

The experiment made me more cautious about the phrase "the model reviewed it." A review is only meaningful when the task is defined, the evidence is available, and the findings can be checked.
