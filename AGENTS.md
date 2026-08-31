# Vault agent instructions

This is an Obsidian vault run on a bottom-up, atomic-note PKM system. Read this fully before touching any files.

## Core philosophy

- Bottom-up structure — organisation emerges from links, not folders.
- Atomic notes — one idea per note, fully expressed.
- Links carry meaning — relationships live in connections, not nesting.
- Don't pre-split — a concept only earns its own note when something else needs to link to it.

## Vault structure

```
00-inbox/        incomplete or unprocessed notes
10-notes/        atomic concept notes (should be ~70% of the vault)
20-hubs/         topic index notes linking related concepts (a handful, 10-15 total)
30-sources/      lecture notes, book notes, papers (~20% of the vault)
90-archive/      old notes not actively used
```

Folder = type, not tag. Never add a `folder` or `location` field to frontmatter.

|Folder|Question to ask|
|---|---|
|`10-notes`|Is this _my_ understanding of an idea?|
|`30-sources`|Does this note have an author other than me?|
|`20-hubs`|Do I have 8+ notes orbiting one topic?|
|`00-inbox`|Is this incomplete or not ready to link to?|

## Your job: processing 00-inbox/

When asked to process the inbox, work through it note by note (not in a silent batch). For each inbox note:

1. **Read and understand** the raw content. Inbox notes are messy by design — fragments, half-thoughts, mixed topics.
2. **Decide what it becomes**, using Phase 2 logic:
    - Would I think about this idea outside of this context? → extract to `10-notes/`
    - Does a note on this already exist? → search the vault first, then add a `[[link]]` to it instead of duplicating
    - Only makes sense tied to its source? → it belongs in `30-sources/`, cleaned up, not extracted
    - Multiple distinct ideas in one inbox note? → split into multiple atomic notes, one idea each
3. **Write in my own words.** Never copy-paste from the inbox note's source material verbatim — atomic notes are understanding, not transcription.
4. **Link naturally inline**, in the body text, as the idea connects to other concepts. Don't bolt on a "Related notes" section — that's not how this system links.
5. **Use the correct template** (below) and fill it in properly — don't leave placeholder fields blank without reason.
6. **Move, don't delete**, the original inbox note once it's been processed — I'll tell you where (default: leave it in place unless I've set up an archive/processed convention; ask me the first time).
7. **Show me a short summary** after each note: what you extracted, where it went, what you linked. Don't move on to the next file until I've had a chance to sanity-check the first few.

## Note templates

### `10-notes/` — atomic note

```yaml
---
created: YYYY-MM-DD
type: note
status: draft
topic: 
tags:
  - dl/<facet>/<leaf>
---

# Title

Body — one idea, in my own words.

*From* → [[source note]]
```

Omit the `tags:` block entirely if no cross-cutting tag applies (don't leave it empty).

### `30-sources/` — lecture / book / paper

```yaml
---
created: YYYY-MM-DD
type: source
source-type: lecture
status: draft
topic: 
tags:
  - dl/<facet>/<leaf>
---

# Title

## Raw notes


## Key concepts mentioned
- 

*From* → 
```

### `20-hubs/` — topic hub

```yaml
---
created: YYYY-MM-DD
type: hub
status: evergreen
---

# Title

## Section
- [[Note]]
- [[Note]]
```

Only create a hub note if 8+ existing notes genuinely orbit one topic and none exists yet. Don't create one pre-emptively.

## Status values

- `draft` — incomplete, still being worked on
- `evergreen` — done, stable, ready to link freely

New notes from inbox processing start as `draft` unless clearly complete.

## Topic

The `topic:` field is broad — one level above the concept. Values currently in use:

- `ML` — anything machine learning / deep learning (the default; ~85% of notes)
- `linear-algebra` — vectors, norms, distance, linear/affine functions
- `statistics` — MLE, standard deviation, bias-variance

Use a list only for genuine cross-field concepts: `topic: [statistics, linear-algebra]`. Don't tag inbox notes — the folder is the tag. Don't invent new topic values casually; check what's already in use first.

## Cross-cutting tags

`tags:` (YAML list, no `#`) mark themes that cut across the topic and the folder, so search or the tag pane can pull a thread together. Hierarchical: `dl/<facet>/<leaf>`. Assign 1–3 per note; omit the block if none fit. Purely mathematical notes (`topic: linear-algebra` / `statistics`) usually get none — the topic field carries them.

**Rules for the taxonomy:**
- Only tag with a leaf that already exists below, *or* add a new leaf to this list in the same commit. Never leave an undocumented tag in a note.
- Prefer the most specific leaf. A note earning a brand-new leaf needs a real cluster (≥2–3 notes), not a one-off.
- The roadmap leaves (marked ·0·) have no notes yet — they're reserved so future notes slot in consistently. Don't delete them.

### `dl/architecture/` — structural blueprint
`mlp` · `cnn` · `rnn` · `transformer` · ·0· `gnn` · ·0· `ssm`

### `dl/training/` — parameter-update mechanics & stability
`optimizer` · `loss` · `regularization` · `normalization` · `initialization` · `activation` · `backprop` (autodiff, computation graphs, vanishing/exploding gradients, BPTT)

### `dl/theory/` — what networks can represent & why they generalize
`expressivity` (universal approximation, depth vs width) · `generalization` (bias-variance, over/underfitting) · `optimization` (loss-landscape geometry, non-convexity)

### `dl/paradigm/` — learning formulation & supervisory signal
`supervised` · ·0· `self-supervised` · ·0· `unsupervised` · ·0· `rl` · ·0· `meta-learning`

### `dl/generative/` — ·0· (none yet)
·0· `diffusion` · ·0· `gan` · ·0· `vae` · ·0· `flow` · ·0· `autoregressive`

### `dl/llm/` — language-model pipelines
`peft` (LoRA, QLoRA, prefix tuning) · `quantization` (AWQ, GPTQ, GGUF, INT4/FP8) · ·0· `alignment` · ·0· `rag` · ·0· `inference`

### `dl/stack/` — implementation & hardware layer
`pytorch` · ·0· `cuda` · ·0· `distributed` · ·0· `evaluation`

## Rules you must follow

- Never copy source text verbatim into a `10-notes/` note — always paraphrase in my own words.
- Never pre-split a note into multiple concepts unless each concept could plausibly be linked to from elsewhere.
- Never add metadata fields that aren't in the templates above.
- Never create a hub note without checking there are genuinely 8+ orbiting notes.
- Always search the existing vault for a matching note before creating a new one on the same concept.
- Always ask before deleting anything — move or leave in place instead.
- Keep atomic notes short enough that I'd actually re-read them. If a note is getting long, that's a signal it's two ideas, not one.

## Vault health check

If asked to review vault health, check the ratio:

```
10-notes   → should be ~70% of the vault
30-sources → ~20%
20-hubs    → a handful, maybe 10-15 total
00-inbox   → should always be close to empty
```

If `30-sources` outnumbers `10-notes`, flag it — it means I'm collecting but not distilling.