# Dynamic-Web-TWAIN-skill

Skill for [Dynamic Web TWAIN SDK](https://www.dynamsoft.com/web-twain/overview/).

[Agent Skills](https://agentskills.io/) is an open standard for extending AI agents with specialized capabilities. Skills package domain-specific knowledge and workflows that agents can use to perform specific tasks.

You can put the `web-twain` folder in the following places to make it effective.

| Location            | Scope               |
| ------------------- | ------------------- |
| `.agents/skills/`   | Project-level       |
| `.cursor/skills/`   | Project-level       |
| `~/.cursor/skills/` | User-level (global) |

Replace `cursor` width your editor's name, like `.codex/skills/`.

## Prompt Examples

### Asking Questions

```
What is Dynamic Web TWAIN service? Please also show the links of referenced docs.
```

### Creating Samples


1. Vanilla-JS local resources sample.

   ```
   Create an index.html file to use Dynamic Web TWAIN to scan documents, with basic document scanners listing and configuration functions. Please use resources files included in SDK instead of using CDN.
   ```

2. Vanilla-JS CDN sample.

   ```
   Create an index.html file to use Dynamic Web TWAIN to scan documents, with basic document scanners listing and configuration functions. Please use resources files from CDN.
   ```

3. React sample.

   ```
   Create a react project to use Dynamic Web TWAIN to scan documents. I only need a minimum sample which lists scanners, sets whether to use document feeder, DPI, pixel type and scans documents.
   ```




