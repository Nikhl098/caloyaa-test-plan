# Defect log | Issues observed during September 28 build/test

These are historical defects from the build work, not newly discovered open bugs. Evidence is summarized without publishing order data, bot credentials or owner-only access details. Severity is a QA assessment, not a measured business impact.

## BUG-01 | Dashboard did not discover orders while phone tab was backgrounded

- **Area / severity:** owner dashboard refresh and alerts / High
- **Observed:** owner had to pull-to-refresh to find a new test order; the expected alarm did not sound while the phone browser was backgrounded. Mobile browser throttling was identified as a constraint.
- **Expected:** on returning to dashboard, it promptly fetches pending orders; an independent notification path alerts the owner while the tab is not active.
- **Change:** periodic foreground polling, refresh on page return, visible pop-up/sound controls and Telegram alert path were introduced.
- **Retest evidence:** a test order later reached the dashboard on the refresh cycle. The owner confirmed the test-sound button worked. This does not prove browser sound in every locked-phone state; Telegram must be tested separately.

## BUG-02 | Telegram alert did not arrive for a test order

- **Area / severity:** order notification integration / High
- **Observed:** owner explicitly reported that nothing arrived in Telegram for a test order, despite the portal work in progress.
- **Expected:** each new accepted order triggers a single matching Telegram notification.
- **Diagnosis and change:** build notes traced failed alert delivery to asynchronous request handling in the Worker; alert dispatch was moved to a lifecycle-aware path, with request body handling corrected before dispatch.
- **Retest evidence:** Telegram API reported success for a later test, and the owner confirmed the alert reached the phone. A subsequent final test had no recorded owner receipt confirmation, so do not infer a universal pass or guarantee zero duplicate notifications.

## BUG-03 | Owner dashboard stuck at "Loading..." after an update

- **Area / severity:** dashboard availability / High
- **Observed:** after an update, the page stayed on "Loading...", blocking normal use of the dashboard.
- **Expected:** the order list loads, or a recoverable error is shown.
- **Change:** the breaking update was corrected and the dashboard became usable again. Existing orders were reported as saved during the interruption.
- **Retest evidence:** subsequent test orders were visible on the dashboard, and owner actions continued. The exact affected browser versions, outage duration and root-cause code diff are not established here.

## Follow-up

Rerun TC-08, TC-10 and TC-11 on the current deployed build and record browser/device, test order identifier (redacted in public evidence), actual result and date. Keep customer and payment details out of public screenshots.
