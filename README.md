# Crypto's biggest primary bet: $12.2M to nominate Barry Moore in Alabama

**poidh bounty #1544 — "Most Surprising Crypto Money Trail of the 2026 Midterms"**

## The insight

Everyone who followed crypto's 2026 money watched Ohio ($56.6M) and the failed
$10.4M attempt to stop Juliana Stratton in Illinois. Almost nobody watched
Alabama — where the Fairshake network made its **largest primary bet of the
entire cycle**.

Defend American Jobs (FEC committee **C00836221**, the Republican arm of the
Fairshake network) reported **$12,203,100.05** in independent expenditures
**supporting Barry Moore** (candidate **S6AL00476**) in Alabama's Republican
U.S. Senate primary and runoff — and **$0** in the general election.

That is:

- **More than the famous anti-Stratton spend** ($10,449,309 opposing Juliana
  Stratton in the Illinois Democratic primary) — making Moore the single
  most expensive primary target, for or against, of crypto's 2026 cycle.
- **2.6× what Moore's own campaign raised all cycle** ($4,635,925.74 in
  receipts through Oct 14, 2026, per the FEC candidate totals API). The
  outside group didn't supplement the campaign; it dwarfed it.
- **$70.26 for every vote Moore received in the June 16 runoff** (173,674
  votes), and **$337.76 for every vote of his 36,129-vote runoff margin**
  over Jared Hudson.
- Spent entirely **before the nomination was decided**: $7,415,826.26 in the
  primary (May 19) and $4,787,273.79 in the runoff (June 16). In November —
  when Moore actually faced a Democrat — the network spent nothing at all.

## What happened in the race

- Moore, a U.S. representative, ran for the open seat vacated by Tommy
  Tuberville (who ran for governor). Fairshake endorsed him (endorsement
  listed on the race's Wikipedia page).
- The spending started early: the first buy was **$1,000,905 to Main Street
  Media Group on Feb 10, 2026**, followed by four more identical $1,000,905
  weekly flights in February–March, while early polls (Oct 2025–Jan 2026)
  had Moore in the 9–28% range behind Steve Marshall.
- **Primary, May 19, 2026:** Moore placed first but with only **39.2%**
  (189,067 votes; Hudson 25.6%, Marshall 24.5%) — no majority, so the race
  went to a runoff.
- **Runoff, June 16, 2026:** Moore won **55.8% to 44.2%** (173,674 to
  137,545; margin 36,129 votes).
- **General, Nov 3, 2026:** with zero crypto independent-expenditure help,
  Moore beat Democrat Everett Wess **54.71% to 45.29%** (917,338 to 759,321)
  — a 9.42-point margin, the **closest regular Senate election in Alabama
  since 1996** (Tuberville had won the seat by 20.36 points in 2020).

Whether the money *caused* the nomination can't be proven from filings —
Moore also held endorsements from President Trump and most of the state's
Republican establishment. What the filings do prove is the allocation: the
network's single biggest primary chequebook was opened not for a swing-state
November race, but to pick the Republican nominee in one of the safest
Republican states in the country — and then closed for the general election,
which turned out to be Alabama's closest Senate race in 30 years.

## The numbers (all FEC, 2026 cycle)

| Item | Amount |
|---|---|
| IE supporting Moore — primary (Form 24 notices) | $7,415,826.26 |
| IE supporting Moore — runoff (Form 24 notices) | $4,787,273.79 |
| **IE supporting Moore — total** | **$12,203,100.05** |
| Same total on Form 3X Schedule E (cross-check) | $12,254,526.93 (+0.42%) |
| IE for/against Moore — general election | $0 |
| Moore's own campaign receipts (through Oct 14, 2026) | $4,635,925.74 |
| Ratio, outside IE to the campaign's own receipts | 2.63× |
| IE per runoff vote received (173,674) | $70.26 |
| IE per runoff margin vote (36,129) | $337.76 |

Spending committee: Defend American Jobs (C00836221) — 100% of the Moore
support. Payees on the Form 24 notices: Main Street Media Group, RBC Media
LLC, Dockside Strategies LLC, Electoral Communications Group LLC.
First expenditure: Feb 10, 2026. Last: June 12, 2026 (runoff week).

Network context (same method, all three committees — Fairshake C00835959,
Defend American Jobs C00836221, Protect Progress C00848440): the largest
support total of the cycle was $36,874,167 for Jon Husted (Ohio, general);
the largest opposition total in a primary was $10,449,309 against Juliana
Stratton. Moore's $12.2M is the largest primary figure of either kind.

## Methodology — reproduce it

**Step 1 — FEC API (the required source).** Free API, DEMO_KEY suffices:

```
GET https://api.open.fec.gov/v1/schedules/schedule_e/?api_key=DEMO_KEY&committee_id=C00836221&candidate_id=S6AL00476&cycle=2026&per_page=100
```

This returns 47 rows totalling $24,457,626.98 — because by law every
independent expenditure is reported **twice**: once on a Form 24 (24/48-hour
notice) and again on Schedule E of the next Form 3X report. Counting both
forms double-counts the same ads. The canonical set used here is the
**22 Form 24 notices (most_recent), totalling $12,203,100.05**; the Form 3X
itemizations of the same expenditures total $12,254,526.93 (+0.42%), the
small difference being estimate-to-actual adjustments. Split by the API's
`election_type`: P2026 = $7,415,826.26, R2026 = $4,787,273.79, G2026 = none.

```
GET https://api.open.fec.gov/v1/candidate/S6AL00476/totals/?api_key=DEMO_KEY&cycle=2026
```

→ receipts $4,635,925.74, disbursements $4,293,858.11, coverage through
2026-10-14.

**Step 2 — bulk-file cross-check (no key needed).**

Download `independent_expenditure_2026.csv` from
https://www.fec.gov/files/bulk-downloads/2026/independent_expenditure_2026.csv
(SHA-256 f432539deb63e7c2b930140ea908fb4d3a79f84a6ee03c862bd1ef49d3d5eabe,
downloaded Nov 19, 2026). Filter `spe_id` ∈ {C00835959, C00836221,
C00848440} → 466 rows, $158,419,987.61. The 22 rows naming
`MOORE, FELIX BARRY` match the Form 24 set exactly (same amounts, same FEC
image numbers) and sum to $12,203,100.05. Ranking all candidates in that
file by primary-only spending confirms Moore is the network's largest
primary target.

**Step 3 — election results.** Wikipedia, "2026 United States Senate
election in Alabama" (results tables sourced to the Alabama Secretary of
State / FEC): primary May 19, runoff June 16, general Nov 3, 2026 — figures
quoted above. "Closest since 1996" is that article's characterization of the
9.42-point general-election margin.

**Caveats.** Independent expenditures are not contributions to the campaign;
they are ads and services bought independently (here, mostly TV/media buys
via Main Street Media Group). Filings can be amended; figures use the most
recent version of each notice as of Nov 19, 2026. Vote totals are the
reported (post-canvass Wikipedia-published) figures. Correlation is not
causation: no claim is made that the spending caused the outcome — only
that the allocation itself is the surprise.
