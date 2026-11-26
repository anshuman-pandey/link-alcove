# Audit checkpoint — 26 November 2026

Public source: https://github.com/anshuman-pandey/link-alcove

Reviewed source head: `5c19fd410997a3dad66d38e2a273799a4d9078be`. Latest recorded [CI run](https://github.com/anshuman-pandey/link-alcove/actions/runs/43703048443) is success at this head.

Fresh local core check:

```text
l terms and collection (4.590585ms)
✔ browser HTML escapes imported markup and keeps folders (0.504645ms)
✔ malformed and oversized imports fail before storage (4.203172ms)
✔ Chrome-style nested folders, entities, unclosed DT/DD, tags and notes (12.720826ms)
✔ unsupported URLs and duplicates have visible counts; credentials never imported (3.299482ms)
✔ browser export is data only; scripts and resource attributes do not become content (1.836673ms)
✔ existing URL wins, repeat imports are idempotent, input objects unchanged (0.847607ms)
✔ our HTML export round-trips titles, folders, notes and tags without markup execution (3.206502ms)
✔ ordinary pages, empty, unsupported, oversized and deeply nested inputs fail safely (43.534019ms)
✔ overlong fields are counted as skipped, oversized notes fail whole preview (2.454189ms)
✔ stale drafts cannot overwrite newer saved revisions (2.338591ms)
✔ quota failure does not mutate previous library (1.648473ms)
✔ corrupt storage requires explicit recovery and exact raw comparison (1.546836ms)
✔ unsupported locking refuses unsafe writes (0.967499ms)
ℹ tests 17
ℹ suites 0
ℹ pass 17
ℹ fail 0
ℹ cancelled 0
ℹ skipped 0
ℹ todo 0
ℹ duration_ms 236.390482
```

Releases: None returned by GitHub. No hosted demo URL was verified. A source archive or preview release is not a hosted deployment.

Remaining checks:

- Public HTTPS deployment
- Native browser bookmark manager import
- Broader naming review

This refresh corrects the publication checkpoint and preserves the earlier dated workflow results. It does not claim fresh browser, hardware or production security acceptance. Next: complete the listed acceptance checks and verify a persistent HTTPS deployment where required.
