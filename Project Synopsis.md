## **D.A.W.N: Daily Awareness & Well-being Navigator**

### **Introduction/Background**

Dementia affects an estimated 47 million people worldwide, a number projected to nearly double by 2040 as the population ages. Patients with dementia often wake up to a confusing world. They don’t know where they are or how they got there. They can’t say what day or even what season it is. This disorientation produces anxiety and isolation, which in turn has been shown to accelerate cognitive decline. Additionally, those tasked with caring for someone with dementia—often a family member or loved one—are left with this immense responsibility with potentially little outside help.

### **Terminology**

* **Caregiver:** person primarily responsible for caring for someone with dementia  
* **Carepartner:** person with dementia paired with a caregiver

### **Project Description**

D.A.W.N. (Daily Awareness & Well-being Navigator) is an orientation tool inspired by the premise of the movie *Fifty First Dates*. It is a tablet-based application mounted to the inside of a carepartner’s room that serves to reorient the patient each morning. It plays a video-based morning greeting from a loved one to remind the patient where they are, how they got there, and that they are loved and were not abandoned. It introduces the potential staff and faculty of the housing community by name and photo and reviews the day’s agenda—medication, meals, events, etc. The carepartner’s tablet is paired with a caregiver interface that caregivers use to upload media and adjust what the tablet displays.

### **Current State**

This project is currently in beta testing at St. Ann’s Home in Irondequoit NY, hosted on an RIT server. The existing codebase is clean, well-organized, and well-documented, with a backlog already in place. The team this year is therefore inheriting a working system, not starting from scratch. Gerry Garavuso, a retired project manager and 16-year guide for Multidisciplinary Senior Design in KGCOE, serves as project sponsor and client to bring both domain context and ongoing availability for requirements feedback. Tim Anderson, a faculty member at St. Ann’s, serves as the team's primary point of contact at the facility. Requests involving facility logistics, resident access, or scheduling are typically routed through Gerry to Tim. Drew Saur, the team's senior product coach, provides process and technical guidance throughout the term and is kept informed via weekly meetings.

### **Objectives**

* **Validate product direction through iterative, evidence-based feature discovery.** The project currently lacks sufficient research into which features genuinely reduce patient anxiety and disorientation versus which merely seem plausible. This term prioritizes rapid prototyping and beta deployment as a discovery mechanism by building features to test hypotheses, not to lock in a final feature set.  
* **Establish a reliable feedback loop between the tablet application and the development team.** Without structured, ongoing signals from real usage, feature decisions remain guesswork. Collecting telemetry and caregiver-reported feedback should provide the team with enough data to determine which features are valuable and which are unnecessary or detrimental.  
* **Increase confidence in what to prioritize.** Given the lack of established research on this specific patient population and use case, decisions about what to build next should be driven by what beta data actually shows, not assumption.  
* **Reduce dependency on RIT infrastructure.** Hosting the application independently of RIT's environment improves the project's long-term sustainability beyond any single academic term or team.  
* **Improve the project's viability as an ongoing, multi-team effort.** This includes making the codebase accessible to outside contributors and ensuring documentation is sufficient for next year's team to onboard without relying on this year's team being available.

### **Scope**

#### **In Scope (for the upcoming year)**

* **Feature discovery via rapid prototyping.** Build and deploy a small number of candidate features (to be identified early in the term, primarily based on sponsor input) as testable prototypes rather than fully polished features. Prioritize speed of iteration over completeness.  
* **Beta cohort expansion.** Grow the beta test group at St. Ann's Home beyond its current size, within the constraints of what the facility and sponsor can support (target cohort size to be finalized with Gerry and Tim before implementation begins).  
* **Telemetry instrumentation.** Implement logging on the caregiver and carepartner applications sufficient to measure feature usage and engagement (e.g., which segments patients interact with, session frequency, time-of-day patterns) — scoped to what's needed to evaluate prototyped features, not a general-purpose analytics platform.  
* **Caregiver feedback mechanism.** Establish a lightweight, low-overhead way for caregivers/staff to report qualitative observations alongside telemetry data (exact format TBD).  
* **Hosting migration.** Move application hosting from the RIT server to AWS, covering deployment and environment configuration; this does not include a broader database or architecture redesign unless the migration surfaces a blocking issue.  
* **Open-source preparation.** License the repository and prepare it for external visibility (README, contribution guidelines, license file). Does not include actively recruiting or managing outside contributors this term.  
* **Documentation handoff.** Update requirements, architecture, design, and test documentation to a standard sufficient for next year's team to onboard without needing this year's team's direct involvement.

#### **Out of Scope**

* Finalizing a permanent feature set  
* Automated video calling/conferencing integration (Zoom, FaceTime, etc.)  
* Voice assistant integration  
* Motion/presence-based activation  
* Rollout beyond beta cohort

### **Software Architecture**

#### **Current Architecture**

The D.A.W.N. system is built as a monorepo with a shared Go backend and two purpose-built frontends. Caregivers use a React web app to upload photos, videos, audio, and text prompts, and schedule them onto their carepartner's daily agenda. That content is served through a single REST API backed by Postgres (for structured data and scheduling) and MinIO (for media storage). A separate React Native app exists for the carepartner and is deployable as a kiosk-style Electron app on a Raspberry Pi or as an Expo app for iOS. It displays the scheduled content to the carepartner in a simplified interface, pairing to the system via a device code rather than a login.

Architecturally, the backend follows a clean layered design (routes, controllers, services, models) organized by domain, which keeps the system easy to extend as new content and widget types are added. The two frontends are decoupled from each other but share the same API and data model, allowing the caregiver's scheduling decisions to flow directly into what the carepartner sees, with the whole system deployable as a single containerized stack.

*Insert future architecture diagrams here*

#### **Planned Architecture Changes**

* **Hosting:** migrate from current hosting to AWS (RDS for Postgres, S3 replacing MinIO for uploaded media, ECS/ECR for the Go backend, ALB, AWS Certificate Manager, and Route 53 for accepting HTTPS traffic and forwarding it to the app container).

### **Software & Hardware Requirement Specifications**

#### **Development:**

* **Software:** Go 1.25+, Node.js/npm, PostgreSQL \+ MinIO (run locally or via docker-compose.dev.yml), Expo CLI with Expo Go or a simulator for the mobile app.  
* **Hardware:** any standard laptop; a phone/simulator to test the carepartner app.

#### **Deployment:**

* **Software:** Docker \+ Docker Compose running docker-compose.yml (Go server \+ Postgres 15 \+ MinIO), a domain for autocert/TLS (ports 80/443 open), and an Expo build for the kiosk device.  
* **Hardware:** hosted server; a Raspberry Pi 4+ (arm64) or iPad for the kiosk display

### **Methodology**

The team will follow Scrum, chosen specifically because of the uncertainty around how both caregivers and carepartners will actually use D.A.W.N.—the same uncertainty driving the project's discovery-oriented objectives. The team will build simple, prototyped features in short sprints, measure their real-world effectiveness, and adjust based on that data rather than assumption. The team will also participate in standard Scrum ceremonies (daily virtual asynchronous standups, sprint planning, retrospectives, backlog refinement).

Quality is enforced through a CI/CD pipeline (automated unit, integration, and Selenium browser testing on every pull request), mandatory two-reviewer code review with one-business-day time limit, and a feature-branch workflow that isolates work before merging into a canary integration branch and finally into main. Every feature must be demonstrated and approved by Gerry before merging into main, giving the sponsor a direct checkpoint on what actually ships. Progress and quality are tracked via code coverage, burndown charts, and carepartner response feedback.

### **Challenges & Risk Assessment**

* **Designing for a vulnerable, non-verbal-feedback population.** Patients can't reliably self-report whether a feature helps or confuses them, and the team has no prior domain experience with dementia care.  
  *Mitigation:* lean on telemetry \+ caregiver feedback together (per objectives), and validate new features with Gerry/staff before wide deployment.  
* **Inherited codebase and migration risk.** The team is extending an existing system, not building fresh. Undocumented assumptions could slow onboarding.  
  *Mitigation:* consult the existing documentation for any assumptions made by our team, or reach out to previous developers/ask Gerry as a second resort.  
* **Sponsor and facility dependency.** Beta cohort expansion and prioritization decisions depend on Gerry's availability and St. Ann's cooperation, both outside the team's control.  
  *Mitigation:* set a regular check-in cadence and confirm cohort logistics early, not late-term.

### **Conclusion**

D.A.W.N. enters this term as an inherited, working system rather than a blank-slate project. This is a real advantage, but also something that reframes the team's job as validation and refinement rather than initial design. The core challenge is determining which features actually help a population that can't easily tell you so directly; that's why this term's objectives center on rapid prototyping, telemetry, and caregiver feedback rather than a fixed feature roadmap. In parallel, the team will reduce dependency on RIT infrastructure and strengthen the project's documentation and licensing so it can continue as a multi-year effort beyond this team's involvement. Success this term is not necessarily a finished product, rather it is more like a system the next team can pick up with clear evidence about what's worth building on.