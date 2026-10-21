# Issue 160: feedback form translations

Source: `3fc4bd69003790fd3cc58f5ffb8ef71c5e6b5e99`; tested tree: `180d09b190574ce51dd1af4dbc7010d6d5d4f890`; base: `85999075b5737740237a1b2c796019c78e5fff58`.

All feedback controls, placeholders, ratings, status messages and known API error messages now use the existing English/Spanish/French dictionaries. Canonical API rating values remain English; changing language preserves input and selection. Existing error messages map to translation keys; unknown server messages receive the translated generic fallback. This does not redesign transport, server validation, submission races or focus management.

## Results

- Before patch: 2 new cases pass, 11 fail on actual untranslated UI/state.
- After patch: all 13 new cases pass; the existing form test also passes.
- Full suite: 875 tests pass, zero fail, all 77 suites pass.
- TypeScript: exit0, zero diagnostics.
- ESLint: exit0, zero errors; 32 existing warnings elsewhere, none in changed files.
- Default Next.js/Turbopack build: exit0.
- All 263 tracked files compared byte-for-byte with the test copy, and the published tree matches the tested source. Existing tests, dictionary entries, dependencies and config are unchanged.

## Component checks

Six native nonpersistent WebKit screenshots cover en/es/fr, light/dark and 390/900 pixel widths. Dialog and page bounds fit the tested viewports. Visible Charlotte exercise opened the Spanish dark form, entered synthetic feedback and observed translated success. The fetch boundary is mocked; no live feedback is submitted. These are component fixtures, not a deployed end-to-end test.

Local environment: macOS arm64, Node24.20.0, isolated case-sensitive workspace with the existing complete exact-lockfile dependencies reused. Official Ubuntu/Node20 CI is separate and not claimed to have passed.

Implementation, translation drafting, testing and review were AI-assisted. No independent human or native-speaker review is claimed. Assignment and reward eligibility were queried and remain unconfirmed. No payment amount, escrow, currency/network or receiver is promised. A$0 spent.
