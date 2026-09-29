# Manual test cases | Caloyaa

**How to use:** Record build, device/browser, date, actual result and evidence for each run. The expected outcomes below are specifications, not blanket claims of execution. Use only owner-approved synthetic test orders. No real payment or customer details.

| ID | Area | Steps / test data | Expected result | Evidence status |
| --- | --- | --- | --- | --- |
| TC-01 | Storefront smoke | Open public storefront on phone and desktop | Hero, menu and ordering controls render without error | Storefront publicly reachable; device matrix not recorded |
| TC-02 | Basket | Add an available item, increase quantity, then remove it | Count and total update each time; empty-basket state returns | Proposed regression case |
| TC-03 | Sold-out item | Open an item marked sold out and try to add it | Item cannot enter basket; state is clear | Proposed regression case |
| TC-04 | Checkout fields | With an item in basket, try empty required details and then valid synthetic details | Incomplete request is blocked with useful error; valid request can continue | Proposed regression case |
| TC-05 | Order integration | Submit a clearly marked TEST order through storefront | Server acknowledges request; exactly one corresponding order appears in owner dashboard | September 28 build notes record a test order reaching dashboard after server 201; rerun on current build |
| TC-06 | Price and payment copy | Change basket quantity and inspect total, payee and UTR text | Displayed amount changes correctly; copy says UTR alone does not verify payment | Current public page shows independent verification warning; arithmetic not recorded |
| TC-07 | WhatsApp backup | Open fallback, inspect prefilled text without sending | Item, quantity, total and request details are readable; no message sent during test | September 28 build notes record link/text inspection; no message sent |
| TC-08 | Dashboard load | Open owner dashboard after deployment | Orders render or actionable error appears; not stuck on Loading... | Real Loading... regression logged in defect log; retest on each build |
| TC-09 | Foreground refresh | Leave dashboard open, create a TEST order | New order appears without manual reload and alert is shown | Build notes record test order visible within refresh interval; device-specific alert result separate |
| TC-10 | Background/return | Put phone browser in background/lock, create TEST order, reopen | New order is fetched on return; stale screen does not hide it | Earlier background failure documented; device-specific retest needed |
| TC-11 | Telegram integration | Create one TEST order with owner monitoring bot | One alert reaches owner; order details match dashboard | Owner confirmed receipt for a September 28 test after fix; later final test receipt unconfirmed |
| TC-12 | Owner action | Accept a pending TEST order with default prep value, then inspect state | State changes once; no duplicate action or blank-time failure | Build notes report accept flow fixed; repeat on current build |
| TC-13 | Duplicate/invalid submit | Double tap submit or enter invalid checkout data | No duplicate live order; clear validation/error | Proposed negative case; no result claimed |
| TC-14 | Responsive/accessibility | Navigate menu and checkout at narrow width using keyboard/screen reader basics | Controls remain readable, labeled and reachable | Proposed exploratory check |

**Execution evidence:** September 28 build/test notes for TC-05, TC-07, TC-09 and TC-11 were recorded during development, not a full independent regression run. Rows marked proposed must be executed before reporting pass/fail. Browser/background notification delivery is not guaranteed by a web tab alone.
