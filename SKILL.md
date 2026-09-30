# Paperbrief — literature digest skill

When the user wants the state of research on a topic (`/paperbrief <topic>`), produce a digest — don't make them read 20 abstracts.

## Protocol

1. Run `node bin/paperbrief.mjs brief "<topic>" --n=8` (one arXiv request; respect the ~1 req / 3s limit — never parallelize calls).
2. If zero results, broaden terms once ("KV cache eviction" → "KV cache"), then report honestly.
3. Present the digest, then add what the CLI can't: a 5-line **analyst note** — what the top papers agree on, where they disagree, what's newest, and the one paper to read first.
4. Always caveat: abstracts only, verify against PDFs before citing.

## Rules

- Prefer recent papers for fast-moving topics; say so when results skew old.
- Never invent citations, venues, or author claims beyond the digest.
- Keep the analyst note opinionated but labeled as your synthesis, not the papers'.
