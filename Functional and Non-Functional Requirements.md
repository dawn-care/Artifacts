# **D.A.W.N. Functional and Non-Functional Requirements**

These are the system-level requirements for D.A.W.N.: what the three apps and the backend must do, and the qualities they must have. The [Feature List](Feature%20List.md) breaks each requirement into user stories, and its **Maps to** column links each story back to the requirement it satisfies.

* **Functional requirements (FR)** say what the system does.
* **Non-functional requirements (NFR)** say how well it does it: privacy, security, usability, performance and so on.
* **Verified by** says how the team checks that a requirement is met.

## **Functional requirements**

### **Carepartner tablet**

| ID | Requirement | Verified by |
| :---- | :---- | :---- |
| FR-1 | The tablet shall show an always-on screen with the day and time of day, plus the widgets the caregiver placed on it (photo, message, reminders, weather, sports, news). | Jest component tests; Maestro flow on the tablet |
| FR-2 | The tablet shall play scheduled media full screen at its set time, with no tap needed, and return to the always-on screen when it ends. | Jest tests of the playback state machine; Maestro flow |
| FR-3 | The tablet shall play or stop media when staff send the command, and tell the server whether it received the command and how the play ended. | Go tests of the WebSocket hub; Jest tests; manual test with the staff app |
| FR-4 | The tablet shall show a dim, calm night screen outside the carepartner's awake hours. | Jest tests of the shared night-hours rules |
| FR-5 | The tablet shall pair with a caregiver's account using a code shown on its screen, and keep working without anyone signing in. | Go service tests; Maestro pairing flow |
| FR-6 | The tablet shall report every play to the server: when it starts, finishes, stops or fails, and what started it. | Go service tests; Jest tests |
| FR-7 | The tablet shall show captions and the sender's name and photo on videos. | Jest component tests; review on the tablet |
| FR-8 | The tablet shall show what's coming up in the resident's day (activities, visits, care rounds, today's nurse), with no medication details. | Jest component tests; review with St. Ann's staff |

### **Caregiver web app**

| ID | Requirement | Verified by |
| :---- | :---- | :---- |
| FR-9 | Caregivers shall sign in with a Google account or a one-time code sent to their email, and sign out of every device at once. | Go service and controller tests |
| FR-10 | Caregivers shall record or upload photos, videos and audio, and tag each item with the situations it helps in and the family members in it. | Go service tests; manual test in the browser |
| FR-11 | Caregivers shall lay out the tablet's screen on its 4 × 3 grid and set the carepartner's awake hours. | Go tests of the grid rules; Jest tests of the shared rules |
| FR-12 | Caregivers shall schedule media to play once or repeating daily, weekly or monthly, and skip single days. | Go tests of the recurrence rules |
| FR-13 | Caregivers shall preview the carepartner's screen exactly as the tablet shows it. | Manual comparison with the tablet |
| FR-14 | Caregivers shall pair tablets, care for more than one carepartner, and invite other family members to contribute. | Go service tests; manual test in the browser |
| FR-15 | Caregivers shall add family members and write guidance for staff about each one. | Go service tests; manual test in the browser |
| FR-16 | Caregivers shall receive staff requests for new videos, see which of their clips were played and how they were rated, and be notified when one helped. | Go service tests; manual test in the browser |
| FR-17 | Caregivers shall send the team feedback on how D.A.W.N. is working for their carepartner. | Manual test in the browser |

### **Staff app**

| ID | Requirement | Verified by |
| :---- | :---- | :---- |
| FR-18 | Staff shall sign in, and their role and unit shall limit which residents they see and what they can do. | Go service and controller tests |
| FR-19 | Staff shall find a resident and pick a clip by the situation or the family member asked for, with the best-rated, still-valid clip first. | Go service tests; manual test on a phone |
| FR-20 | Staff shall play and stop a clip on the resident's tablet, and see whether it reached the tablet and how it ended. | Go tests of the WebSocket hub; manual test with a tablet |
| FR-21 | Staff shall rate each play within 5 minutes of it ending, and be reminded about plays they haven't rated. | Go service tests |
| FR-22 | Staff shall see and set a resident's sleeping hours, and nothing shall play during them. | Go service tests; manual test on a phone |
| FR-23 | Staff shall ask the caregiver for a new video when no clip fits, and see each request's status. | Go service tests; manual test on a phone |
| FR-24 | Activities staff shall see which residents to invite to events, mark attendance, and share event photos with consenting residents' tablets and families. | Go service tests; review with the activity director |
| FR-25 | Facility admins shall add general fallback clips and set each resident's photo consent. | Go service tests; manual test on a phone |

## **Non-functional requirements**

| ID | Category | Requirement | Verified by |
| :---- | :---- | :---- | :---- |
| NFR-1 | Privacy | No medical information is stored in telemetry, ratings or video requests: these use structured fields, not free text. Resident names and room numbers stay out of logs. | Review of the data inventory (`docs/data-inventory.md`); code review |
| NFR-2 | Privacy | Event photos are only ever shown for residents whose photo consent is on. | Go service tests |
| NFR-3 | Security | Every API request is authenticated: caregivers by their session, the tablet by a device token from pairing, and staff by their sign-in. Each can reach only its own residents' data and media files. | Go middleware and controller tests |
| NFR-4 | Security | All network traffic is encrypted with HTTPS/TLS, including the server's connections to the database and media storage. | Review of the deployment configuration |
| NFR-5 | Security | The database, media storage and backups are encrypted at rest. | Review of the AWS configuration |
| NFR-6 | Security | Secrets stay out of code and git: leaked keys are rotated, passwords come from the environment or a secrets manager, and Swagger is off in production. | Code review; secret scanning |
| NFR-7 | Compliance | Before the beta, the team has a Business Associate Agreement with the hosting provider, a data inventory, an incident response plan, and sign-off from each facility's compliance team. | Beta go/no-go checklist |
| NFR-8 | Usability | The tablet never requires a tap, and nothing on it moves or flashes on its own apart from playing media. | Review on the tablet |
| NFR-9 | Usability | Tablet text is legible: orientation text 76 px or larger, other text 26 px or larger, contrast 7:1 or better, and touch targets about 20 mm or larger. | Design review; contrast checks |
| NFR-10 | Usability | Staff can start the right clip in 3 taps and under 10 seconds, and rate it in 1 tap. | Timed tests with St. Ann's staff |
| NFR-11 | Performance | A clip starts on the tablet within 3 seconds of staff pressing Play. | Timed tests on the tablet |
| NFR-12 | Reliability | The tablet keeps showing its screen if the Wi-Fi drops, and recovers by itself when it comes back. It runs locked in kiosk mode, with no notifications, settings or exits. | Manual test on the tablet |
| NFR-13 | Platforms | The tablet app runs on the Samsung Galaxy Tab A9+ (Android). The caregiver app runs in current desktop browsers. The staff app runs on staff members' own Android and iOS phones. | Manual test on each platform |
| NFR-14 | Hosting | Before the beta, D.A.W.N. is hosted on AWS, with all data and media moved from the RIT server without loss. | Migration check comparing record and file counts |
| NFR-15 | Maintainability | Every pull request passes CI (build, lint, type checks and tests) and is reviewed by at least one teammate, and two for a release to `main`. | GitHub Actions; branch protection |
