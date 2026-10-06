# RefereeCode AI Kit

**Stop your AI assistant from writing `any`, leaking server code to the client, and skipping validation.**

RefereeCode AI Kit is a set of modular Cursor Project Rules and prompt workflows for **Next.js (App Router) + TypeScript + Tailwind CSS + Zod**. It gives your AI coding assistant clear, scoped constraints, and pairs them with compiler and lint settings so the rules are enforced, not just suggested.

This repository contains a **free sample**: the kit's core rule file. The full kit is a paid download.

**[→ Get the full kit for USD 10](https://refereecode.lemonsqueezy.com/checkout/buy/3a12d4cc-48de-4f7f-ac06-d08223793b56)**

---

## Try the free core rule

The core rule is the always-on foundation of the kit. It enforces:

- **No `any`.** Not explicit, not inferred, not `as any`. Untrusted data is parsed with Zod, never cast.
- **A correct Server/Client boundary.** Server Components by default, `'use client'` only where interactivity needs it, and no server-only modules or secrets in client code.
- **Validation at every trust boundary.** Request bodies, params, search params, form data, environment variables, and third-party responses all go through Zod.

### Install

1. Copy [`.cursor/rules/000-core.mdc`](.cursor/rules/000-core.mdc) into the `.cursor/rules/` folder at the root of your Next.js project.
2. Reload Cursor.
3. Open Agent chat and confirm the rule appears among the active rules.

The free rule is released under the MIT License. See [`LICENSE`](LICENSE).

---

## What's in the full kit

```
.cursor/rules/
├── 000-core.mdc                   # Always on. Hard rules: no `any`, Server/Client boundary, validation
├── 010-nextjs-app-router.mdc      # Server vs Client Components, data fetching, env vars, route segments
├── 020-validation-zod.mdc         # Zod at every trust boundary, inferred types, safe parsing
├── 030-styling-tailwind.mdc       # Class composition, variants, tokens, accessibility
├── 040-api-and-server-actions.mdc # Validate → authenticate → authorize → execute → respond
└── 100-best-practices.mdc         # Early returns, size limits, Result-based errors, naming

workflows/
├── 01-secure-api-route.md         # 5 chained prompts: contract → schemas → service → handler → audit
└── 02-component-refactor.md       # 6 chained prompts: diagnose → lock behavior → types → boundary → restructure → verify

README.md                          # 3-step install, plus tsconfig and ESLint settings that enforce the rules
LICENSE                            # Single-developer commercial license
```

### Two tiers of rules

| Tier | Meaning | Examples |
| --- | --- | --- |
| **MUST** | Mandatory. The AI asks before breaking one. | No `any`, no server imports in client files, Zod on all external input |
| **SHOULD** | Strong defaults. The AI may deviate, but must say why. | Early returns, file-size limits, `Result` instead of `throw` |

### Context-aware loading

Only the core rule is always in context. The others attach automatically when you work on matching files. For example, the API rule loads when you edit a `route.ts`. This keeps token usage low and the guidance relevant.

### Workflows with review checkpoints

For the two tasks where a single prompt most often goes wrong (building an API endpoint and refactoring a component), the kit includes chained prompts. Between each step there is a checkpoint you verify before continuing, so the AI never designs, builds, and approves its own work in one pass.

---

## Pricing

**USD 10, one-time payment.** Single-developer license for unlimited personal and client projects. Minor updates included. No subscription.

**[Buy the full kit on Lemon Squeezy →](https://refereecode.lemonsqueezy.com/checkout/buy/3a12d4cc-48de-4f7f-ac06-d08223793b56)**

## Compatibility

Built for Next.js 15+ (App Router), TypeScript 5+, Tailwind CSS 3 or 4, and Zod 3 or 4. Requires a Cursor version that supports Project Rules (`.cursor/rules/`).

## A note on expectations

AI assistants are non-deterministic. No rule set guarantees that a model follows every instruction every time. That's why the full kit also ships the TypeScript and ESLint settings that catch what slips through.
