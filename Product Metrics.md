# **Product Metrics**

We track five product metrics. Four measure D.A.W.N. in use: whether the media helps residents, and whether staff and the tablet are fast and easy enough. The fifth measures how well the code is tested. Each metric checks one of the requirements in [Functional and Non-Functional Requirements](Functional%20and%20Non-Functional%20Requirements.md).

## **Scope**

* The four usage metrics come from the beta at St. Ann's Home and are reported every two weeks during it. Before the beta, they are checked on test devices.
* They use only structured data (plays, ratings, times and touch counts), never names, room numbers or medical information (NFR-1).
* Targets for helpfulness are a starting point. The team will revisit them after the first two weeks of the beta.

## **Summary**

| \# | Metric | Target | Checks | Data available today |
| ----- | ----- | ----- | ----- | ----- |
| 1 | Staff-Rated Helpfulness | 80% of staff plays are rated; 50% of rated plays helped | FR-21 | Yes |
| 2 | Time and Taps to Play | 90% of staff plays start within 3 taps and 10 seconds | NFR-10 | No: the staff app doesn't log it yet |
| 3 | Tablet Start Time | 90% of staff plays start on the tablet within 3 seconds | NFR-11 | Yes |
| 4 | Tablet Touches | Touches per tablet per day go down over the beta | NFR-8 | No: the server doesn't store touches yet (#381) |
| 5 | Test Coverage | Server 70%; tablet and shared code 90% | NFR-15 | Yes |

## **1\. Staff-Rated Helpfulness**

**Target:** staff rate at least 80% of the plays they start, and at least 50% of rated plays are rated **Helped** or **Helped a lot**.

**How it's measured:** after a staff-started play ends, staff rate it on five steps within 5 minutes: much worse (−2), worse (−1), no change (0), helped (1) or helped a lot (2). Each play's rating is stored with it in the `Playback` table. We report the share of staff plays that were rated, and the share of rated plays at 1 or 2, overall and per situation (such as "wants to go home").

**Why it matters:** this is the project's main evidence of whether D.A.W.N. helps. Staff are in the room when a clip plays, so they see its effect directly. Facial recognition and sentiment analysis were considered and rejected, because the facial expressions of people with dementia may not reflect how they feel. Per-situation results show which kinds of media work and which don't.

## **2\. Time and Taps to Play**

**Target:** 90% of staff plays start within 3 taps and 12 seconds of staff opening the app, and rating a play takes 1 tap.

**How it's measured:** the staff app records the time it was opened and each tap until Play is pressed, and sends the count and time with the play. *This isn't built yet.* Until it is, the team times staff by hand during beta visits.

**Why it matters:** staff use D.A.W.N. in the middle of a hard moment with a resident. If finding the right clip takes longer than calming the resident another way, staff won't use it.

## **3\. Tablet Start Time**

**Target:** 90% of staff plays start on the tablet within 3 seconds of staff pressing Play, and fewer than 5% fail or expire.

**How it's measured:** each `Playback` row records when it was requested (`requestedAt`) and when it started on the tablet (`startedAt`). We report the time between them, and the share of staff plays that ended **failed** or **expired** (the tablet didn't accept the command within 30 seconds).

**Why it matters:** a slow or failed start loses the moment and makes staff stop trusting the app. Media cached on the tablet may be needed to meet 3 seconds on facility Wi-Fi.

## **4\. Tablet Touches**

**Target:** the number of touches per tablet per day goes down over the course of the beta.

**How it's measured:** the tablet records each touch with the screen it was on (day, night or playing), what was under the finger (a widget, an empty cell or playing media) and the gesture, but never a position or text. Repeated taps within 2 seconds count as one try. *The tablet already sends these in batches, but the server has no endpoint to store them yet (#381).* We report touches per tablet per day, and which widgets and screens are touched most.

**Why it matters:** the tablet is designed to never need a tap (NFR-8). Frequent touches suggest a resident is confused or expects something to happen, and screens that draw many touches may need a redesign.

## **5\. Test Coverage**

**Target:** server code 70% statement coverage; tablet and shared code 90%. The caregiver and staff apps get targets once they have tests.

**How it's measured:** `go test -cover ./...` for the server and `jest --coverage` for the tablet and `shared/`. As of November 23, 2026, the server is at 57% and the tablet and shared code at 97%; the caregiver and staff apps have no automated tests. *Coverage isn't reported in CI yet.*

**Why it matters:** D.A.W.N. was inherited and has been largely rebuilt, and changes can break existing behavior without anyone noticing. Every pull request must pass its tests before merging (NFR-15), but passing tests only protect the code they cover. Coverage shows which parts of the system have no tests behind them.
