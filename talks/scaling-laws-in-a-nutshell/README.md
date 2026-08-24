# Scaling Laws, in a Nutshell

> My attempt to build a clear, intuitive picture of scaling laws in modern AI.

**Status:** Work in progress

## About this talk

I am not an expert on scaling laws. This talk is a record of how I am learning to reason about them: what the empirical patterns say, why they became so influential, and where the simple story starts to break down.

The goal is not to present a comprehensive academic survey. I want to make the core ideas understandable, preserve the important caveats, and leave the audience with a useful mental model.

## Intended audience

Engineers and technically curious people who work with LLMs but do not necessarily have a machine-learning research background.

## Questions I want to answer

- What does a scaling law actually describe?
- Why do parameters, training data, and compute matter together?
- What does a power law tell us about predictability and diminishing returns?
- How did the Chinchilla result change the "bigger is better" story?
- How are pretraining, post-training, and test-time scaling related?
- What can scaling laws predict, and what can they not tell us?

## Draft outline

1. Why scaling became a central idea in AI
2. The empirical pattern: loss decreases predictably with scale
3. The three knobs: model size, data, and compute
4. Power laws and diminishing returns
5. Compute-optimal training: from Kaplan to Chinchilla
6. Beyond pretraining: post-training and test-time compute
7. Limits, caveats, and open questions

## Working takeaway

Scaling laws are empirical relationships that help us predict how model performance changes as resources grow. They make large training runs more predictable, but they are not laws of intelligence and do not guarantee that every capability improves smoothly.

## References

See the organized [reference list](reference/README.md) for the recommended reading order and links to videos, explanatory articles, and primary papers.

More detailed notes and slides will be added as the talk develops.
