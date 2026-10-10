# Changelog

Every published version of the ADS schools directory and what changed in it. Each version is a [Release](../../releases).
This list is **updated continuously**: corrections are published as new versions, and each one is recorded here.

Questions, corrections or missing schools: **ram@adsopen.org**

| Version | Released | Rows | Summary |
|---|---|---:|---|
| **v9** | 2026-10-10 | 1,471,114 | 2,149 missing schools added in Telangana and West Bengal; 3 more added by hand; 6 names corrected |
| v8 | 2026-10-07 | 1,468,962 | Operational schools only; 314 names corrected; 385 IB/Cambridge copies identified; 2 missing schools added |
| v2 | 2026-08-12 | 1,696,488 | v1 + 15 class-range fixes + 1,045 IB and Cambridge schools |
| v1 | not released | 1,695,443 | The UDISE+ extract as retrieved |

The jump from v2 to v8 is deliberate. The version numbers follow our internal master data. Versions 3–7 were working
versions that were never published, and their effects are listed under v8 below.

---

## Coming next: cleaning forecast (probable, week of 12 October 2026)

This is what we expect to clean next. It is a forecast, not a promise: items may move, and anything that changes will be
recorded under its version above.

- **More missing schools, state by state.** v9 re-collected Telangana and West Bengal district by district (see below).
  The remaining states and the organisation-filed schools follow, about one state a day.
- **More IB/Cambridge copies.** About 80 groups of IB/Cambridge records were left out of the v8 review because the match
  was uncertain. They are being reviewed now, so more records will probably be marked `duplicate`.
- **A review of IB/Cambridge links to same-name campuses**, e.g. "The Shri Ram School" (Gurugram), where an
  international record may point at the wrong campus.
- **More area labels on same-name campuses** ("Name, Place"), as they are found.

Later, not expected this week:
- A real state for the organisation-filed schools (KVS, NVS, IAF, Navy).
- Class ranges for international schools that have no UDISE twin.

---

## v9 (2026-10-10)

Files in the release:

| File | What it is |
|---|---|
| `ads-schools-v9.csv.gz` | The dataset. Same 13 columns as v2 and v8, in the same order. |
| `changes_since_v8.csv` | **Every row-level change since v8** (2,158 rows). Columns: `udise_code`, `change`, `column`, `before`, `after`. For each added school, `after` gives its name, district and how it was found. |

Nothing was removed, and no v8 record changed apart from the 6 names below.

### 1. 2,149 missing schools added in Telangana and West Bengal

The original UDISE+ collection (July 2026) searched UDISE+ **pincode by pincode**, using the India Post pincode list. Three
kinds of school were out of its reach:

- schools whose UDISE+ record uses a pincode that is **not in the India Post list** (often a mistyped or retired one);
- schools with **no pincode at all** in UDISE+ (e.g. La Martiniere for Boys, Kolkata);
- schools **registered after the collection ran** (UDISE+ is updated continuously; many 2026-27 registrations).

In October 2026 both states were collected again, first by pincode (every pincode within 5 of a listed one) and then
**district by district**, which returns every school in the district whatever its pincode. Only **Operational** schools
were kept, and anything already in the directory was skipped.

| State | Added |
|---|---:|
| Telangana | 532 |
| West Bengal | 1,617 |
| **Total** | **2,149** |

- Each new school is matched to its IGOD district in the same way as the rest of the file.
- Names are as UDISE+ writes them, with stray spaces and commas tidied.
- 146 of them share a name with another school in the same district, so they carry an area label, e.g.
  "SARASWATI SHISHU MANDIR, Mayureswar" or "THE DELHI SCHOOL, Bodhan". The existing schools keep their names.
- 1 school was left out as a second UDISE code for a school already listed: SR High School, Khammam (same address as
  36311092402).

### 2. Three schools added by hand

Reported missing and checked against UDISE+:

| udise_code | School | Place |
|---|---|---|
| 27230500196 | Khar Education Society Junior College of Commerce / Science | Mumbai. UDISE+ lists it as Closed; it is open. It was in v2 and removed in v8. |
| IBIND-0267 | Smt. Sulochanadevi Singhania IB World School | Thane |
| 36230202368 | Jawahar Navodaya Vidyalaya Rangareddy | Filed under Navodaya Vidyalaya Samiti, Hyderabad Region |

### 3. Six names corrected

| udise_code | Before | After |
|---|---|---|
| 09090102303 | D L F PUBLIC SCHOOL | DLF Public School |
| 09100109115 | BAL BHARTI PUB SCH. | Bal Bharti Public School, Noida |
| 09270912190 | ST M R JAIPURIYA SCH GOMATI NAGAR | Seth M. R. Jaipuria School, Gomti Nagar |
| 09341401005 | SHEELING HOUSE CIVIL LINES | Sheiling House School |
| 09452214205 | ARMY PUBLIC SCHOOL | Army Public School, New Cantt |
| 36230202359 | DELHI PUBLIC SCHOOL, KHAJAGUDA | Delhi Public School, Hyderabad - Khajaguda |

---

## v8 (2026-10-07)

Files in the release:

| File | What it is |
|---|---|
| `ads-schools-v8.csv.gz` | The dataset. Same 13 columns as v2, in the same order. |
| `changes_since_v2.csv` | **Every row-level change** to a record that is in both v2 and v8, plus the added records (708 rows). Columns: `udise_code`, `change`, `column`, `before`, `after`. |
| `removed_since_v2.csv.gz` | **Every v2 record that is not in v8** (227,528 rows), with the reason. Columns: `school_id`, `udise_code`, `school_name`, `igod_district_name`, `igod_state_name`, `source`, `reason`. |

### 1. Non-operational schools removed (227,527 records)

v2 carried every school in the UDISE+ extract, whatever its status. v8 keeps only those UDISE+ lists as **Operational**:

| UDISE+ status | Records removed |
|---|---:|
| Permanently Closed | 126,359 |
| Closed | 73,446 |
| Merged | 23,761 |
| Sanctioned but not Operational | 2,452 |
| DCF not Received | 1,509 |
| **Total** | **227,527** |

No IB or Cambridge record was removed for this reason.

### 2. One duplicate removed

`CAMBIND-0453` "National Public School" is the same school as UDISE `29200910417` (National Public School, HSR Layout,
Bengaluru), so it was removed. It is the only removal not caused by UDISE+ status, and it is listed in
`removed_since_v2.csv.gz`.

### 3. School names corrected (314 records)

Names were corrected where the source name was wrong, unclear or shared by several campuses:
- Same-name campuses get an area label in the form "Name, Place", e.g. "National Public School, JP Nagar".
- Spelling mistakes are fixed, e.g. "Grammer" → "Grammar".
- IB and Cambridge names are aligned with the matching UDISE school.

Most corrections are to well-known private schools, IB/Cambridge schools and their UDISE twins. Every one is in
`changes_since_v2.csv` (`change = name corrected`), with the old and new name.

### 4. IB/Cambridge copies identified (385 records)

The v2 merge matched IB and Cambridge schools to UDISE only on the exact name within a state, and never compared IB with
Cambridge. A manual review found **385 more copies**, e.g. Delhi Public School R.K. Puram had a UDISE, a Cambridge and an
IB record. Following v2's rule that both records are kept, these copies are **not deleted**. Instead:
- 384 are now `duplicate_status = duplicate`, with `duplicate_of_udise_code` set to the record they copy. That record
  can be a UDISE school or, where no UDISE twin exists, another IB/Cambridge record.
- 1 (`IBIND-0246`, The Universal School, Mumbai) is now `ambiguous`, because it matches more than one UDISE campus.

**Effect:** the counting rule from v2, `duplicate_status IS NULL OR duplicate_status = 'unique'`, now gives
**1,468,248** distinct schools.

### 5. IB/Cambridge records that became their own entry (3 records)

These were `duplicate` copies of a UDISE school that UDISE+ now lists as closed. That record was removed in step 1, so the
IB/Cambridge record is now `unique`, with `duplicate_of_udise_code` cleared:
- CAMBIND-0313 Green Gables International School
- IBIND-0214 Stonehill International School
- IBIND-0241 The School Of Raya

A fourth, CAMBIND-0292 Gems Genesis International School, turned out to be a copy of another record. It is counted in
section 4.

### 6. District corrections (3 records)

`IBIND-0012`, `IBIND-0231` and `IBIND-0240` are Chennai schools that v2 had filed under Theni (Tamil Nadu). They now sit
under Chennai, in both `district_name` and `igod_district_name`.

### 7. Pincode correction (1 record)

`29200900221` (National Public School, JP Nagar, Bengaluru): pincode 560040 → 560062.

### 8. Two missing schools added

The original UDISE+ data was collected pincode by pincode. Some schools are missing from it, most likely because UDISE+
holds a mistyped or unlisted pincode for them. These two were reported missing and added by hand:

| `school_id` | `udise_code` | `school_name` | Place |
|---|---|---|---|
| 9900001 | 19170106605 | La Martiniere for Boys, Kolkata | Kolkata, West Bengal |
| 9900002 | 19170106611 | La Martiniere for Girls, Kolkata | Kolkata, West Bengal |

- `source` is `UDISE`, because both carry real UDISE codes. Hand-added records are numbered from 9900001.
- Classes are 1–12. The pincode (700017) is **assumed**; it was not read from UDISE+.
- UDISE+ misspells the girls' school as "La Martinere for Girls". v8 uses the correct spelling.
- We expect more such gaps, and later versions will add them. Please report missing schools to ram@adsopen.org.

### Not changed in v8
- The 13 columns, their order and their meaning are the same as in v2.
- Every other value of every kept record is identical to v2.
- **Organisation-filed schools** (KVS, NVS, IAF EC Society, Navy Education Society) are still filed under the
  organisation instead of a state: 2,132 records in v8. MSRVVP has none left. The derived state column once planned for
  "v3" has not been built.
- Names keep the source's casing and untidiness: 2,758 contain a line break, and 25,342 have leading or trailing spaces.
  Use a real CSV parser.

---

## v2 (2026-08-12)

- **v1** + 15 records corrected where `class_frm` was greater than `class_to` (all 15 in Rajasthan; the two values were
  swapped).
- **+1,045 international schools:** 779 Cambridge and 266 IB, with no UDISE code. They are numbered from `school_id`
  9000001, with codes `CAMBIND-0001` and `IBIND-0001` onwards. Their overlap with UDISE is marked in `duplicate_status`
  and `duplicate_of_udise_code`.
- State and district names are matched to IGOD (`igod_state_name`, `igod_district_name`), alongside the UDISE forms.

## v1 (not released)

The UDISE+ extract exactly as retrieved: 1,695,443 records. It contained no international schools.
