# PR366 review improvements

Published source: `db36cfffcde51cb600f5907e6b75a2cafca3e763`. Tested tree: `afc752b781ef2e5b6d1f93a89867203a704a8b0b`. Base: `85999075b5737740237a1b2c796019c78e5fff58`.

The existing Too many requests response now has an explicit translated wait-and-retry explanation in English, Spanish and French. Three new tests fail against the preceding PR revision (13 existing tests pass) and pass after the fix. Form contents and canonical API rating values survive the error, language changes and a mocked retry. No client-side retry timer, live request or server-rate-limit change is introduced.

The new feedback dictionary namespace is now placed at the start rather than the end of each locale file. All pre-existing entries are unchanged. Three-way text merges of the overlapping files with PR363 succeed in both orders and retain both namespaces. No upstream merge was performed.

## Fresh verification

- Standalone PR366: 878 tests pass, 0 fail, 77 suites. TypeScript, lint and default production build all exit0.
- Temporary combined source from PR363, PR364, PR365 and the updated PR366: 904 tests pass, 0 fail, 80 suites. TypeScript, lint and default production build all exit0.
- Both lint runs retain 32 pre-existing warnings; zero errors. No tests, dependencies, lockfile, compiler rules or source settings were relaxed.
- Six nonpersistent WebKit component captures show the actual localized rate-limit error at desktop/mobile sizes in light/dark themes. Fetch is mocked; no production feedback was sent.
- All tracked source files were compared against the validation copies after execution. The combined source manifest and provenance heads are included.

Local environment: macOS arm64 / Node24.20.0 / isolated case-sensitive workspace using existing complete lockfile-matched dependencies. An initial cached production build timed out without a code diagnostic. Its generated cache was moved aside and the unchanged source passed a fresh default build. The timeout and successful retry logs are both retained; no claim is made that the cache was conclusively the only cause. Official Ubuntu/Node20 CI is separate and remains subject to maintainer approval.

No source changes to PR363/364/365. No payment commitment or receipt is claimed; A$0 spent. AI-assisted implementation and testing; no independent human or native-speaker review claimed.

## Prior evidence

Root-level artifacts outside review-polish/ preserve the earlier PR366 revision and its original localization tests/screenshots. Current evidence is under review-polish/.
