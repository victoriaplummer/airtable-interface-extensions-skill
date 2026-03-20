# Airtable Custom Interface Extensions - Claude Skill

A comprehensive reference document that makes Claude (or any LLM) excellent at building Airtable Custom Interface Extensions.

## Why this exists

Airtable shipped a new Interface Extensions SDK that is significantly different from the old Blocks SDK. Claude's training data is full of old SDK patterns that no longer exist. This document gives Claude the complete, current API surface so it produces working code on the first try.

## What's inside

SKILL.md - a single, dense reference file covering the complete API surface, styling guidance, data patterns, FieldType reference, and common mistakes.

## How to use

### Claude Projects (claude.ai)

1. Open your Claude Project
2. Go to Project Knowledge
3. Upload SKILL.md

### Claude Code (CLI)

Copy SKILL.md into your project's .claude/ directory.

### Other LLMs

The document is model-agnostic markdown. Add it to any system prompt, RAG pipeline, or knowledge base.

## Sources

Built from official Airtable documentation and verified against their GitHub example repos.

## License

MIT