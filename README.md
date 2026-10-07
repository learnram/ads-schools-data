# ADS Schools Data

Bulk downloads for the [ADS Initiative](https://adsopen.org) schools directory: a reference list of schools in India, searchable at **[adsopen.org/schools](https://adsopen.org/schools)**.

This repository holds **data only**. Each dataset version is published as a [Release](../../releases), so every version keeps a permanent download URL.

## Latest

| | |
|---|---|
| **Version** | v8 |
| **Rows** | 1,468,962 (1,468,248 distinct schools once the IB/Cambridge copies are set aside) |
| **Download** | [`ads-schools-v8.csv.gz`](../../releases/latest) (28.1 MB gzipped, 157.7 MB expanded) |
| **What changed** | [`CHANGELOG.md`](CHANGELOG.md): every version since v1. The release also carries a row-by-row change list and the list of removed records. |

**v8 lists operational schools only.** 227,527 UDISE+ schools that are closed, merged or otherwise not operating were removed after v2. If you used v2, read the [changelog](CHANGELOG.md) first.

Full column documentation, caveats and checksums are in the [release notes](../../releases/tag/schools-v8). **Read them before using the data.** Three things in particular will give you wrong answers if you don't know about them:

1. Some schools are filed under an administering organisation instead of a state, so a state filter silently misses them.
2. The IB and Cambridge rows partly overlap the UDISE rows. Deduplicate on `duplicate_status` before counting.
3. `wc -l` overcounts, because thousands of school names contain line breaks.

## Continuously updated

**This list is updated continuously.** Whenever we find a cleaner version of a school's name, or a school that is missing, merged twice or filed under the wrong district, we correct it and publish a new version. Each version is a new Release, and [`CHANGELOG.md`](CHANGELOG.md) records exactly what changed. Earlier releases stay downloadable, but **always use the latest one**.

What we expect to clean next is listed under **[Coming next](CHANGELOG.md#coming-next-cleaning-forecast-probable-week-of-7-october-2026)** in the changelog.

## Sources

| Source | Rows in v8 | |
|---|---:|---|
| UDISE+ | 1,467,918 | Department of School Education & Literacy, Ministry of Education, Government of India. Operational schools only. 2 of these were added by hand (see the changelog). |
| Cambridge | 778 | [Cambridge school finder](https://connectedtot.com/find-a-cambridge-school/): schools with no UDISE code |
| IB | 266 | [IB school finder](https://ibo.org/programmes/find-an-ib-school/): schools with no UDISE code |

State and district names are also matched to the **IGOD** (Indian Government Organisation Directory) listings. Both the original and the canonical forms ship as separate columns.

Nothing here is independently verified against the schools themselves. Coverage is what the sources contain; it is not a census.

## Queries, corrections and takedown

For any question about the data, or to report a wrong or missing school, write to **ram@adsopen.org**.

## Licence

Apache 2.0.
