# ADS Schools Data

Bulk downloads for the [ADS Initiative](https://adsopen.org) schools directory — a reference list of schools in India, searchable at **[adsopen.org/schools](https://adsopen.org/schools)**.

This repository holds **data only**. Each dataset version is published as a [Release](../../releases), so every version keeps a permanent download URL.

## Latest

| | |
|---|---|
| **Version** | v2 |
| **Rows** | 1,696,488 |
| **Download** | [`ads-schools-v2.csv.gz`](../../releases/latest) — 32.4 MB gzipped, 172.1 MB expanded |

Full column documentation, caveats and checksums are in the [release notes](../../releases/tag/schools-v2). **Read them before using the data** — there are three things in particular that will produce wrong answers if you don't know about them:

1. Some schools are filed under an administering organisation rather than a state, so a state filter silently misses them.
2. The IB and Cambridge rows partly overlap the UDISE rows; don't count without deduplicating on `duplicate_status`.
3. `wc -l` overcounts, because thousands of school names contain line breaks.

## Sources

| Source | Rows | |
|---|---:|---|
| UDISE+ | 1,695,443 | Department of School Education & Literacy, Ministry of Education, Government of India |
| Cambridge | 779 | [Cambridge school finder](https://connectedtot.com/find-a-cambridge-school/) — schools with no UDISE code |
| IB | 266 | [IB school finder](https://ibo.org/programmes/find-an-ib-school/) — schools with no UDISE code |

State and district names are additionally matched to the **IGOD** (Indian Government Organisation Directory) listings; both the original and canonical forms ship as separate columns.

This is a **snapshot**, not a live feed. Nothing here is independently verified against the schools themselves, and coverage is what the sources contain rather than a census.

## Corrections and takedown

**ram@adsopen.org**

## Licence

Apache 2.0.
