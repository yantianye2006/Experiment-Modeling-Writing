# Core principles (citation)

Use this skill to turn manuscript text into a defensible citation export:

- segmented text with citation candidates for each segment
- a reference-manager import file in `.enw`, `.ris`, or Zotero `.rdf`
- conservative evidence notes explaining whether each candidate truly supports the segment

## Default scope

Default to broad scholarly coverage (`all`): do not filter candidates by publisher family,
journal brand, or prestige tier. Rank by how directly the source supports the exact claim,
the quality and proximity of the evidence, source authority, and metadata integrity. Prefer
primary research for experimental, causal, mechanistic, or quantitative claims; use reviews
mainly for background or synthesis; label preprints and other non-peer-reviewed scholarship
clearly. Do not use blogs, news releases, search snippets, or unsourced webpages as the sole
support for a scholarly claim.

Apply a journal-family restriction only when the user explicitly asks for one:

- `Nature系列`: Nature Portfolio journals.
- `CNS`: `Cell`, `Nature`, and `Science` plus their major sister journals.
- `CNS及其子刊` or `CNS/sister journals`: accepted titles in Nature Portfolio, the AAAS Science family, and Cell Press.
- `只要Nature/Science/Cell正刊`: only the flagship journals `Nature`, `Science`, and `Cell`.

When a restricted scope is requested, verify current official journal pages if the boundary is
submission-critical because journal portfolios change. The exact optional boundary is in
`references/journal-scope.md`.

## Source hierarchy

Use sources in this order:

1. Structured bibliographic metadata: Crossref, PubMed/NCBI E-utilities, DOI metadata.
2. Publisher and repository pages: official journal pages, DOI landing pages, PubMed, arXiv, and discipline-specific authoritative repositories.
3. Full text or abstract pages, if accessible.
4. Secondary databases such as Google Scholar, Semantic Scholar, Web of Science, or Scopus only as discovery aids, not as the sole support basis.

Prefer structured APIs for metadata and publisher pages for claim verification. If metadata and publisher page disagree, preserve the DOI and journal-page facts and flag the discrepancy.

## Search quality rules

- Prefer precision over volume. A useful answer is usually 3-8 candidates, not 50 loosely related papers.
- Use exact phrase searches only for distinctive terms; otherwise use concept terms and synonyms.
- When a journal-family restriction is active, verify journal identity instead of inferring it from a word in the title.
- Treat citation count as a tie-breaker, not evidence of support.
- Capture retractions, corrections, and expressions of concern when visible in Crossref or publisher metadata.
- Date-sensitive topics require current searching and an explicit search date.
- For medical, clinical, or safety claims, search current literature and state that citations do not replace clinical guidance or systematic review.

## Source notes

This skill uses public bibliographic APIs, authoritative scholarly databases and repositories,
publisher pages, and reference-manager import documentation. Verify pages at use time when exact
metadata, publication status, journal coverage, or current import behavior matters.
