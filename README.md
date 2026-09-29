# Caloyaa | Manual QA case study

A test-planning and defect-analysis project based on the real Caloyaa cafe ordering flow. The [public storefront](https://caloyaa-cafe.github.io/) lets customers browse food, build a basket and send an order request. The owner dashboard receives and manages orders. This repository documents the test approach, reusable manual test cases and selected issues found while the system was built and checked in September 2026.

> Scope note: This is a case study, not a certification or a claim that every listed test passed. The test cases contain expected results; only observations backed by the project history are marked observed. No customer orders, credentials, payment identifiers or private dashboard access details are published here.

| Document | What it contains |
| --- | --- |
| [Test plan](TEST-PLAN.md) | Objectives, scope, approach, risks, entry/exit criteria and deliverables |
| [Test cases](TEST-CASES.md) | Customer and owner-flow checks, with expected results and evidence status |
| [Defect log](DEFECT-LOG.md) | Three real issues, observed impact, fixes and verification limits |

## System under test

- Customer-facing [Caloyaa storefront](https://caloyaa-cafe.github.io/): menu, basket, checkout and optional WhatsApp fallback.
- Owner-only order dashboard: order intake, refresh, notifications and status changes. Its authenticated route is intentionally not linked here.
- Order-alert integration: Telegram delivery and browser-side sound/pop-up. Alert behavior is different when a mobile browser is in the background.

## What this demonstrates

Requirements-based manual test design, positive and negative cases, integration checks, regression planning, defect reproduction and honest separation of observed results from proposed tests. The artifacts are written in English for QA portfolio review. They contain no invented coverage percentages, pass rates or customer data.

**Project context:** Caloyaa is a real cafe operated by Nikhil Partap Singh. Documentation assembled from the live storefront and September 28 build/test notes. The owner should review any future execution results before claiming them as personal hands-on testing.
