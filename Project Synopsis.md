# **D.A.W.N: Daily Awareness & Well-being Navigator**

## **Introduction/Background**

Dementia affects an estimated 47 million people worldwide, a number projected to nearly double by 2040 as the population ages. People with dementia often wake up to a confusing world. They don't know where they are or how they got there, or even what day or season it is. This disorientation causes anxiety and isolation, which has been shown to speed up cognitive decline. The people caring for them, often family members, carry this responsibility with little outside help.

## **Terminology**

* **Carepartner (resident):** the person with dementia, living in a care facility.
* **Caregiver (family):** the person primarily responsible for a carepartner, usually a family member. Caregivers supply the content the tablet shows.
* **Staff:** the facility's floor staff, who can start and stop content on a resident's tablet.

## **Project Description**

D.A.W.N. is an orientation tool, inspired by the premise of the movie *Fifty First Dates*. A tablet mounted in the resident's room shows a calm, always-on screen and plays video/audio messages from their family. The resident never has to touch it.

* **Always-on screen:** the day of the week and the time of day (morning, afternoon, evening) in very large type, a family photo, and small extra widgets the family chooses, such as the weather. At night the screen turns dim and warm.
* **Playback:** family members record or upload videos, audio and photos and schedule them to play at set times, such as a morning greeting at 8 AM. Content plays full screen, with no tap needed, and the screen returns to the always-on view afterward.
* **Staff control:** staff pick a clip from their phone by the resident's situation (for example, "wants to go home") or by family member, and it begins on the tablet within a few seconds. They can stop it, and afterward rate how it went.

The system is three apps on one backend:

| App | Used by | What it does |
|---|---|---|
| Caregiver web app | Family | Sign in, pair a tablet, upload or record media, lay out the screen, schedule playback, and preview what the tablet shows |
| Carepartner tablet app | Resident | Shows the always-on screen and plays scheduled or staff-started content |
| Staff app | Facility staff | Picks a clip for a resident's situation, starts and stops it on their tablet, and rates how it went |

## **Current State**

D.A.W.N. is an inherited, working system that this year's team has largely redesigned. The tablet app was rebuilt for an Android tablet, and the family app gained a new UI, email + one-time code authentication, screen layout editor, in-app recording, and a live preview. A new staff app lets floor staff play a clip on a resident's tablet from their phone. The beta has not started yet. The team is preparing for it, which includes moving hosting to AWS, running the tablet unattended for several days, and working through a consent and privacy checklist with each facility. St. Ann's Home in Irondequoit, NY is the planned beta site.

Gerry Garavuso, a retired project manager and 16-year guide for Multidisciplinary Senior Design in KGCOE, is the project sponsor and client, providing domain context and ongoing feedback on requirements. Tim Anderson, a faculty member at St. Ann's, is the team's main contact at the facility; development requests about facility logistics, resident access or scheduling go directly to Tim. Drew Saur, the team's senior product coach, provides process and technical guidance and meets with the team weekly. Ann Marie Cook, CEO of Lifespan, is an external stakeholder who supports the idea and wants to see how D.A.W.N. works in different settings before investing further.

## **Objectives**

* **Find out which features actually help.** There is little research on which features reduce anxiety and disorientation for this population. The team builds features as small, testable prototypes and uses the beta to learn what works, rather than locking in a final feature set.
* **Build a feedback loop from real use.** The tablet reports every play (scheduled, staff-started or tapped, and whether it started, finished, stopped or failed). Together with feedback from caregivers and staff, this data should show which features are valuable and which are unnecessary or harmful.
* **Let beta data drive priorities.** Decisions about what to build next should come from what the beta shows, not from assumptions.
* **Reduce dependency on RIT infrastructure.** Hosting on AWS keeps the project running beyond any one academic term or team.
* **Open source the project.** The code is already public on GitHub but has no license yet. The team will recommend an open-source license to Gerry, then add it along with contribution guidelines and a README that outside developers can follow, so others can use, study and build on D.A.W.N.
* **Make D.A.W.N. a sustainable, multi-year effort.** Documentation should let next year's team onboard without needing this year's team.

## **Scope**

### **In Scope (this year)**

* **Three-app redesign.** Rebuild the tablet and caregiver apps, and build the staff app, whose play and stop commands reach the tablet in real time.
* **Feature discovery through rapid prototyping.** Build a small number of candidate features, chosen mainly from sponsor input, as testable prototypes. Speed of iteration matters more than polish.
* **Beta preparation and launch.** Confirm the participating facilities, complete consent, privacy and security work (data inventory, privacy notice, keeping resident names out of logs, requiring sign-in or a device token on every API request, and encrypting data in transit and at rest), and run a beta at St. Ann's Home.
* **Telemetry.** Record what the tablet shows and plays, and how caregivers use their app, enough to evaluate the prototyped features. This is not a general-purpose analytics platform.
* **Caregiver feedback.** A lightweight way for caregivers to tell the team how D.A.W.N. is working for their carepartner, and a notification when staff rate their media as having helped.
* **Hosting migration.** Move hosting from the RIT server to AWS before the beta, including automated deploys, secrets management and HTTPS on the production domain, then retire the RIT server.
* **Open-source preparation.** Add a license, contribution guidelines and a README overhaul. Actively recruiting outside contributors is not included.
* **Documentation handoff.** Keep requirements, architecture, design and test documentation good enough for next year's team to onboard on their own. The requirements are in [Functional and Non-Functional Requirements](Functional%20and%20Non-Functional%20Requirements.md), broken into user stories in the [Feature List](Feature%20List.md).

### **Out of Scope**

* Finalizing a permanent feature set
* Video calling (Zoom, FaceTime, etc.)
* Voice assistant integration
* Motion or presence-based activation
* Rollout beyond the beta facilities

## **Software Architecture**

### **Current Architecture**

D.A.W.N. is a monorepo with a Go backend and three frontends:

* **Backend (Go):** one REST API that is the only part of the system talking to the database, file storage and outside services. Postgres stores structured data (accounts, screen layouts, schedules, play records), and MinIO stores the media files. Code is organized by domain in layers (routes, controllers, services, models), which keeps it easy to extend.
* **Caregiver web app (React + TypeScript + Vite):** caregivers sign in with Google or with a code sent by email. In production, the Go server serves this app and the API from the same address.
* **Carepartner tablet app (Expo / React Native):** runs on a Samsung Galaxy Tab A9+ (Android). Tablets pair with a caregiver's account through a short code shown on screen rather than a login. Tablets get the app from Expo's build service, and later changes arrive over the air. A web version of the tablet app powers the caregiver's live preview.
* **Staff app (Expo / React Native):** runs on staff members' own Android and iOS phones. Staff sign-in is in progress. Its play and stop commands reach the tablet over a WebSocket.
* **Shared rules:** a small TypeScript folder used by both the caregiver app and the tablet, so the caregiver's preview always matches what the tablet shows (awake hours, screen grid, what is playing).

The whole backend, including the built caregiver app, runs as a single containerized stack (Docker Compose).

*Insert future architecture diagrams here*

### **Planned Architecture Changes**

* **Hosting:** move from the RIT server to AWS before the beta, with automated deploys from GitHub Actions. After the beta, each facility may get its own AWS account.
* **Media caching:** the tablet downloads all of a resident's media ahead of time so a staff-started clip starts quickly.

## **Software & Hardware Requirement Specifications**

### **Development:**

* **Software:** Go 1.25+, Node.js/npm, Docker with Docker Compose (Postgres and MinIO), and Android Studio with an Android emulator (JDK 17 or 21) for the tablet and staff apps. Maestro runs the tablet's end-to-end tests.
* **Cloud services:** GitHub for code, reviews and CI (GitHub Actions); Google Cloud for the Google sign-in client; an Expo account for tablet builds and over-the-air updates (EAS); and API keys for OpenWeather and NewsAPI for the weather and news widgets. A mail account (SMTP) is only needed to test sign-in emails; in development the server logs them instead.
* **Hardware:** any standard laptop; an Android emulator or tablet to test the tablet app, and Android and iOS phones or emulators to test the staff app.

### **Deployment:**

* **Software:** the Docker Compose stack (Go server, Postgres 15, MinIO) on AWS, a domain with HTTPS, and Expo's build and update service (EAS) for the tablet app.
* **Hardware:** a hosted server, one Samsung Galaxy Tab A9+ (11-inch, landscape) per resident room, and staff members' own Android or iOS phones with the staff app installed.

## **Methodology**

The team uses **Deadline-Driven Development**, a hybrid of Shape Up and Kanban. Instead of fixed-length sprints, each iteration works toward a real deadline, such as a sponsor demo or a deployment, and starts with a meeting with Gerry (the product owner) to agree on what must be done by then. This fits a project whose priorities shift with what the team learns from the sponsor, the facility and the beta. At each deadline, the active backlog is empty, `canary` is merged into `main`, and the backlog is refined within two days for the next deadline.

Work is tracked on a GitHub Projects board, with each ticket labeled by focus area (such as caregiver, carepartner, staff, server or cloud), each led by a team member. Every ticket gets its own branch and small pull requests. The author reviews their own change first; then one teammate reviews it before it merges into `canary`, and two review each release into `main`. Automated checks run on every pull request. The team meets with Gerry and coach Drew Saur weekly. Process is measured through pull request metrics (size, review time, balance and breadth across focus areas), and the product through staff feedback once the beta begins. See the **Development Methodology** artifact for details.

## **Challenges & Risk Assessment**

* **Designing for a vulnerable population that can't easily give feedback.** Residents can't reliably say whether a feature helps or confuses them, and the team has no prior experience with dementia care.
  *Mitigation:* combine telemetry with caregiver and staff feedback, follow strict design rules on the tablet (no taps required, no motion, very large text), and validate new features with Gerry and facility staff before deploying them widely.
* **Privacy and consent.** The beta involves residents of a care facility, which may bring HIPAA, consent and research-approval requirements. If St. Ann's is covered by HIPAA, it will likely need to own the AWS account that holds resident data, and a Business Associate Agreement (BAA) must be signed before residents are enrolled. The team doesn't yet have a contact on St. Ann's compliance team, and no one has been identified to sign the BAA.
  *Mitigation:* get in touch with St. Ann's compliance team early, through Gerry and Tim, to settle who owns the AWS account, whether a BAA is needed and who signs it. Keep medical information and resident names out of telemetry and logs, keep a data inventory, and complete a consent and privacy checklist with each facility before the beta starts.
* **Hosting migration before the beta.** The beta depends on a stable AWS deployment that isn't finished yet.
  *Mitigation:* move the existing Docker Compose stack to AWS as is, and test the tablet unattended for several days before the beta.
* **Inherited codebase.** Undocumented assumptions in the existing system can slow the team down.
  *Mitigation:* check the existing documentation first, then ask previous developers or Gerry. Keep documentation current as the code changes.
* **Dependency on the sponsor and facility.** Beta logistics and priorities depend on Gerry's availability and St. Ann's cooperation, both outside the team's control.
  *Mitigation:* hold regular check-ins and confirm beta logistics early in the term, not late.

## **Conclusion**

D.A.W.N. began this year as an inherited, working system, and the team has turned it into a redesigned three-app product built around a calm, hands-free tablet. The team's main job is to learn which features actually help a population that can't easily say so, which is why the year centers on prototypes, telemetry and caregiver feedback rather than a fixed roadmap. In parallel, the team is moving hosting to AWS and preparing the project's documentation and license, so it can continue for years after this team. Success this year is not a finished product. It is a beta-tested system that the next team can pick up, with clear evidence about what is worth building on.
