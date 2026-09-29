# Test plan | Caloyaa ordering flow

**Version:** 1.0, September 29, 2026  
**Type:** Manual functional and integration test plan  
**System:** [Caloyaa public storefront](https://caloyaa-cafe.github.io/) and authenticated owner order dashboard

## 1. Objectives

1. Check that a customer can browse available items, build a basket and send a complete order request without losing item, quantity or price details.
2. Check that an order accepted by the server becomes visible to the owner, with clear state and timely alerting.
3. Check the backup WhatsApp route and payment instructions without treating an entered UTR as proof of payment.
4. Catch regressions in mobile/background behavior, page loading and integration alerts before release.

## 2. Scope

**In:** menu browsing; sold-out item behavior; basket changes; checkout fields; pickup/table/delivery request choices where offered; order submission; owner dashboard loading, refresh, alerts and status changes; Telegram alert delivery; WhatsApp fallback; basic responsive/mobile and accessibility checks.

**Out:** real payment settlement or automatic UPI verification, delivery logistics, Zomato/Swiggy systems, penetration testing, production load testing and private customer data. A payment or order request must not be marked fulfilled merely because a transaction ID was typed.

## 3. Strategy

- Derive positive, negative and boundary cases from the visible storefront and owner workflow. Record expected results before execution.
- Use clearly labeled test orders only, coordinate with the owner, and clean them up where the app supports it. Never use a real customer's personal information.
- Run a short smoke pass after each deployment: storefront loads, basket/checkout works, server accepts a test request, dashboard shows it, and the owner can act on it.
- Exercise integration behavior separately: foreground tab, background/locked phone and reopening; Telegram notification; WhatsApp fallback. Browser audio/autoplay and mobile power restrictions must be considered.
- For each run, note date, browser/device, build or commit, actual result and evidence. Retest fixed defects, then repeat critical flow regression cases.

## 4. Risks and mitigations

| Risk | Mitigation |
| --- | --- |
| Background mobile tabs can be throttled, delaying dashboard polling or sound | Test real device/background transition; use a separate phone-level notification route; do not promise guaranteed delivery |
| Telegram/API dependency fails even when dashboard succeeds | Check alert receipt separately from order creation; keep order visibility and backup route testable |
| Deploy introduces a JavaScript loading error | Smoke-test dashboard load immediately after every change and retain rollback path |
| Test orders may be mistaken for real work | Prefix TEST, coordinate with owner, and remove/reject where possible |
| UTR typed without actual payment | State clearly that owner verifies payment independently before acceptance |

## 5. Environment and data

Public production storefront and an authenticated owner session with explicit owner access. Use a phone browser plus a desktop browser when available. Use synthetic names and test orders, no real phone numbers or actual UPI payment. Record exact version and device per execution; this plan does not claim a completed cross-browser matrix.

## 6. Entry and exit criteria

**Entry:** build is deployed; owner access works; menu and checkout are reachable; test data and cleanup method are agreed; notification channel is connected if alert cases are run.

**Exit:** critical smoke flow passes on the release build; high-severity defects are fixed and retested or explicitly accepted by owner; test orders are accounted for; known limitations and unresolved results are logged. A test with no observed result is not a pass.

## 7. Deliverables

This plan, the linked [test cases](TEST-CASES.md), a dated execution record when cases are run, the [defect log](DEFECT-LOG.md), and a concise release summary with unresolved risks. No invented schedule, staffing level, test count or pass-rate target is asserted.
