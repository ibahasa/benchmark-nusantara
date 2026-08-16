# Disputing a figure

This repository does not take code contributions. What it takes is corrections,
and the fastest way to get one applied is to make it specific.

## What a useful dispute looks like

Name the row and the reason. Every verdict here is attached to one item, so a
disagreement can be settled on that item rather than argued in general.

> In `raw/javanese-word-meanings-135/export-jv-B-hasil-model.csv`, the lemma
> `X` is scored wrong for model `Y`. The answer given is a valid Javanese
> equivalent in the Yogya-Solo variety, and it should be added to the key.

That we can check in minutes. Compare it with:

> Your Javanese benchmark is unfair to our model.

That we cannot act on at all, however true it may turn out to be.

## The three disputes we expect most

**The answer key is incomplete.** A model gave a correct equivalent that our key
does not list. This is the most common real defect, and the one we most want to
hear about. Our keys are plural by design, and they have been extended before
after review.

**The item itself is broken.** Some items cannot distinguish understanding from
an empty answer. `Tembung` means *kata*, and almost any filler sentence about a
Javanese word contains the word *kata*. We keep such items only where the
alternative is worse, and we would rather be told when we got that judgement
wrong.

**The variety is wrong.** Javanese sets are scored against Yogya-Solo. If an
answer is standard in East Javanese or Banyumasan and we marked it wrong, say
which variety and, if you can, where it is attested.

## What we will not change on request

**The score of a model because its vendor asks.** A verdict changes when the
item, the key, or the rubric is shown to be wrong, not when the party affected by
it objects. This applies equally to models that flatter us.

**Withheld items.** Where a set has a withheld slice, those items are never
published and no request will produce them. Which sets have one, and how much
each withholds, is in the table in `README.md`. They are the only reason a figure
here can still be defended a year from now.

**Retroactive figures in articles.** An article is a frozen claim on a date and
links to a commit SHA. If a correction changes a number, the current data changes
and the article gets a dated follow-up note. The original text is not silently
edited.

## How to send one

Open an issue on this repository, or write to **halo@ibahasa.com**.

Include the dataset folder, the file, and the row. A `sha256` from
`MANIFEST.json` helps if you are quoting a version that may since have changed.

## What happens next

A correction that holds up is applied to the source data, the affected figures
are recomputed, and the dataset is republished. The `PROVENANCE.md` of that set
records what changed and when. A correction that does not hold up gets an answer
explaining why, which is a slower reply than silence but a more useful one.

## Reusing this data

CC BY 4.0. Attribution to ibahasa.

One request that the license does not cover, so we make it as a request: **please
do not put this repository into a training corpus.** See `CANARY.txt` inside the
datasets that publish their answer keys. A benchmark key inside a training set
stops measuring understanding and starts measuring recall, and the number becomes
worthless to you as well as to us.
