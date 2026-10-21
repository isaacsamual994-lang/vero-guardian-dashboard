# Explorer hash normalization: issue 170

Published source: `844dca8a65acc161c612f4b14b98a6f75bfb2593`
Base: `85999075b5737740237a1b2c796019c78e5fff58`
Tested source tree: `e57bdbc53023883b0a3f5e1e178055f339dd2447`

This is a one-line helper fix plus 14 tests. It lowercases the trimmed transaction hash as the existing comment promises; URL prefix and invalid-input behavior are unchanged. No UI/layout, transaction submission, wallet integration or hash-format validation is added.

## Verified local results

- New helper tests: 14 passed. Before the patch, 4 normalization cases failed and 10 compatibility cases passed. No runtime/setup failures were counted as regressions.
- Full Jest suite: 876 passed, zero failed, all 77 suites passed.
- TypeScript: exit 0, no diagnostics.
- ESLint: exit 0, zero errors, 32 existing warnings outside changed files.
- Default production build (`next build`, Turbopack): exit 0.
- All 263 tracked files were compared byte-for-byte with the validation copy. The published Git tree matches the tested tree.

## Environment and limitation

macOS arm64, Node v24.20.0, isolated case-sensitive HFSX workspace. Reused the existing complete dependency installation for this exact package-lock; no package or lockfile changes. The first build rejected a linked node_modules outside the project root; the same dependency directory was temporarily placed inside the test project for the successful build, then restored and checked. No compiler setting or check was relaxed.

No visual changes are introduced, so no new UI screenshots are claimed. Official upstream Node20/Ubuntu CI and maintainer review remain separate gates. Prior withdrawn PRs also addressed this issue; this contribution independently follows the published issue and includes before/after test evidence.

Implementation and testing were AI-assisted under the account owner's authorization. No independent human review is claimed. GrantFox eligibility is discretionary; no reward amount, assignment, escrow or payment is confirmed. Cost of this attempt: A$0.
