# mogy-vault

A focused ML knowledge vault. Notes live here permanently — write once, link often.

---

## Structure

```
mogy-vault/
├── 00-inbox/               ← Capture raw notes here first
│
├── concepts/               ← Evergreen concept notes
│   ├── foundations/
│   │   ├── math/           ← Vectors, Norms, Distance, Std Dev, Linear Functions
│   │   └── classical-ml/   ← Perceptron, Linear/Logistic Regression, Softmax…
│   └── deep-learning/
│       ├── architectures/  ← MLP, CNN, Wide vs Deep, Deep Learning
│       ├── training/       ← Gradient Descent, Backprop, PyTorch workflow
│       ├── optimization/   ← Adam, Momentum, RMSProp, LR Decay
│       ├── regularization/ ← Dropout, L1/L2, Early Stopping, Overfitting
│       ├── normalization/  ← BatchNorm
│       ├── activations/    ← ReLU, Non-Linear Activations, Dead Neurons
│       └── weight-init/    ← He, Glorot
│   └── generative/         ← RNNs, LSTMs, Sequence Modelling, BERT
│
├── literature-notes/       ← Paper-level notes (with PDF excerpts)
│   ├── papers/             ← One note per paper
│   └── mechanisms/         ← Specific techniques cited in papers
│
├── projects/               ← Applied work, blog drafts
│
└── assets/templates/       ← Templates for new notes
```

---

## How to Use

### Adding a new concept note
1. Drop a raw note in `00-inbox/`
2. When fleshed out, move it to the right `concepts/` subfolder
3. Use the **Concept template** (`assets/templates/Concept.md`)
4. Add `[[wiki-links]]` to related notes and link back from them

### Adding a new paper note
1. Create a file in `literature-notes/papers/` using the **Paper template**
2. Fill in frontmatter: title, authors, date, pdf, url, tags
3. Write your highlights and takeaways
4. If a paper introduces a specific mechanism, create a note in `literature-notes/mechanisms/` and link to it

### Linking philosophy
- Link generously with `[[Note Name]]` — Obsidian resolves by filename
- Every note should have at least one outgoing link and be linked from at least one other note
- Use the **Map of Content** (`Map of Content.md`) as the vault's table of contents
- Tag notes with `#tags` for cross-cutting concerns (e.g. `#normalisation`, `#CNN`)

### Workflow for reading papers
1. Read the paper with PDF open
2. Create a paper note using the Paper template
3. Paste key excerpts / highlights with page references
4. Identify mechanisms → create or link mechanism notes
5. Link paper note to relevant concept notes

---

## Templates

| Template | Use for |
|---|---|
| `assets/templates/Paper.md` | Research paper notes |
| `assets/templates/Mechanism.md` | Specific techniques from papers |
| `assets/templates/Concept.md` | Evergreen concept notes |

---

## Entry Point

Start from [[Map of Content]] to navigate learning paths.
