# AGENTS: budi-bounty

Public repo for the Budi Bounty board (Monad Metropolis hackathon, Track 04). Read `CONTEXT.md` and `docs/adr/` before working; use the glossary's terms exactly.

## Rules

- Commit as `mel@innvertir.com` only. Changes land on `main` via squash-merged PRs; never push or open a PR without the owner's go.
- No secrets in tracked files. No em-dashes in written output. Prose in `.md` files is one line per paragraph.
- This repo talks to the private `budi` monorepo only over HTTP, never by importing its code.
- Node package manager: pnpm.

## Agent skills

### Issue tracker

Issues and specs live in this repo's GitHub Issues (`gh` CLI). See `docs/agents/issue-tracker.md`.

### Triage labels

The five default labels: `needs-triage`, `needs-info`, `ready-for-agent`, `ready-for-human`, `wontfix`. See `docs/agents/triage-labels.md`.

### Domain docs

Single-context: `CONTEXT.md` and `docs/adr/` at the repo root. See `docs/agents/domain.md`.
