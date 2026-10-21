# Issue 164: build the prepared transaction before serialization

Source: `99e46ab48a44779cbfd74dfa29f8ba0fe2af27fd`; tested tree: `165548e6df5c711b98b5e0c7903c81e472d92c46`; base: `85999075b5737740237a1b2c796019c78e5fff58`.

One-line production change: call `.build()` on the result of `assembleTransaction()` and remove the `any` cast. The SDK TransactionBuilder has no toXDR; the built Transaction does. Eight new tests retain real SDK builder/serialization while fully mocking RPC and wallet boundaries. The fake signer echoes a synthetic unsigned envelope: no actual signing, broadcast or live halt operation is performed.

## Results

- Before patch: 4 pass / 4 fail with the original toXDR TypeError.
- Patched full suite: 870 pass / 0 fail across 77 suites (including all 8 new cases).
- TypeScript: exit 0, no diagnostics.
- ESLint: exit 0, no errors; 32 existing warnings elsewhere.
- Default Next.js/Turbopack production build: exit 0.
- All 263 tracked files matched the tested copy, and the published Git tree matches the local tree. Existing tests, dependencies and configuration are unchanged.

Local environment: macOS arm64 / Node 24.20.0 / case-sensitive HFSX workspace with the existing complete exact-lockfile dependency installation reused. This is not upstream Ubuntu/Node 20 CI. Local test/build output is included here; official CI/review remain separate gates.

AI-assisted implementation, review and testing; no independent human review claimed. Assignment and payment eligibility were queried on #164 but are not confirmed. No fee, escrow or wallet destination has been promised. A$0 spent.
