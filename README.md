# Local AI Hardware Bench — community

Submissions, corrections and discussion for
**[localaiarena.com](https://localaiarena.com)**, a database of measured
local-LLM inference performance where every number traces to a dated,
attributed public source.

This repository holds **no code and no data**. It exists so that the numbers
on the site can be argued with in public. The dataset and the build pipeline
live elsewhere and are not open source — see *Why this repo is separate* below.

## What to open

| You want to | Open |
|---|---|
| Point at a benchmark that should be in the dataset | **[Submit a benchmark](../../issues/new?template=benchmark-submission.yml)** |
| Say a published number is wrong or stale | **[Report a wrong number](../../issues/new?template=correction.yml)** |
| Anything else — questions, ideas, methodology arguments | **[Discussions](../../discussions)** |

## What makes a submission usable

The bar is not "is this number plausible", it is **can someone else check it**.
A tok/s figure on its own is not evidence; the conditions that produced it are
what make it comparable to anything else on the site. So a submission needs:

- **A public URL** where the measurement was published, with a **named author**
  and a **date**. A screenshot, a DM or a number typed into the form with no
  source behind it cannot be ingested, however accurate it is.
- **The quantisation and the context length.** Without these a figure is not
  comparable — a 4-bit run and an 8-bit run of the same model on the same
  machine are different measurements, not two readings of one.
- **The backend, and its version if stated.** The same silicon gets faster as
  backends improve; that is why every record carries a date.
- **Batch size and offload**, because batch-1 latency and batched throughput
  answer different questions, and a model that spilled to system RAM is a
  different measurement again.

[How to measure tok/s in a way someone else can use](https://localaiarena.com/guides/how-to-measure-honestly/)
is the long version, and is worth reading before running something new.

**Most submissions are rejected, and that is the intended outcome.** The
benchmark numbers on the open web include AI-generated articles inventing
models that do not exist, content mills restating each other, and "calculator"
pages that compute a figure and present it as a measurement. Rejection is not
a judgement of you.

## What happens to a submission

1. It is checked against the raw source text — not the summary, the source.
2. If it survives, it is added to the dataset with your source cited by URL,
   author and date.
3. Confidence is then **computed, not assigned**: two or more independent
   sources agreeing within 25% make a record `verified`, one makes it
   `single-source`, and sources that disagree beyond that make it `disputed`,
   with the disagreement shown rather than averaged away. Independence is keyed
   on the author, so one person cross-posting a run to three forums counts once.

The full rules are published at
[localaiarena.com/methodology](https://localaiarena.com/methodology/).

## Submitting your own measurement

Very welcome, and it is the fastest way to fill a gap. Two things to know:

- Publish it somewhere public first — a forum post, a gist, a repo issue — and
  link that. The site cannot cite a figure that exists nowhere but this issue.
- By submitting, you agree it may be published on the site under
  [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/), credited to
  you. You keep every other right to your own work.

## Why this repo is separate

The site's dataset is a compilation: several hundred posts read, attributed,
checked against raw source text, and mostly thrown away. That curation is
licensed CC BY-NC 4.0, and the build pipeline behind it is not open source.

None of that affects contributing here. What a submission actually is, is a
**link to something already public** — so nothing about receiving it requires
opening the dataset or the pipeline. Every individual measurement on the site
belongs to whoever made it and is credited to them by name and date.
