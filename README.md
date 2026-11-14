# Ad Blocker — Chrome MV3 Development Preview

> **Version 0.1.0 · Early implementation · 15 November 2026**  
> A small, original-code browser extension foundation now exists. **Its synthetic Chromium integration suite passes, but it is not production ready.** Full AdGuard/uBlock/Ghostery feature parity is a long-term goal, not a current claim.

## Vision

Build a market-competitive, independently branded, privacy-first ad-blocking software platform, starting with Chrome Manifest V3. Compete on **measured blocking quality, low website breakage, efficient resource use, privacy and user experience**. Use AI coding agents such as Codex Cloud and compatible open-source components only when they reduce total effort without compromising legality, security or maintainability.

**New developer?** Start with [START HERE](docs/START_HERE.md) and the **[60-step implementation checklist](docs/IMPLEMENTATION_CHECKLIST.md)**. You do **not** need the original planning chat.

## Current code: what is actually here

| Capability | Code state | Required proof |
|---|---|---|
| Chrome Manifest V3 package | Chromium fixture verified | Manual install/store review remains |
| Bundled sample blocking rules (few ad networks) | Chromium fixture verified | Limited starter domains only |
| Global protection toggle | Chromium fixture verified | Options control and paused restart pass |
| Per-site trusted website list | Chromium fixture verified | Reload, subdomains, unrelated domains, restart pass |
| Basic cosmetic CSS | Chromium fixture verified | Fixture safety only; broader compatibility pending |
| Popup, options and local settings | Partly verified | Options in Chromium; popup Node tests; toolbar/accessibility review pending |
| Node unit tests and structural checks | CI verified | [Passing GitHub Actions run](https://github.com/rejoansardar23/ad-blocker/actions/runs/43469964379) |
| Dependency-free extension packaging | CI verified | GitHub Actions artifact; synthetic Chromium load verified |
| Comprehensive filter-list support, tracker modes, custom rules, element picker | Not yet built | Milestones P1 |
| Chrome Store release, Chrome/Firefox/desktop/DNS products | Not yet built | Separate approval/testing |

This is a **starter ruleset**, not a market-leading blocker yet. No telemetry or remote code is implemented. Do not make unsupported claims of 100% blocking, exact ad counts or YouTube ad removal.

## Verified CI build

The [successful validation/build run](https://github.com/rejoansardar23/ad-blocker/actions/runs/43469964379) ran structural checks, Node unit tests and the package build and uploaded the `ad-blocker-chrome-unpacked` artifact. The later [combined Chromium run](https://github.com/renoukhan39-bit/ad-blocker/actions/runs/43647171852) passed 14 Node tests and 10 synthetic filtering/reload/restart cases on Chromium 158.0.8127.18. This establishes fixture mechanics, not general website compatibility.

## Quick start

Requires **Node.js 22+** and Chrome/Chromium 121+ for testing.

```bash
git clone https://github.com/renoukhan39-bit/ad-blocker.git
cd ad-blocker
npm run check
npm run build
```

Open `chrome://extensions` → enable **Developer mode** → **Load unpacked** → select `dist/chrome`.

Unit checks and packaging use built-in Node APIs. For the browser suite, run `npm ci --no-audit --no-fund`, `npx playwright install --with-deps chromium`, then `npm run test:e2e`. The extension contains no third-party runtime packages. See [Chromium test guide](docs/CHROMIUM_TEST_GUIDE.md) and [developer setup](docs/DEVELOPER_SETUP.md).

## Documentation map

- **[START_HERE.md](docs/START_HERE.md)** — orientation for humans and AI developers.
- **[IMPLEMENTATION_CHECKLIST.md](docs/IMPLEMENTATION_CHECKLIST.md)** — 60 sequential tasks with status.
- [VISION.md](docs/VISION.md) — competitive goals and principles.
- [PRODUCT_SPEC.md](docs/PRODUCT_SPEC.md) / [FEATURE_MATRIX.md](docs/FEATURE_MATRIX.md) — product requirements and verified/planned states.
- [ARCHITECTURE.md](docs/ARCHITECTURE.md) — existing request/permission design and future modules.
- [ROADMAP.md](docs/ROADMAP.md) — phase delivery and exit gates.
- [REUSE_AND_LICENSES.md](docs/REUSE_AND_LICENSES.md) / [REUSE_AUDIT_TEMPLATE.md](docs/REUSE_AUDIT_TEMPLATE.md) — public repository evaluation before integration.
- [TESTING.md](docs/TESTING.md) / [COMPETITIVE_BENCHMARK.md](docs/COMPETITIVE_BENCHMARK.md) — quality proof and competitor benchmarking.
- [SECURITY_PRIVACY.md](docs/SECURITY_PRIVACY.md) / [SECURITY.md](SECURITY.md) — security, privacy and vulnerability disclosures.
- [CODEX_WORKFLOW.md](docs/CODEX_WORKFLOW.md) / [AGENTS.md](AGENTS.md) — Codex Cloud instructions and credit-saving workflow.
- [DEVELOPER_SETUP.md](docs/DEVELOPER_SETUP.md) / [RELEASE_GUIDE.md](docs/RELEASE_GUIDE.md) — local workflow and future releases.
- [DECISIONS.md](docs/DECISIONS.md) / [RESEARCH_BACKLOG.md](docs/RESEARCH_BACKLOG.md) — open decisions and research.
- [CONTRIBUTING.md](CONTRIBUTING.md) — how to propose scoped, testable changes.

## Reuse strategy and competitor references

We propose **one main modular product repo**, not a blind merge of several GPL codebases. The current minimal implementation is original code without imported upstream engines. Before larger features, audit possible foundations [Very Good AdBlock](https://github.com/chrisbbreuer/very-good-adblock), [Unblock](https://github.com/adyoi/unblock), [Ghostery's adblocker SDK](https://github.com/ghostery/adblocker), [WXT](https://github.com/wxt-dev/wxt) and filtering datasets. Use [AdGuard](https://github.com/AdguardTeam/AdguardBrowserExtension) and [uBlock Origin](https://github.com/gorhill/uBlock) as competitor references, not license-free source.

**Ownership/license warning:** the repo is public, but a project-wide source license is not yet selected. The founder must decide licensing/distribution and external contribution terms before a public release or major third-party code import. Original code ownership does not imply ownership of upstream components.

## Next milestone

Follow the [reviewed dependency queue](docs/PR_EXECUTION_QUEUE.md). Complete the pinned reuse/license audit and owner distribution decision, then eligible settings/security work before importing filter engines or data. Finish accessibility and manual installation gates. Keep the full Node and Chromium suite green for each implementation PR.

**The goal is real working software with evidence.**
