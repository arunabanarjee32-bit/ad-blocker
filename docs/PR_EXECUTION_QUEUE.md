# Ordered implementation and pull-request execution queue

**Updated:** 15 November 2026 (Asia/Kolkata). **Owner:** repository maintainer. **Goal:** implement and validate a competitive Chrome MV3 ad blocker by merging one tested, reviewable increment at a time.

The GitHub issues below represent **future PR scopes**, not already-written code. Do not create empty PRs for unfinished features. New implementation PRs should be opened only when there is a real diff and the preceding gates are satisfied. Final license and commercial distribution decisions belong to the owner.

## Reviewed foundation and repository routing

The requested destination is `renoukhan39-bit/ad-blocker`. The original PRs and implementation issues exist in `rejoansardar23/ad-blocker`; that repository is read-only through the current connection. The starting main trees were identical. Existing implementation was ported and fixed, preserving the original source links:

| Original work | Destination | Verified result |
|---|---|---|
| [Original PR #3](https://github.com/rejoansardar23/ad-blocker/pull/3) | [Merged PR #1](https://github.com/renoukhan39-bit/ad-blocker/pull/1) | Generated lockfile, npm ci, 10 Node tests and 10 Chromium cases; [CI](https://github.com/renoukhan39-bit/ad-blocker/actions/runs/43646943965) |
| [Original PR #4](https://github.com/rejoansardar23/ad-blocker/pull/4) | [Merged PR #2](https://github.com/renoukhan39-bit/ad-blocker/pull/2) | Corrected full-rule comparison, 14 Node tests and 10 combined Chromium cases; [CI](https://github.com/renoukhan39-bit/ad-blocker/actions/runs/43647171852) |
| [Original PR #17](https://github.com/rejoansardar23/ad-blocker/pull/17) | This documentation port | Issue links and dependency gates reviewed; original PR is not modified |

Browser evidence: Chromium 158.0.8127.18, Playwright 1.65.0, CI Node v22.23.4. Local Node v24.22.1 checks/build pass; local browser execution is blocked by the workspace's network/socket restrictions. See [Chromium guide](CHROMIUM_TEST_GUIDE.md). These are synthetic fixture results, not production or competitor benchmarks.

The issue links below intentionally point to the original requirement scopes. Implementation PRs and any newly needed tracking issues belong in the destination repository. Do not treat issue/PR numbers as interchangeable across repositories.

## Complete work in this order

Current status: [foundation audit](FOUNDATION_AUDIT.md) has pinned preliminary findings and automated dependency controls. Original issue #2 remains blocked on owner distribution/license direction and full candidate validation. Issues are disabled in this fork (HTTP 410), so do not assume local issue creation succeeded. Original security issue #5 is independently eligible after the merged foundation; imports/compilers remain gated.

| Order | Issue | Dependency | Deliverable |
|---|---|---|---|
| 03 | [#2](https://github.com/rejoansardar23/ad-blocker/issues/2) | Owner must select license and distribution approach | Pinned foundation + dependency + license audit and ADR; no copied unapproved code |
| 04 | [#5](https://github.com/rejoansardar23/ad-blocker/issues/5) | Destination PRs #1 and #2 (merged) | Permission, privacy, settings consistency and MV3 security fixes with browser regressions |
| 05 | [#6](https://github.com/rejoansardar23/ad-blocker/issues/6) | Issue #2 | Licensed filter-source catalog and provenance; no unapproved subscriptions bundled |
| 06 | [#7](https://github.com/rejoansardar23/ad-blocker/issues/7) | Issue #2 and #6 | A chosen, tested filter-to-DNR compiler with quotas/coverage checks |
| 07 | [#8](https://github.com/rejoansardar23/ad-blocker/issues/8) | Issue #7 | Filter updates, integrity checks, versioning, last-known-good rollback |
| 08 | [#10](https://github.com/rejoansardar23/ad-blocker/issues/10) | Issue #7 | User rules, exception priority, validated import/export, persistence tests |
| 09 | [#9](https://github.com/rejoansardar23/ad-blocker/issues/9) | Chrome test baseline, browser constraints | Dynamic cosmetics, accessible reversible element picker |
| 10 | [#11](https://github.com/rejoansardar23/ad-blocker/issues/11) | Issue #6, #7 | Tracker/nuisance/region filtering profiles with attribution and false-positive checks |
| 11 | [#12](https://github.com/rejoansardar23/ad-blocker/issues/12) | Stable filtering core | Polished accessible dashboard and honest production-compatible diagnostics |
| 12 | [#14](https://github.com/rejoansardar23/ad-blocker/issues/14) | Feature-complete candidate | Objective competitor benchmark and performance regression corpus |
| 13 | [#13](https://github.com/rejoansardar23/ad-blocker/issues/13) | Core + security + benchmark results | Privacy/security/legal review, release ZIP, changelog, store readiness |
| 14 | [#15](https://github.com/rejoansardar23/ad-blocker/issues/15) | Chrome release stability | Edge and Firefox adapter feasibility + verified browser builds |
| 15 | [#16](https://github.com/rejoansardar23/ad-blocker/issues/16) | Separate platform approval | Desktop and DNS product research, cost/security ADRs |

**Original request:** aim for a world-class AdGuard/uBlock/Ghostery competitor while conserving Codex credits. That means a verified baseline, compatible reused components, low site breakage and strict feature acceptance, **not** a mass merge of four open-source products.

## Definition of an implementation PR

Every PR should:
- Link its issue and concrete acceptance criteria.
- Identify existing functionality and reused/borrowed components with pinned commits and licenses.
- Have focused code changes; avoid changing many modules without need.
- Include unit and/or Chromium integration tests covering positive and negative behavior.
- Include exact command results, CI URL, browser version and restrictions.
- Explain new manifest permissions, privacy and security implications.
- Update `docs/FEATURE_MATRIX.md`, `docs/IMPLEMENTATION_CHECKLIST.md`, and ADRs honestly.
- Leave production completeness and competitor benchmarks **unclaimed** until tested.

## Codex review/merge protocol

1. Open the **oldest eligible PR**, read its diff, issue and this plan.
2. Run `npm run check` and `npm run build`, then `npm run test:e2e` using the committed Chromium tooling. Install dependencies with `npm ci` and the pinned browser as documented.
3. Diagnose and fix failures on the PR branch (or propose review changes), re-run CI and check browser regressions.
4. Review security, licensing, source attribution and data collection effects.
5. **Merge only when checks and scope acceptance pass** and the maintainer has approved any unresolved licensing/release choice.
6. Update main, rebase next PR if needed and repeat.
7. For future issues, implement the smallest working increment, open a PR, review and merge before starting dependent work.

## Blockers to return to the maintainer

- Choice of proprietary vs source-available vs open-source distribution and contributor terms
- Payments, publishing or changing repo visibility
- Third-party code or filter datasets with ambiguous copyright/redistribution terms
- Permissions that materially expand browsing access or data collection
- Competing architectural proposals requiring product direction
- Any security vulnerability not safely addressable in ordinary PR review

If blocked, create an issue stating evidence, choices and a recommendation, not a vague request to "fix all".

## Progress tracking

The [60-step checklist](IMPLEMENTATION_CHECKLIST.md) remains the high-level product goal and issue tasks are the implementation queue. Only mark completed after merged source, tested behavior and documentation evidence. Planned tasks do not imply work in the background; Codex runs only when explicitly tasked.
