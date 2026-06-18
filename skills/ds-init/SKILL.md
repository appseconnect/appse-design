---
name: ds-init
description: >
  Initializes the Product Design environment for appse ai. Verifies prerequisites
  (AGENTS.md, MCP), clones arise-specs into arise-workspace, creates
  ds-workspace.code-workspace, validates Figma MCP, and scaffolds design handbook
  folders. Run this first, before any other ds- skill. Trigger on phrases like
  "init design", "set up design environment", "ds-init", "initialize design
  workspace", or "get the design environment ready". ds- working skills are
  reserved — this init prepares the workspace ahead of them.
---

# ds-init — Initialize the Product Design Environment

First skill in the Design plugin. Clones the handbook repo, creates the **Design
role workspace file**, validates Figma, and scaffolds design folders.

Read `conventions/workspace.md` (appse-core) for repo URLs and workspace rules.

---

## Constants

| Constant | Value |
|----------|-------|
| Workspace root | `%USERPROFILE%\repos\arise-workspace` |
| Workspace file | `%USERPROFILE%\repos\arise-workspace\ds-workspace.code-workspace` |
| Specs clone target | `%USERPROFILE%\repos\arise-workspace\arise-specs` |
| Specs repo URL | `https://insyncworld@dev.azure.com/insyncworld/APPSeCONNECT-Reimagine/_git/arise-specs` |
| Setup report | `%USERPROFILE%\repos\arise-workspace\setup\ds-env-{YYYY-MM-DD}.md` |
| Marketplace path | `%USERPROFILE%\.cursor\plugins\local\appse-marketplace` |
| Role plugin name | `appse-design` |

**Workspace roots for Design:** `arise-specs` only.

---

## Workflow

### Step 0 — Ensure Cursor Plugins Installed (marketplace-first)

If **`/setup-ds`** was already run, skip to Step 1.

Otherwise follow **Phase 1–3** in `appse-marketplace/skills/references/marketplace-plugin-install.md` for role plugin **`appse-design`**.

**Fresh plugin clone** → **Developer: Reload Window**, then re-run **`/ds-init`**. Install fails → hard stop.

### Step 1 — Load Config

- Load `AGENTS.md` and `conventions/workspace.md`.

### Step 2 — Workspace and Repository (pause before clone)

1. Create `%USERPROFILE%\repos\arise-workspace` and `setup/` if missing.

2. **Clone or pull `arise-specs`** (confirm first; stop on dirty tree).

3. **Write `ds-workspace.code-workspace`** (Design role only):

   ```json
   {
     "folders": [
       { "path": "<relative-or-absolute-path-to-arise-specs>", "name": "arise-specs" }
     ],
     "settings": {}
   }
   ```

4. **Open workspace:**

   ```powershell
   cursor "$env:USERPROFILE\repos\arise-workspace\ds-workspace.code-workspace"
   ```

5. **Verify** `arise-specs/handbook/guidelines/` is readable.

### Step 3 — Validate Design Tooling (MCP)

- **Figma** — confirm auth. Failure → warn, link connector settings.

### Step 4 — Confirm Brand Standards

- `handbook/guidelines/` holds appse ai brand standards.
- Absent → flag for PM/Design lead.

### Step 5 — Scaffold Design Folders

Idempotent:

```
handbook/design/
├── research/
├── flows/
├── wireframes/
├── design-system/
└── handoffs/
```

### Step 6 — Report

Save `setup/ds-env-{YYYY-MM-DD}.md`:

> Design environment ready:
> ✅ `ds-workspace.code-workspace` created and opened
> ✅ arise-specs ({branch})
> ✅ Figma {connected / ⚠️}
> ✅ Brand standards {present / ⚠️}
> ✅ Design folders scaffolded
>
> ds- working skills are reserved. Pair with PM on `pm-user-research` for now.

---

## Definition of Done

- [ ] `appse-marketplace`, `appse-core`, and `appse-design` under `%USERPROFILE%\.cursor\plugins\local\`.
- [ ] `ds-workspace.code-workspace` created and opened.
- [ ] `arise-specs` is a workspace root.
- [ ] Design folders scaffolded.
- [ ] Setup report saved.

---

## Output Rules

- Idempotent; confirm before clone
- Never merge Design folders into another role's workspace file
- Brand standards live in `handbook/guidelines/`
