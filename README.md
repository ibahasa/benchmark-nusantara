# Benchmark Nusantara

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21970463.svg)](https://doi.org/10.5281/zenodo.21970463)

Benchmark data for Indonesian and Javanese language models.

Every figure we publish at [ibahasa.com](https://ibahasa.com/id/benchmark) links
back to a file here, pinned to the commit it was cited at. If you want to check a
number, this is where you check it.

This repository exists because of one uncomfortable fact about language
benchmarks: the moment you publish an answer key, the next model trains on it,
and your number stops measuring understanding and starts measuring recall. Most
of the design choices below are attempts to be honest about that rather than to
pretend it away.

## What is measured

Six sets across two languages. Each set measures one ability and is never
averaged with another.

| Set | Language | Items | What it asks |
|---|---|---:|---|
| `id-B` | Indonesian | 38 | slang comprehension |
| `id-N` | Indonesian | 69 | text normalisation to standard Indonesian |
| `id-W` | Indonesian | 54 | spelling correction, including restraint on text that is already correct |
| `jv-A` | Javanese | 46 | speech levels (*tingkat tutur*), recognising and producing the right register |
| `jv-B` | Javanese | 135 | everyday word meanings |
| `jv-arti-kata` | Javanese | 43 | rare word meanings, absent from open Javanese sources |

The item counts above are fixed. The model panel is not, so it is stated with a
date rather than as a bare number: **as of 2026-08-16, fourteen models**, eleven
through a commercial router and three quantised to 4 bits on our own hardware.
The current list and count live in each set's `ringkas-model.csv`, which grows
when the panel grows. This sentence does not.

Local rows carry a blank cost rather than a zero, because "no invoice" is not the
same as "free", and their latency is not comparable to a hosted API.

## How scoring works

Multiple-choice items are scored by machine. Open-ended items are graded item by
item by a native speaker under a weighted rubric, and the rubric is published
alongside the figures so a verdict can be argued on a specific criterion rather
than merely disagreed with.

The codes in the `penilai` and `rumusan` columns (`mcq-py1`, `open-py1`, and the
rest) identify the prompt wording and the scorer behind each row. Their meanings
are listed in the "Kolom yang menentukan" section of
`benchmark-results/PROVENANCE-hasil.md`.

The Javanese sets are scored against the Yogya-Solo variety. A speaker of East
Javanese or Banyumasan may judge some items differently, and that is a limit of
the measurement, not a defect in the answer.

Answer keys are plural. A word meaning rarely has one correct wording, so each
item accepts several equivalents.

## Held-out slices, and where we did not have one

Most sets withhold roughly 30 per cent of their items from publication. Those
items exist so that a score can still be defended a year from now: if a model
scores well on the public part and poorly on the withheld part, it read the data.

The withheld slice lives inside the set it belongs to and runs on the same pass
as the published part, so the gap between the two measures leakage rather than
weight drift between two dates.

Counts as of 2026-08-17, and they grow as sets grow:

| Set | Withheld |
|---|---:|
| `id-B` | 11 of 38 |
| `id-N` | 20 of 69 |
| `id-W` | 16 of 54 |
| `jv-A` | 13 of 46 |
| `jv-B` | 64 of 199 |

A gap only means something if it is large enough. On slices this size, anything
under roughly twenty percentage points cannot be told apart from noise, and each
set's PROVENANCE states its own threshold.

Two sets have no withheld slice, and we would rather say so plainly than let you
discover it.

`jv-B` and `jv-arti-kata` published their full answer keys on 2026-08-15, 178
lemmas in total. For `jv-B` the reasoning is in its `PROVENANCE.md`: the lemmas
and their definitions were already public on our dictionary pages, so withholding
part of the key would have hidden nothing while making our published figure of
128 out of 135 impossible for anyone to verify. For `jv-arti-kata` the full
publication was deliberate in a different way, turning that set into a dated
contamination marker.

The consequence binds us, not you. **After 2026-08-15, a high score on those two
sets cannot be read as understanding.** Their control is a separate set of
Javanese lemmas drawn from the same pool, keyed under the same rules, and never
published anywhere. It is the only clean Javanese instrument we have left.

Its size is deliberately not stated here. The set grows, and a count of something
you can never inspect tells you nothing you could act on.

## Canary

`javanese-word-meanings-135` and `javanese-rare-word-meanings` each contain a
`CANARY.txt` holding a unique string that appears nowhere else. A model able to
reproduce it has read this repository as training data.

Two limits, stated where the file itself states them. The strings were planted on
2026-08-16, one day after those datasets were published, so a model that ingested
them on the first day will not be caught. And a silent canary is not proof of a
clean model: it answers in one direction only.

**If you are assembling a training corpus, please exclude this repository.**

## Layout

```
raw/<dataset>/
  MANIFEST.json     file list, byte sizes, sha256 of each file, export date
  PROVENANCE.md     how the figures were produced, and what limits them
  CANARY.txt        where present, a contamination marker
  <files>           the data itself
INDEX.md            table of every dataset here
```

Start at [`INDEX.md`](./INDEX.md).

Filenames are flattened from their original directory structure, so a dataset
drawn from several folders cannot produce two files with the same name. The
original path of each file is recorded in `MANIFEST.json`.

`PROVENANCE.md` files are written in Indonesian, which is the canonical version.
Some open with an English section covering what was measured, who scored it, the
main limits, and how to dispute a figure. The rest are being worked through; until
then, write to halo@ibahasa.com and we will answer in English.

## Three datasets that are not benchmark sets

`benchmark-results` is every published measurement in one table, one row per
model per set per task per prompt per repetition, with the run date and whether
that date was recorded or inferred. It is generated from the same snapshot the
website reads, so the numbers here and the numbers on the page cannot disagree.
Start here if you want to check a figure you saw on the site.

`model-throughput` holds per-model aggregates across runs: mean output tokens,
mean latency, implied tokens per second.

`benchmark-runs-archived` is exactly what its name says. It holds run reports
from a pipeline retired on 2026-08-06 and does not grow. The figures that
superseded it live in the per-set datasets and in `benchmark-results`.

## Citing a file

Use a permalink pinned to a commit, not to `main`:

```
https://github.com/ibahasa/benchmark-nusantara/blob/<commit-sha>/raw/<dataset>/<file>
```

A link to `main` shows whatever the file looks like today. A link to a commit
shows what it looked like when it was cited, which is usually what you want when
you are checking someone's arithmetic.

Each file's `sha256` is in `MANIFEST.json` if you want to verify a download.

## Citing this repository

A GitHub permalink is enough to check one file, but it is not a citable
identifier on its own: it has no fixed version and nothing indexes it as a
dataset. This repository is archived on [Zenodo](https://zenodo.org), which
mints a permanent, version-pinned DOI for every GitHub Release.

- **Cite the exact version you used** (recommended, for reproducibility):
  `10.5281/zenodo.21970464` (`v1.0.0`)
- **Cite "whatever is current"** (a concept DOI that always resolves to the
  latest version): `10.5281/zenodo.21970463`

```bibtex
@dataset{huda_2026_benchmark_nusantara,
  author    = {Huda, M. Khoirul},
  title     = {Benchmark Nusantara},
  month     = aug,
  year      = 2026,
  publisher = {Zenodo},
  version   = {v1.0.0},
  doi       = {10.5281/zenodo.21970464},
  url       = {https://doi.org/10.5281/zenodo.21970464}
}
```

`CITATION.cff` in this repository carries the same identifiers and is read
natively by GitHub's "Cite this repository" button on the repo's main page.

## If you think a figure is wrong

We would rather be corrected than be quoted incorrectly. See
[`CONTRIBUTING.md`](./CONTRIBUTING.md), or write to **halo@ibahasa.com**.

## Relationship to `research-data`

Non-benchmark research data lives in
[`ibahasa/research-data`](https://github.com/ibahasa/research-data): dictionary
corrections, corpus frequency tables, editor audits. The two are separated
because they change at different speeds. Research data must freeze so that an
article citing it stays checkable. Benchmark data changes every time a model is
run.

Articles published before the split link into `research-data` at a commit SHA.
Those links still resolve, because a commit permalink serves the tree at that
commit rather than whatever `main` holds today.

## License

CC BY 4.0. Attribution to ibahasa.
