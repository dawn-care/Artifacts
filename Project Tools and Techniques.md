## **Project Tools and Techniques**

### **Project Management**

* **GitHub:** hosts the code (the `dawn-care` organization), pull requests and code reviews.
* **GitHub Projects:** the task board. Tickets are tasks or bugs, labeled by focus area.
* **Team site:** the internal website, hosted on Vercel. It shows meeting agendas and 4Ups, the published artifacts, tasks from the GitHub Project, and pull request metrics.
* **Google Drive:** meeting agendas, 4Ups, notes and project documents.
* **Discord:** day-to-day team communication, plus bots that post pull request activity.
* **Email:** communication with the sponsor and stakeholders.

### **Development Tools**

* **VS Code:** the code editor.
* **draw.io:** diagrams, such as the domain model, stored as files in the Artifacts repo.
* **Docker and Docker Compose:** run the full backend locally (Go server, PostgreSQL and MinIO).
* **Android Studio and the Android emulator:** run the tablet and staff apps without a device.
* **Expo:** builds and runs the tablet and staff apps. EAS Build makes the tablet app, and EAS Update sends changes to tablets over the air.
* **Swagger (swaggo):** API documentation generated from the Go code, served at `/swagger/`.
* **Goose:** database migrations, applied automatically when the server starts.
* **Testing:**
  * Go's built-in tests, with testify and go-sqlmock (no real database needed)
  * Jest and React Native Testing Library for the tablet app and the shared rules
  * Maestro for the tablet app's end-to-end flows on an emulator or tablet
  * ESLint and the TypeScript compiler for the caregiver, tablet and staff apps
* **GitHub Actions:**
  * CI builds, lints and tests each part of the repo on every pull request.
  * A nightly job collects pull request metrics for the team site.
  * Pull request events are forwarded to the team's Discord bots.
* **AI tools:** help write consistent ticket and pull request descriptions, and help authors review their own changes before opening a pull request.

### **Implementation Tools**

* **Backend:** Go, with the chi router and a REST API.
* **Database:** PostgreSQL.
* **Media storage:** MinIO, an S3-compatible object store.
* **Caregiver web app:** React, TypeScript, Vite, Tailwind CSS and React Router.
* **Tablet app:** React Native with Expo and Expo Router, running on a Samsung Galaxy Tab A9+ (Android).
* **Staff app:** React Native with Expo, Expo Router and NativeWind (Tailwind CSS), on staff members' own Android and iOS phones.
* **Shared rules:** plain TypeScript shared by the caregiver app and the tablet.
* **Real-time commands:** a WebSocket that carries staff play and stop commands to the tablet.
* **Sign-in:** Google OAuth, or a one-time code sent by email (SMTP).
* **Widget data:** OpenWeather for the weather widget, NewsAPI for news, and ESPN's public scoreboard data for sports.
* **Hosting:** the Docker Compose stack, currently on an RIT server with HTTPS certificates from Let's Encrypt (autocert). It is moving to AWS before the beta.
