# **PR Comparison Metrics (Process)**

We track five pull request metrics each deadline iteration. Together they keep PRs small and quick to review, spread authoring and reviewing evenly across the team, keep focus-area owners involved in their areas, and make sure every member understands the whole system.

## **Scope**

* Metrics cover PRs for the DAWN project merged into canary or a feature branch. PRs for the internal website are excluded.  
* Every PR is scoped to exactly one ticket and has at least one approving review before it is merged.  
* Every ticket carries its project labels (Caregiver, Carepartner, Staff Member) and technical labels (Server, Cloud, Security, Frontend, UI/UX). Other labels, such as Documentation, Hardware and Internal Tools, are not used.  
* Labels live on tickets, not PRs, so each PR borrows its ticket's labels: from the issue it links ("Closes #481"), or if it links none, from the issue number its branch name starts with (`481-nighttime-hours`). A PR with neither counts toward no focus area.  
* Every night, the `pr-metrics.yml` workflow in the DAWN repo collects the raw facts about each merged PR (size, review times, labels). The team site's /metrics page computes the five metrics from them.  
* Metrics are calculated per deadline iteration. This semester's iterations are Sep 27 – Oct 20 and Oct 21 – Dec 3\.

## **Summary**

| \# | Metric | Target | Why we track it |
| ----- | ----- | ----- | ----- |
| 1 | PR Size | 90% of PRs have ≤ 750 lines and ≤ 15 files changed | Keeps PRs small enough to review quickly and thoroughly |
| 2 | Review and Merge Time | 90% of PRs are reviewed within 24 business hours and merged within 48 | Keeps PRs from blocking teammates or piling up before a deadline |
| 3 | Author and Review Balance | Each member's PRs authored and reviewed stay within 60% of an even share | Prevents anyone from being overloaded with authoring or reviewing |
| 4 | Focus-Area Coverage | 95% of PRs are authored or reviewed by an owner of their focus area | Keeps each specialist involved in their own area |
| 5 | Breadth of Knowledge | Each member works on at least 5 of 6 breadth labels per iteration | Ensures everyone understands how the whole system works |

## **1\. PR Size**

**Target:** 90% of PRs have 750 or fewer changed lines and 15 or fewer changed files.

**How it's measured:** lines added plus lines deleted, and the number of files changed. Test files, documentation (Markdown files such as CLAUDE.md), generated files (package lockfiles, `go.sum`, Swagger output) and images are not counted.

**Why it matters:** large PRs take longer to review and are reviewed less thoroughly. Small, focused PRs keep reviews fast and make defects easier to catch.

## **2\. Review and Merge Time**

**Target:** 90% of PRs receive a first review within 24 business hours and are merged within 48 business hours.

**How it's measured:** business hours (weekends excluded) from when the PR is opened for review until its first review, and until it is merged into canary. A first review that requests changes still counts as the first review; the PR must still be approved and merged within 48 hours.

**Why it matters:** slow reviews block teammates and let PRs pile up in review right before a deadline, when the active backlog must be empty.

## **3\. Author and Review Balance**

**Target:** each member's PRs authored and PRs reviewed both stay within 60% of an even share.

**How it's measured:** the even share is the total number of PRs merged in the iteration divided by six team members. The acceptable range is 40% to 160% of that even share. For example, 60 PRs gives an even share of 10, so each member should author 4–16 PRs and review 4–16 PRs. Above the range means a member is overloaded in that role; below it means they are under-contributing.

**Why it matters:** authoring and reviewing balance each other out. When one member authors far more than their share, the rest of the team has to review far more than theirs. Tracking both numbers catches overloaded authors and overloaded reviewers.

## **4\. Focus-Area Coverage**

**Target:** 95% of PRs are authored or reviewed by at least one owner of a focus area on the PR's ticket.

**How it's measured:** a PR passes when its author or reviewer owns any of its ticket's labels.

| Label | Focus-area owner |
| ----- | ----- |
| Caregiver | Alex Bruno |
| Carepartner | Tess Hacker |
| Staff Member | Haroon Aziz |
| Frontend | Tess Hacker, Haroon Aziz |
| UI/UX | Alex Bruno, Haroon Aziz |
| Server | Jay Doody |
| Cloud | Ashton Michelstein |
| Security | David Holt |

**Why it matters:** it keeps our specialization strong. A specialist checks every change in their area and maintains its quality standards, even when someone else does the work.

## **5\. Breadth of Knowledge**

**Target:** each member authors or reviews at least one PR in at least 5 of the 6 breadth labels every deadline iteration.

**How it's measured:** the breadth labels are Caregiver, Carepartner, Staff Member, Frontend, UI/UX and Server. A member covers a label when they author or review a PR whose ticket has that label.

**Why it matters:** every member should understand how the whole system works, so no area depends on a single person. This metric and Focus-Area Coverage work together: pairing a focus-area owner with a non-owner on each PR satisfies both.
