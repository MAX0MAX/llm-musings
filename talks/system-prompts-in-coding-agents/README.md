# System Prompts in Coding Agents

> A practical look at the hidden operating instructions behind coding agents.

**Status:** Planned

## About this talk

I want to understand what system prompts actually contribute to a coding agent. The interesting part is not collecting prompt text; it is seeing how instructions, tools, repository context, safety rules, and the execution loop work together.

My working assumption is that the system prompt matters, but it is only one layer of the product.

## Questions I want to answer

- What responsibilities belong in a coding agent's system prompt?
- How are tool contracts and behavioral rules expressed?
- How do repository instructions enter the prompt hierarchy?
- What happens when instructions conflict or context becomes too large?
- Why can two agents with similar prompts behave very differently?

## Draft outline

1. What a system prompt is—and is not
2. Instruction hierarchy and context assembly
3. Tools, permissions, and execution boundaries
4. Repository-specific instructions
5. Common failure modes
6. The system beyond the prompt
