<div align="center">

<img src="assets/banner.svg" width="100%" alt="better-harnesses-smaller-models: a small model bar raised by a scaffold to the height of a tall frontier bar, at a fraction of the cost">

*Lift the task into the harness. Keep the small model. Keep the money.*

[![arXiv](https://img.shields.io/badge/arXiv-2607.08938-b31b1b?logo=arxiv&logoColor=white)](https://arxiv.org/abs/2607.08938)
[![our prose](https://img.shields.io/badge/our_prose-CC_BY_4.0-3b7ddd)](LICENSE.md)
![paper license](https://img.shields.io/badge/paper-CC_BY_4.0-8b949e)
![numbers from memory](https://img.shields.io/badge/numbers_from_memory-0-2ea44f)
![tiers](https://img.shields.io/badge/tiers_shipped-all_five-a371f7)
![papers hosted](https://img.shields.io/badge/papers_hosted-0_(on_purpose)-2ea44f)

</div>

> **A notes repo, not a mirror.** This repo is OpenCnid's study of one paper —
> Yang, Zhao, Wu & Kästner, *Better Harnesses, Smaller Models: Building 90%
> Cheaper Agents via Automated Harness Adaptation*
> ([arXiv:2607.08938](https://arxiv.org/abs/2607.08938)). No paper is hosted
> here; arXiv serves the original beautifully, and the one-command fetch is
> below. [The note](density-chain.md) is an original synthesis — our words,
> their findings, a locator on every claim.

> [!IMPORTANT]
> **The one-way rule.** When our note and the paper disagree, the paper wins
> and the note gets fixed. No exceptions, no negotiation. That rule is the
> entire reason we can call the note ground truth with a straight face.

## 🔗 The note

[density-chain.md](density-chain.md) is a five-tier chain-of-density study of
the paper, written to the house
[methodology](https://github.com/OpenCnid/chain-of-density): five rewrites at
a held ~150-word budget, every claim carrying a locator (§ section, Table N,
Fig. N), exact numbers only.

| tier | what it is |
|---|---|
| **T1 — sparse** | the cost problem, the lift-it-into-the-harness thesis, the 89.7%-at-4%-cost headline |
| **T2–T4** | same length each, folding in 2–3 more salient entities per round — the failure-mode framework, Table II, the diversity and capability results |
| **T5 — dense** | maximally fused, still readable, every claim traceable |
| **key results** | exact values — recovery rates, ρ = −0.96, the strategy mix percentages |
| **our take** | the only opinionated section, clearly ours, quarantined |

The one-breath version: frontier agents are great and unaffordable; small
models are affordable and flunk the frontier's harness. But routine business
tasks repeat themselves, so a meta-agent can move the repeated difficulty
out of the model and into the harness — a plan skeleton here, a filtered
tool set there, a hook that programmatically refuses the failure mode — and
suddenly a 26B model is matching the frontier at 4% of the price. The
catch, quantified twice over: it only works when the task actually repeats
(ρ = −0.96), and the harness amplifies capability rather than minting it.

## 🏔️ Standing on the shoulders of giants

The actual science was done by **Chenyang Yang**, **Xinran Zhao**,
**Tongshuang Wu**, and **Christian Kästner**, all at Carnegie Mellon
University, affiliations as printed on the paper. They built the framework,
the optimizer, and the task suite, spent the $1,260 so you don't have to,
and released the code
([malusamayo/migration-analysis](https://github.com/malusamayo/migration-analysis)).
Cite them, not us; BibTeX in [CITATION.md](CITATION.md).

## 📥 Want the PDF? One command, straight from the source

We don't keep a copy here (see: entire ethos, above). arXiv hosts it
beautifully, for free, forever — no middlemen, no photocopier smell:

```bash
curl -L -o better-harnesses.pdf https://arxiv.org/pdf/2607.08938v1
```

Drop the `v1` to always get the current version; keep it to get the exact
bytes our note studied.

## Source and attribution

The paper is by Chenyang Yang, Xinran Zhao, Tongshuang Wu, and Christian
Kästner.

> Yang, C., Zhao, X., Wu, T., & Kästner, C. (2026). *Better Harnesses,
> Smaller Models: Building 90% Cheaper Agents via Automated Harness
> Adaptation*. arXiv:2607.08938v1. https://doi.org/10.48550/arXiv.2607.08938

When citing the research, cite the original paper rather than this repo. See
[CITATION.md](CITATION.md) for BibTeX.

## Provenance

The note in [density-chain.md](density-chain.md) was verified against a fresh
fetch of the arXiv v1 PDF on July 18, 2026; v1 (submitted July 9, 2026) is
the latest version as of that date. Consult the
[arXiv record](https://arxiv.org/abs/2607.08938) for newer versions.

This repo briefly hosted a checksum-verified snapshot of the v1 PDF
(SHA-256 `3fac74f3152a8ec2cd6d28e98a6e5cff323fea9c39e7328bdb38bfb0b3003b17`)
as an acquisition artifact; it was removed on July 18, 2026 in favor of the
one-command fetch above, per house rule. The exact bytes remain retrievable
from this repository's git history, and the hash above still verifies them.

## Kept honest by machine

[`index.json`](index.json) is the machine-readable face of this repo: the
source pin, the verification date, the tags. **Trellis**, our current
project, consumes those indexes and owns freshness — when arXiv revs a v2,
the note gets flagged before we get embarrassed.

## Honest notes

- **We are not affiliated with the authors** or Carnegie Mellon. We just
  appreciate a paper that publishes its budget line.
- **No papers are hosted here.** The paper stays at arXiv under its authors'
  CC BY 4.0 license; we point, we don't photocopy.
- **The note is lossy by construction.** The locators are the refund policy:
  any claim can be walked back into the paper in one hop.
- **We will get things wrong.** When we do, the fix lands source-first and
  the correction is public history. If we've mangled this paper, open an
  issue — correcting the record *is* the project.

## License

The paper: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) per the
arXiv record, © its authors. Our prose: [CC BY 4.0](LICENSE.md) © OpenCnid
Labs.

## Layout

```
density-chain.md    the five-tier note (the artifact)
index.json          machine-readable pin + verification metadata
CITATION.md         BibTeX — cite the humans, not us
AGENTS.md           the agents' front door
LICENSE.md          CC BY 4.0 for our prose; the paper keeps its own
assets/             banner art (the scaffold is load-bearing)
```

The methodology — METHOD.md, the synthesis prompt, the `density-chain` skill
— lives canonically in
[chain-of-density](https://github.com/OpenCnid/chain-of-density) and is
linked, not copied.

---

<div align="center">
<sub>This README was assembled by a large model that read a paper about replacing large models. It has decided not to take it personally: the harness, after all, was the hero.</sub>
</div>
