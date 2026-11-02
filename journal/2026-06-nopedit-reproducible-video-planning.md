# NopEdit: making video plans reproducible

**Period:** June–October 2026  
**Theme:** AI-assisted engineering, planning, measurement, quality assurance

NopEdit is a personal project exploring how to make parts of gaming-video production more systematic without handing creative judgment to an autonomous editor.

The problem became clear as I worked on more videos: planning logic was being repeated across individual projects. The same kinds of rules appeared in several places, while the creative decisions that genuinely belonged to a particular video were mixed in with them. That made changes harder to reason about and made it difficult to know whether a refactor had preserved the behavior of an existing plan.

I approached this as a separation problem. Reusable rules belong in shared code; video-specific decisions belong in a smaller project-level description. When a project needs an exception, the reason should be visible rather than silently overriding the shared behavior.

## Reproducibility before abstraction

I did not want to move repeated logic into a shared planner and simply assume the result was equivalent. The migration uses existing plans as reference points. The new planner generates a plan, and tests compare its output with the known plans. Differences need to be explicit and named. The purpose is not to make every old decision permanent; it is to make changes intentional and inspectable.

This became a useful general engineering principle for me: when replacing a working system, preserve a way to compare the old behavior with the new one. A refactor should not be accepted just because the new structure looks cleaner.

## Measure what can be measured

Another part of the project explores cut placement using recorded measurements from voice regions and camera-facing signals. The measurements can be saved and replayed, so a later plan can be checked without silently re-guessing the same inputs. When required evidence is missing, the system should stop and say what is missing rather than inventing a value.

The delivery checks look at the rendered file, not just the plan that was supposed to produce it. They cover technical properties such as dimensions, duration, the final frame, and audio levels. Synthetic test files with known faults help check whether the gate catches the problems it is intended to catch.

I also maintain a source-graded collection of editing principles. I don't want a well-known creator tip and a carefully supported professional recommendation to appear equally authoritative just because both are written as rules. The evidence behind a principle should affect how much weight I give it.

## The human boundary

NopEdit is not an autonomous system that watches any long recording and decides what story should be told. It helps organize and verify repeatable parts of production. Choosing the story, deciding what is funny or meaningful, and approving the final edit remain human responsibilities.

I use Claude Code and agent workflows to help implement and test the system. My role is to define the problem, decide how the pieces should fit together, specify acceptance criteria, inspect changes, and check whether the output meets those criteria. That is AI-assisted development, not a claim that I independently hand-wrote every implementation detail.

## What I would carry into another project

- Separate reusable policy from project-specific choices.
- Preserve provenance: a rule or exception should have an explainable origin.
- Make important outputs replayable where possible.
- Test the delivered artifact, not only the intermediate representation.
- Keep creative decisions with the person whose taste and intent the work is meant to express.
