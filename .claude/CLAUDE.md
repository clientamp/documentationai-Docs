# Documentation Agent Instructions

This repo powers the Client Amp documentation site via documentation.ai. Content is MDX files organized by product folder, configured in `documentation.json`.

## Repo Structure

```
documentationai-Docs/
├── documentation.json          # Site config with products dimension
├── lickityclick/               # LickityClick docs
├── helmnative/                 # HelmNative docs
├── tightedit/                  # TightEdit docs
├── tightshare/                 # TightShare docs
├── droplet-dash/               # Droplet Dash docs
├── sponsor-crm/                # Sponsor CRM docs
├── ds-hub-api/                 # DS Hub API docs
├── flow/                       # Flow docs
└── shared-core/                # SharedCore developer docs
```

## MDX Rules

- **Format**: All pages must be `.mdx` files
- **Frontmatter**: Every file MUST have `title` (required) and `description` (recommended)
- **File naming**: kebab-case only (e.g., `ai-provider.mdx`, not `AIProvider.mdx`)
- **Paths in documentation.json**: Omit the `.mdx` extension (e.g., `lickityclick/introduction`)
- **No placeholder text**: Every page must contain real, useful content. Do not leave "Documentation coming soon" or similar stubs.

## Frontmatter Template

```mdx
---
title: Page Title Here
description: One-line description of this page's content.
---
```

## Available MDX Components

Use these documentation.ai components in your MDX:

### Callout
```mdx
<Callout kind="info" title="Optional Title">
  Content here. Kinds: info, tip, warning, success, danger.
</Callout>
```

### Steps
```mdx
<Steps>
  <Step title="Step Name" icon="lucide-icon">
    Step content.
  </Step>
</Steps>
```

### Tabs
```mdx
<Tabs>
  <Tab title="Tab Name" icon="lucide-icon">
    Tab content.
  </Tab>
</Tabs>
```

### Card Grid
```mdx
<Columns cols={3}>
  <Card title="Title" icon="lucide-icon" href="/path">
    Card description.
  </Card>
</Columns>
```

### Code Groups
```mdx
<CodeGroup tabs="Swift,JavaScript">
  ```swift
  // Swift code
  ```
  ```javascript
  // JS code
  ```
</CodeGroup>
```

### Expandable
```mdx
<Expandable title="Section Title" default-open="false">
  Hidden content.
</Expandable>
```

### ParamField (for API docs)
```mdx
<ParamField query="param_name" param-type="string" required="true">
  Description of the parameter.
</ParamField>
```

### Update (for changelogs)
```mdx
<Update label="2026-03-15" description="v2.0.0" tags={["feature", "improvement"]}>
  ## What's New
  - Feature description
</Update>
```

## Icons

All icons use [Lucide](https://lucide.dev/) names in kebab-case: `link`, `mail`, `film`, `share-2`, `server`, `database`, `package`, `check-square`, `code`, `book`, `rocket`, `zap`, `star`, `plug`, `clock`, `history`, `home`, `key`, `cpu`, `palette`, `wifi`, `layers`, `info`, `globe`, etc.

## Source Repos

Product source code is at `/Users/openclaw/dev/<repo-name>`:

| Product | Source Repo | Key Files |
|---------|------------|-----------|
| LickityClick | `/Users/openclaw/dev/lickityclick` | `README.md`, `docs/architecture.md`, `docs/data-model.md`, `docs/deployment.md`, `docs/testing-guide.md`, `src/lib/db/schema.ts` |
| HelmNative | `/Users/openclaw/dev/HelmNative` | `README.md`, `.claude/CLAUDE.md`, `Packages/HelmCore/Sources/` |
| TightEdit | `/Users/openclaw/dev/tightedit` | `README.md`, `.claude/CLAUDE.md` |
| TightShare | `/Users/openclaw/dev/tightshare` | `README.md`, `.claude/CLAUDE.md` |
| Droplet Dash | `/Users/openclaw/dev/droplet-dash` | `.claude/CLAUDE.md`, source code |
| Sponsor CRM | `/Users/openclaw/dev/sponsor-crm` | `README.md`, `.claude/CLAUDE.md` |
| DS Hub API | `/Users/openclaw/dev/ds-hub-api` | `.claude/CLAUDE.md`, source code |
| Flow | `/Users/openclaw/dev/flow` | `README.md`, `.claude/CLAUDE.md` |
| SharedCore | `/Users/openclaw/dev/shared-core` | `.claude/CLAUDE.md`, `Docs/DESIGN_TOKEN_INVENTORY.md`, Swift package sources |

## Workflow

1. Read source material from the product repo (README, CLAUDE.md, source code)
2. Write MDX content into the correct product folder in this repo
3. Update `documentation.json` navigation if you add or rename pages
4. Commit and push to `main` — documentation.ai auto-deploys on push
5. Each container in documentation.json must use ONE child type (groups OR pages OR dropdowns, not mixed)

## Quality Bar

- Reference actual features, APIs, and workflows from the source code
- Include real code examples where appropriate (Swift for native apps, TypeScript/JavaScript for web apps)
- Use Steps for setup/onboarding flows
- Use Tabs for platform-specific or variant content
- Use Callouts for important notes, tips, and warnings
- Keep language concise and direct — write for developers and creators
- No marketing fluff — focus on how things work and how to use them
