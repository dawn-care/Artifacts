## **Development Methodology**

### **Overview**

Our team uses **Deadline-Driven Development**, which is a hybrid of Shape Up and Kanban with some other additional features. We work towards meaningful, often external deadlines (e.g. important demo) instead of fixed cycles or sprint lengths. We start each new iteration with a meeting with our sponsor to decide what needs to be done before the deadline

### **Planned activities**

**Weekly Meetings**

We will have meetings from 5:00-6:15pm every Tuesday and Thursday, and from 8:15-9:15 on Mondays online. 

Tuesday meetings are with our sponsor and coach where we go over our Agenda and 4up (see Agendas and 4Ups below). We will conclude every meeting with our goals for the upcoming week and the next meeting. 

Thursdays will be developer meetings where we start each meeting with what we’ve been working on throughout the week, what we plan to do in the upcoming week, and if we have any existing blockers. These meetings will be used to go over high level tasks like assignments for the course and architectural decisions. 

Monday meetings will be used for creating the Agenda and 4up, as well as going over any blockers identified online throughout the week. If applicable, we will go over the product and active backlogs to assign and refine tasks to be completed by the next deadline (see Deadline-based Iterations below).

**Deadline-based Iterations**

Rather than using sprints as our iterations, we will define meaningful and tangible deadlines based on needs from the sponsor or stakeholders, deployments, developer schedules, or any other meaningful events that would change the deadline. These deadlines will be a hard date where the following should be true:

* All tasks in the active backlog have been completed, meaning Active Backlog, In Progress and In Review should be empty  
* A merge from canary to main should be performed  
* A backlog refinement meeting will be held within the following two days to repopulate the active backlog

### **Roles**

**Scrum Master**  
The Scrum Master will facilitate our process and make sure we are following it effectively. They will lead and organize all internal team meetings (see Weekly Meetings above). They will also review this document and other process related tasks in order to update/improve it as the project grows.

**Product Owner**   
Our sponsor, Gerry, will act as the product owner. During Tuesday meetings (see Weekly Meetings above), he will provide insight on our development process, verify we are meeting his standards, and propose ideas for the project's future.

**Development Team**  
The development team will be responsible for designing, implementing, testing, and delivering tasks from the product backlog to the product owner. They will actively communicate with the product owner, as well as each other when any blockers arise.

Within the development team, each team member will have focus areas relating the project, product or both: Tess Hacker (DevOps, Careparnter Dev), Ashton Michelstein (Cloud Dev), Alex Bruno (Caregiver Dev), Haroon Aziz (Frontend, Staff Dev), David Holt (Security Dev), and Jay Doody (Backend Dev). Features emerging for each of these focus areas will be defined by the development team and expanded on by the lead(s) of the respective focus areas (see Features below)

**Stakeholders**

Stakeholders include individuals or groups who have an interest in or are affected by the project, such as customers, users, sponsors, or organizational representatives. If a stakeholder wants to reach out regarding the project, communication will go through the product owner (besides Tim). We have two major external stakeholders that are not direct users of the application: Tim Anderson (St. Ann’s) and Ann Marie Cook (Lifespan).

Tim is our primary contact at St. Ann’s, where we will perform beta testing. All communication to St. Ann’s will go through Tim, and communication to Tim will either go through the product owner, or the development team's designated sponsor communicator. Tim will provide similar input to the project as the product owner to verify the product is functional.

Ann Marie is the CEO of Lifespan and is a fan of the product in theory. She would like to see how this works in various environments before investing further into the product.

### **Process Standards**

**CI/CD Pipeline**  
A CI/CD pipeline will be established through GitHub to automatically build, test, and validate changes submitted to the project. The pipeline will run on pull requests and changes to designated branches to identify build failures and regressions early. Successful changes can then be deployed to the appropriate development or testing environments.

Further internal tooling will be developed to support the development teams process. This will include AI scripts for consistent documentation (ticket descriptions, pull request descriptions, etc) and a Discord pull request bot that notifies the team when a pull request is created, merged, or a review is submitted.

**Code Reviews**  
All pull requests will go through a code review process with two phases. The pull request creator must review their code (manually or AI assisted) prior to publishing their pull request. Once a pull request is published, the creator will assign a reviewer, who will manually review and either approve it or request changes. One reviewer is required for feature branches merged into canary, while two are required for merges from canary to main (see Development Workflow below).

**Communication**  
Communication between the product owner and stakeholders will be done through email with the primary contact being the development team's sponsor communicator. Internal communication between the development team and with the coach will be through Discord.

The project website will be used to organize technical and non-technical tasks for the project. This will be a public website, accessible by the coach, product owner, stakeholders, and development team, with the primary focus being for the development team’s internal use. The website will help the development team stay organized and have all resources relating to the project accessible from a single website.

### **Tools**

**Git and GitHub**  
Git will be used for version control throughout development. GitHub will host the project's repositories and provide the platform for managing branches, pull requests, code reviews, and the CI/CD pipeline. All development work will follow our defined branching and pull request workflow.

**GitHub Projects**  
A GitHub Projects board will be used to organize and track project tasks. We will use priorities and labels to group our tickets into focus areas (see Development Team above). The two major ticket types on the board will be tasks and bugs (which will be identifiable through labels). The board will be used to maintain visibility on features within the development team.

### **Metrics and measurements**

**PR Metrics (Process)**  
We will track five PR metrics each deadline iteration. Together they keep PRs small, quick to review, spread authoring and reviewing across the team, keep focus-area experts involved in their areas, and make sure every member understands the whole system. The table below is an outline of these metrics and our internal website has the actual data:

| Metric | Target | Importance |
| :---- | :---- | :---- |
| PR Size | 90% of PRs have \<= 750 LOC and \<= 15 files changed | Keeps PRs small enough to review quickly and thoroughly |
| Review and Merge Time | 90% of PRs are reviewed within 24 business hours and merged within 48 | Keeps PRs from blocking teammates or piling up before a deadline |
| Author and Review Balance | Each member’s PRs authored and reviewed stay within 60% of an even share | Prevents anyone from being overloaded with authoring or reviewing |
| Focus-Area Coverage | 95% of PRs are authored or reviewed by a focus-area expert for at least one of the ticket’s focus areas | Keeps each specialist involved in their own area |
| Breadth of Knowledge | Each member works on at least 5 of 6 focus areas per iteration | Ensures everyone understands how the whole system works |

The PR size target metric excludes test files and docs from the total file count. The review and merge time metric implies business hours are Monday-Friday (weekends not included). Author and review balance refers to an even share as all six team members contribute an even number of PRs and review an even number of PRs (ie. if we have 60 PRs in a deadline, the fair share would be each member authoring and reviewing 10 each, meaning each person has 4-16 authors and reviews). This metric has the largest margin as each deadline may focus on different focus areas more than others, meaning some members might have a heavier iteration in reviews and some in authors. Focus area coverage refers to the roles of each team member, see the table below for this specification. Breadth of knowledge addresses the following six focus areas: server, frontend, ui/ux, caregiver, carepartner, staff member.

The following assumptions can be made about our process to ensure these metrics are tracked effectively:

* All PRs (excluding merges from canary → main) have at least one review before merging  
* All tickets in the backlog and PRs are properly tagged with their relevant labels  
* All PRs tracked by these metrics are merged into the DAWN section of the repo (not the Internal-Website)  
* All PRs are scoped to exactly one ticket and each feature branch starts with the issue number of that ticket (ie. 121-caregiver-feature-slug)

| Label | Caregiver | Carepartner | Staff | Server | Frontend | UI/UX | Cloud | Security |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| **Devs** | Alex | Tess | Haroon | Jay | Tess & Haroon | Alex & Haroon | Ashton | David |

**Staff Feedback (Product)**  
We will collect feedback from staff members and use it to evaluate whether the system meets the needs of carepartners. Feedback will be reviewed regularly and used to identify usability issues, missing functionality, device effectiveness, and any opportunities for improvement. Relevant feedback will result in new or modified backlog items. This cannot be tracked until we go into beta testing with St. Ann’s.

### **Development Workflow**

**Features**  
All features will be defined and approved by the entire development team, but tickets created in the backlogs will be defined by developers who have the corresponding focus area. These tasks will be created initially in the product backlog, and moved to the active backlog if it needs to be completed by the upcoming deadline. The developer who creates the ticket will be assigned to it, or they will communicate with another developer to hand off the ticket to them.

**Branching**  
The main branch will act as our production branch, meaning only production-ready code will be merged to it. Once we begin beta testing, this branch will only be merged into at the end of a deadline (see Deadline-based Iterations above). This branch will only receive merges from canary, or critical hotfixes.

A canary branch will act as the development branch, meaning all reviewed and approved feature branches will be merged into it prior to the deadline. As long as all feature branches are in canary by the end of the deadline, merge order and location does not matter (excluding main), but a general guideline is that one-off features should be merged into canary, and larger features should be shipped to canary at once upon their completion.

Feature branches will be created for each ticket in the product backlog. Multiple feature branches can exist for the same ticket, but there should never be multiple tickets completed on one feature branch.

**Pull Requests**  
Everyone should submit many small, focused pull requests rather than large changes containing multiple unrelated features. Each pull request should address a specific piece of functionality defined in a ticket. This will make code reviews more manageable and will allow issues to be identified and addressed quickly.

If the change affects the UI, photos or videos will be added to the pull request description. However, reviewers are still encouraged to pull the branch and manually test the app to verify these results.

### **Documentation**

**Google Drive**  
TODO

**Meeting Notes**  
Meeting notes will be taken by the development team notetaker for sponsor meetings and other meetings with external stakeholders (see Weekly Meetings above). Notes will be reviewed by development team members whenever they miss a meeting.

**Agendas and 4Ups**  
Agendas and 4Ups will be completed by the development team weekly (see Weekly Meetings above). These will be used to facilitate sponsor meetings, as well as identify needs from the sponsor/coach. Risks are identified by the development team for the development team to manage (if there are any not addressed online prior to the documents creation).