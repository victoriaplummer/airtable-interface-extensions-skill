# Airtable Custom Interface Extensions — Claude Skill

A comprehensive reference document that makes Claude (or any LLM) excellent at building [Airtable Custom Interface Extensions](https://airtable.com/developers/interface-extensions).

## Why this exists

Airtable shipped a **new** Interface Extensions SDK (`@airtable/blocks/interface`) that is significantly different from the old Blocks SDK (`@airtable/blocks`). Claude's training data is full of old SDK patterns — components like `<Button>`, `<Input>`, `<Box>`, and `<FormField>` that **no longer exist**. Without this skill, Claude will confidently write code that doesn't compile.

This document gives Claude the complete, current API surface so it produces working code on the first try.

## What's inside

**`SKILL.md`** — a single, dense reference file covering:

- **Import map** — the two import paths and what comes from each
- **Old vs New SDK disambiguation** — explicit table of what changed so Claude stops hallucinating old components
- **Styling and libraries** — confirmed that npm packages (D3, Recharts, Radix UI) work, why Tailwind/shadcn is difficult, and how to use Airtable's built-in color system
- **Data reading patterns** — useBase, useRecords, getCellValue, multi-table with custom properties
- **Data writing patterns** — permission-check-first pattern, single/batch operations, the batching loop template
- **Array field append pattern** — the number 1 footgun (linked records, attachments, multi-select all OVERWRITE)
- **Linked record patterns** — autocomplete with fetchForeignRecordsAsync, create-and-link in one write
- **Custom properties** — all 5 types (string, boolean, enum, table, field) with stable-identity warning
- **GlobalConfig** — persistent key-value storage patterns
- **Dark mode** — CSS-first approach (preferred) plus JS hook fallback
- **Complete FieldType reference** — read/write cell value formats for all 25+ field types
- **Constraints and limits** — 50-record batch, 15 writes/sec, 1.9MB payload, 150kB GlobalConfig
- **Official example repos** — all 8 Airtable repos with what each demonstrates
- **10 common mistakes** — the specific things Claude gets wrong without guidance

## How to use

### Claude Projects (claude.ai)

1. Open your Claude Project
2. Go to **Project Knowledge**
3. Upload `SKILL.md`
4. Claude will now reference it when building Airtable Interface Extensions

### Claude Code (CLI)

Copy `SKILL.md` into your project's `.claude/` directory:

```bash
mkdir -p .claude
cp SKILL.md .claude/airtable-interface-extensions.md
```

Claude Code will automatically include it as context.

### Other LLMs

The document is model-agnostic markdown. Add it to any system prompt, RAG pipeline, or knowledge base where you want an LLM to write Airtable Interface Extension code.

## Sources

This skill was built by scraping and synthesizing the **official Airtable documentation**:

| Source | What was extracted |
|--------|--------------------|
| [Getting Started Guide](https://airtable.com/developers/interface-extensions/guides/getting-started) | CLI setup, prerequisites |
| [Hello World Tutorial](https://airtable.com/developers/interface-extensions/guides/hello-world-tutorial) | Project scaffold, development mode |
| [Read Data Guide](https://airtable.com/developers/interface-extensions/guides/read-data-from-airtable) | useBase, useRecords, multi-table patterns |
| [Write Data Guide](https://airtable.com/developers/interface-extensions/guides/write-back-to-airtable) | CRUD operations, permissions, batch limits, linked records |
| [Custom Properties Guide](https://airtable.com/developers/interface-extensions/guides/builders-custom-properties) | useCustomProperties hook, property types |
| [Dark Mode Guide](https://airtable.com/developers/interface-extensions/guides/dark-mode) | CSS and JS approaches |
| [Full API Reference](https://airtable.com/developers/interface-extensions/api) | All models, hooks, components, utils, FieldType enum |
| [Airtable GitHub org](https://github.com/orgs/Airtable/repositories) | 8 example extension repos, source code patterns |

The source code of Airtable's [word-cloud extension](https://github.com/Airtable/interface-extensions-word-cloud-typescript) was used to confirm npm package compatibility (D3), CSS import patterns, and dark mode implementation.

## Contributing

Found an error or want to add a pattern? PRs welcome. The goal is to keep this as the single best reference for AI-assisted Airtable Interface Extension development.

## License

MIT