# **PR Comparison Metrics (Process)**

We track five pull request metrics each deadline iteration. Together they keep PRs small and quick to review, spread authoring and reviewing evenly across the team, keep focus-area owners involved in their areas, and make sure every member understands the whole system.

## **Scope**

* Metrics cover PRs for the DAWN project merged into canary or a feature branch. PRs for the internal website are excluded.  
* Every PR is scoped to exactly one ticket and has at least one approving review before it is merged.  
* Every ticket carries its project labels (Caregiver, Carepartner, Staff Member) and technical labels (Server, Cloud, Security, Frontend, UI/UX). Other labels, such as Documentation, Hardware and Internal Tools, are not used.  
* Metrics are calculated per deadline iteration. This semester's iterations are Sep 27 – Oct 20 and Oct 21 – Dec 3\.

## **Summary**

| \# | Metric | Target | Why we track it |
| ----- | ----- | ----- | ----- |
| 1 | PR Size | 90% of PRs have ≤ 500 lines and ≤ 15 files changed | Keeps PRs small enough to review quickly and thoroughly |
| 2 | Review and Merge Time | 90% of PRs are reviewed within 24 business hours and merged within 48 | Keeps PRs from blocking teammates or piling up before a deadline |
| 3 | Author and Review Balance | Each member's PRs authored and reviewed stay within 60% of an even share | Prevents anyone from being overloaded with authoring or reviewing |
| 4 | Focus-Area Coverage | 95% of PRs are authored or reviewed by an owner of their focus area | Keeps each specialist involved in their own area |
| 5 | Breadth of Knowledge | Each member works on at least 5 of 6 breadth labels per iteration | Ensures everyone understands how the whole system works |

## **1\. PR Size**

**Target:** 90% of PRs have 500 or fewer changed lines and 15 or fewer changed files.

**How it's measured:** lines added plus lines deleted, and the number of files changed. Test files, documentation (Markdown files such as CLAUDE.md) and generated files (package lockfiles, Swagger output) are not counted.

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
| Staff Member, Frontend, UI/UX | Haroon Aziz |
| Server | Jay Doody |
| Cloud | Ashton Michelstein |
| Security | David Holt |

**Why it matters:** it keeps our specialization strong. A specialist checks every change in their area and maintains its quality standards, even when someone else does the work.

## **5\. Breadth of Knowledge**

**Target:** each member authors or reviews at least one PR in at least 5 of the 6 breadth labels every deadline iteration.

**How it's measured:** the breadth labels are Caregiver, Carepartner, Staff Member, Frontend, UI/UX and Server. A member covers a label when they author or review a PR whose ticket has that label.

**Why it matters:** every member should understand how the whole system works, so no area depends on a single person. This metric and Focus-Area Coverage work together: pairing a focus-area owner with a non-owner on each PR satisfies both.

Claude Prompt:  
okay, lets take a step back and re-evaluate this entire metric proposal process.

here are some assumptions that should be true for our process:

* all PRs merged into canary (or some other feature branch) have at least one review and approval before being merged  
* all tickets in the backlog are properly tagged with their relevant labels  
  * project-specific labels: caregiver, carepartner, staff member  
  * technical labels: server, cloud, security, frontend, ui/ux  
  * other labels do not matter for these metrics like documentation, hardware, internal tooling, etc  
* any PRs created and merged should not be for internal-website, only for the DAWN project  
* all PRs are scoped to exactly one ticket

here is what is bad that is currently happening:

* PRs are too large, and thus, take longer to review (both are bad)  
* PRs are not being reviewed and authored consistently across the team (some are doing way more reviewes than authors and vice versa)  
* Not every team member has a breadth of knowledge across the whole system (whether this is reviewing or authoring PRs given a specific label/topic)

here is what is going good:

* Everyone has a specialization based on their respective focus area (they are the ones creating the tickets, working on them, and/or reviewing them for their specific focus area)

i want to ensure both the bad things stop happening and the good things are kept up. in an ideal world, the following is true:

* 90% of PRs are 500 lines or fewer lines and touch 15 or fewer files (excluding docs like CLAUDE.md and test files)  
* 90% of PRs are reviewed within 24 hours (business days, not including weekends), and merged within 48 hours (whether the initial review was an approval or rejection, the PR should be approved and merged by this date)  
* ideally, everyone has an equal number of PRs authored and reviewed as each other (ie. 60 PRs created means each person has 10 authored and 10 reviewed). lets say numerically that people should stay within 60% of these values (in the example above, each person should have between 6 and 16 PRs authored and 6-16 PRs reviewed, anything over/under is a concern for over/under-performance)  
* at least one team member with a focus area relating the ticket should be either the PR author or PR reviewer 95% of the time (ie. a ticket marked caregiver, frontend, carepartner is either authored or reviewed by one of Alex, Tess or Haroon)  
* each deadline iteration, all team members should have at least one PR either authored or reviewed for all project-specific labels (caregiver, carepartner, staff member), frontend, ui/ux and server.

tell me if these are valid metrics and what exactly they show for us/what problems they solve. keep this simple (1-3 sentences) and create mock data for it based on the provided repo.

