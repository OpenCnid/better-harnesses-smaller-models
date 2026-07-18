# Agent instructions

## The note

- [density-chain.md](density-chain.md) is a five-tier chain-of-density study
  of the paper: same length per tier, more entities each tier, a locator on
  every claim. Skim with T1, work with T5; exact values live in its key
  results table.
- The note is working ground truth; the paper is canonical. On any conflict,
  the paper wins and the note gets fixed.
- `index.json` carries the machine-readable pin (arXiv:2607.08938v1),
  verification date, and tags. Parse it; don't scrape the markdown.
- To update the note, invoke the `density-chain` skill from
  [chain-of-density](https://github.com/OpenCnid/chain-of-density); study the
  paper at the source; write nothing from memory. Humor only in the README
  and *our take* — tiers, key results, and provenance stay bone-dry.

## The paper

- No PDF is hosted here. Fetch it straight from the source:
  `curl -L -o better-harnesses.pdf https://arxiv.org/pdf/2607.08938v1`
  (drop the `v1` for the current version).
- Downloaded copies are session study material: scratchpad only, never
  committed back to this repo.
- A v1 snapshot lived in this repo's git history until July 18, 2026;
  SHA-256 `3fac74f3152a8ec2cd6d28e98a6e5cff323fea9c39e7328bdb38bfb0b3003b17`
  still verifies those historical bytes if reproducibility matters.
- Attribute claims and quotations to arXiv:2607.08938v1 and the paper's
  authors, not to this repository.
- The note pins version 1. Check `https://arxiv.org/abs/2607.08938` for newer
  versions before making version-sensitive claims.
- The paper is licensed CC BY 4.0. Preserve attribution and follow the
  license terms.

