# The Dev Loop in a Nutshell

> My compact mental model of how a coding agent turns an open-ended request into verified changes.

**Status:** Planned

## About this talk

This talk focuses on the loop around the model: inspect the environment, choose an action, observe the result, and continue until the outcome is verified. I want to explain why this loop matters more than a single impressive model response.

## Questions I want to answer

- What are the minimum stages of an effective development loop?
- Which decisions should come from the model, and which should remain deterministic?
- Why are tests and other verification signals essential?
- How should an agent recover when an action fails?
- When should the loop stop and ask a human for help?

## Draft outline

1. From one-shot generation to iterative work
2. Inspect, plan, act, and observe
3. Editing, running, and verifying
4. State, memory, and recovery
5. Permissions and human checkpoints
6. What makes a loop trustworthy
