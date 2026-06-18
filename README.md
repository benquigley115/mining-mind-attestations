# Mining Mind — Public Attestation Chain

This repository is a tamper-evident public record. It exists so that anyone —
an investor, an auditor, a competitor — can independently verify *when* Mining
Mind first saw a piece of data, without taking our word for it.

## What this repository is

One JSON manifest per day. Each manifest contains:

- the announcements Mining Mind captured that day (id, headline, release
  timestamp, and **capture timestamp** — the moment our system first saw it),
- a SHA-256 record hash for each announcement,
- the SHA-256 of the full dataset and of the derived analytics tables,
- **the SHA-256 of the previous day's manifest file.**

That last field is what makes this a *hash chain*. Altering any historical
day's data would change that day's manifest bytes, which breaks the recorded
link in every manifest that follows it — visibly, and permanently.

## What it proves

1. **Capture-before-claim.** Each manifest is committed to this repository on
   the day it covers. Those commit timestamps are controlled by GitHub, not by
   us. Nobody — including us — can later pretend an announcement was captured
   earlier than the chain shows.

2. **Dataset integrity.** Every Mining Mind evidence pack prints a dataset
   hash. If that hash appears in this chain, the pack was produced from an
   attested dataset state — not a tampered copy.

3. **Honesty about gaps.** Days the publisher missed are disclosed in the next
   manifest (`gap_days_since_previous`), never papered over. Announcements that
   predate the capture loop carry no capture timestamp and are labelled
   "captured retrospectively" in the product.

## Verify it yourself
