# Assignment 7 — Capstone: Deploy a Production-Grade Stack for The EpicBook

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

In this assignment, you will deploy the EpicBook application as a production-oriented Docker Compose stack on a cloud VM. You will use optimized container images, isolated networks, health checks, persistent MySQL storage, a selected reverse proxy, logging, backup and restore testing, and reliability procedures.

---

# Task 0 — App Discovery and Architecture

## Goal

Review the EpicBook repository and design the intended application architecture.

### Evidence

#### Screenshot 1 — EpicBook Project Structure

Add a terminal screenshot showing the EpicBook project structure after cloning the repository.

![alt text](screenshots/As7T0ss1.png)

---

#### Screenshot 2 — Architecture Diagram

Add a screenshot of your architecture diagram showing:

- Public user
- Reverse proxy
- Frontend
- Backend
- Database
- Docker networks
- Public and private ports
- Persistent database storage

Add your full name inside the diagram or as a clear caption below it.

![alt text](screenshots/As7T0ss2.png)

---

#### Screenshot 3 — Environment Variables and Ports Document

Add a screenshot showing the contents of:

```text
docs/02-env-and-ports.md
```

It must document environment-variable names, internal ports, persistent-data details, and the health-check method. Do not expose real credentials or values.

![alt text](screenshots/As7T0ss3.png)

---

# Task 1 — Create Production Docker Images

## Goal

Create optimized production images for the EpicBook backend and frontend.

### Evidence

#### Screenshot 4 — Backend Dockerfile

Add a screenshot showing `backend/Dockerfile`, including:

- Dependency stage
- Minimal runtime stage
- Production startup command
- Internal backend port
- Non-root user configuration

![alt text](screenshots/As7T1ss4.png)

---

#### Screenshot 5 — Frontend Dockerfile

Add a screenshot showing `frontend/Dockerfile`, including:

- Nginx runtime image
- Static frontend files copied to the Nginx web root

![alt text](screenshots/As7T1ss5.png)

---

#### Screenshot 6 — Docker Ignore Files

Add a screenshot showing both:

```text
backend/.dockerignore
frontend/.dockerignore
```

![alt text](screenshots/As7T1ss6.png)

---

#### Screenshot 7 — Docker Image Builds and Size Comparison

Add a terminal screenshot showing successful builds of:

- Baseline backend image
- Optimized backend image
- Frontend image

The screenshot must also show the baseline and optimized backend image-size comparison.

![alt text](screenshots/As7T1ss7.png)

---

#### Screenshot 8 — Backend Running as Non-Root User

Add a terminal screenshot showing the optimized backend container running as a non-root user.

![alt text](screenshots/As7T1ss8.png)

---

### Notes

Write a short note covering:

- Baseline and optimized backend image sizes
- The image-size reduction achieved
- One Docker layer-caching optimization used
- The security benefit of running the backend as a non-root user

Baseline backend image: 460 MB.

Optimized backend image: 392 MB.

Image-size reduction: 68 MB, approximately 14.78%.

Docker layer-caching optimization: Copied package.json and package-lock.json before copying application source files. This allows Docker to reuse the dependency-installation layer when only source code changes.

Security benefit of non-root execution: The optimized backend runs as the node user (UID 1000) instead of root. This reduces the privileges available to the application and limits potential damage if the application is compromised.

---

# Task 2 — Create the Docker Compose Stack and Networks

## Goal

Create one Docker Compose stack containing the reverse proxy, frontend, backend, and MySQL database.

### Evidence

#### Screenshot 9 — Docker Compose Services

Add a screenshot showing `docker-compose.yml` with all four services:

```text
reverse-proxy
frontend
backend
database
```

![alt text](screenshots/As7T2ss9.png)
![alt text](screenshots/As7T2ss99.png)

---

#### Screenshot 10 — Networks and Named Volume

Add a screenshot showing:

- `front-tier` network
- `back-tier` network
- `db_data` named volume

![alt text](screenshots/As7T2ss10.png)

---

#### Screenshot 11 — Docker Compose Validation

Add a terminal screenshot showing successful Docker Compose validation without exposing environment-variable values or secrets.

![alt text](screenshots/As7T2ss11.png)

---

# Task 3 — Configure Health Checks and Startup Dependencies

## Goal

Configure health checks and ensure services start only after their dependencies are healthy.

### Evidence

#### Screenshot 12 — Backend Health Endpoint

Add a screenshot showing the backend application configuration for the `/health` endpoint.

![alt text](screenshots/As7T3ss12.png)

---

#### Screenshot 13 — MySQL and Backend Health Checks

Add a screenshot showing `docker-compose.yml` with health checks for MySQL and the backend.

![alt text](screenshots/As7T3ss13.png)
![alt text](screenshots/As7T3ss133.png)

---

#### Screenshot 14 — Frontend and Reverse-Proxy Health Checks

Add a screenshot showing:

- Frontend health check
- Reverse-proxy health check
- `depends_on` conditions using `service_healthy`

![alt text](screenshots/As7T3ss14.png)
![alt text](screenshots/As7T3ss144.png)

---

#### Screenshot 15 — Running Healthy Services

Add a terminal screenshot showing Docker Compose service status. The database, backend, frontend, and reverse proxy must be running successfully.

![alt text](screenshots/As7T3ss15.png)

---

#### Screenshot 16 — Public Health Endpoint

Add a terminal screenshot showing a successful response from the public application health endpoint through the reverse proxy.

![alt text](screenshots/As7T3ss16.png)

---

#### Screenshot 17 — Health-Check and Startup-Order Document

Add a screenshot showing the contents of:

```text
docs/03-healthchecks-and-depends-on.md
```

Explain the health-check method for each service and the startup dependency order.

![alt text](screenshots/As7T3ss17.png)

---

# Task 4 — Configure the Reverse Proxy and Same-Origin Routing

## Goal

Use either Nginx or Traefik as the only public entry point for the EpicBook application.

### Evidence

#### Screenshot 18 — Selected Reverse-Proxy Configuration

Add a screenshot showing the configuration for your selected reverse proxy.

It must show routes for:

- Static frontend assets
- Application pages
- API requests
- Health endpoint

![alt text](screenshots/As7T4ss18.png)

---

#### Screenshot 19 — Only Reverse Proxy Publishes Port 80

Add a screenshot of `docker-compose.yml` showing that only the `reverse-proxy` service publishes port 80.

![alt text](screenshots/As7T4ss19.png)

---

#### Screenshot 20 — Reverse-Proxy Route Testing

Add a terminal screenshot showing successful requests through the selected reverse proxy to:

- Application page
- One API endpoint
- One static asset
- Health endpoint

![alt text](screenshots/As7T4ss20.png)

---

#### Screenshot 21 — EpicBook Application Through Public IP

Add a browser screenshot showing the EpicBook application loaded through the VM public IP address.

Add your full name as a clear caption below the screenshot.

![alt text](screenshots/As7T4ss21.png)

---

#### Screenshot 22 — Proxy Routing and CORS Document

Add a screenshot showing the contents of:

```text
docs/04-proxy-routing-and-cors.md
```

Explain the proxy routes and state whether CORS was required and why.

![alt text](screenshots/As7T4ss22.png)

---

# Task 5 — Prove Data Persistence, Backup, and Restore

## Goal

Verify MySQL persistence and perform a controlled backup and restore drill.

### Evidence

#### Screenshot 23 — MySQL Volume Configuration

Add a terminal screenshot showing the `db_data` named volume and its MySQL mount configuration.

![alt text](screenshots/As7T5ss23.png)

---

#### Screenshot 24 — Test Data Before Backup

Add a terminal screenshot showing the selected test data before the backup and restore drill.

![alt text](screenshots/As7T5ss24.png)

---

#### Screenshot 25 — Successful Backup Creation

Add a terminal screenshot showing successful backup creation and the backup file stored in the host backup directory.

![alt text](screenshots/As7T5ss25.png)

---

#### Screenshot 26 — Controlled Data-Loss Test

Add a terminal screenshot showing that the selected test record was removed during the controlled data-loss test.

![alt text](screenshots/As7T5ss26.png)

---

#### Screenshot 27 — Restore Verification

Add a terminal screenshot showing successful restore and verification that the deleted test record is available again.

![alt text](screenshots/As7T5ss27.png)

---

#### Screenshot 28 — Persistence After Down/Up Cycle

Add a terminal screenshot showing that database data remains available after a non-destructive Docker Compose down/up cycle.

Do not use `docker compose down -v`.

![alt text](screenshots/As7T5ss28.png)

---

#### Screenshot 29 — Persistence and Backup Document

Add a screenshot showing the contents of:

```text
docs/05-persistence-and-backup.md
```

Include the backup plan and restore procedure.

![alt text](screenshots/As7T5ss29.png)

---

# Task 6 — Configure Logging and Observability

## Goal

Configure useful reverse-proxy and backend logs without exposing sensitive information.

### Evidence

#### Screenshot 30 — Logging Configuration

Add a screenshot showing:

- Configuration for the selected reverse proxy
- Proxy log format
- Docker Compose host log-directory bind mount

![alt text](screenshots/As7T6ss30.png)
![alt text](screenshots/As7T6ss300.png)

---

#### Screenshot 31 — Persistent Proxy Logs and Backend Logs

Add a terminal screenshot showing:

- Selected reverse-proxy logs available from the host directory after a proxy restart
- Backend logs displayed through Docker Compose

![alt text](screenshots/As7T6ss31.png)

---

### Notes

Write a short note covering:

- The selected reverse proxy
- Host path used for reverse-proxy logs
- How backend logs are viewed
- Whether JSON or standard text logs were used
- Why passwords, tokens, headers, and database connection strings must not appear in logs

Nginx was selected as the reverse proxy for the EpicBook application. Reverse-proxy logs are persisted on the EC2 host in logs/nginx/, which is mounted to /var/log/nginx/ inside the reverse-proxy container.

Backend logs can be viewed using docker compose logs backend. The Nginx access log uses structured JSON format, while the error log uses standard text format.

Passwords, authentication tokens, sensitive headers, and database connection strings must never appear in logs because logs may be retained or accessed by other users. Exposing these details could compromise accounts, reveal database credentials, and put application data at risk. Logs should contain only the information needed for troubleshooting and monitoring.

---

# Task 7 — Deploy and Verify the Stack on a Cloud VM

## Goal

Deploy the completed Docker Compose stack on an AWS or Azure VM and verify public access.

### Evidence

#### Screenshot 32 — VM Public IP and Inbound Rules

Add a cloud-console screenshot showing:

- VM public IP address
- SSH port 22 restricted to your IP address
- HTTP port 80 allowed from Anywhere

![alt text](screenshots/As7T7ss32.png)

---

#### Screenshot 33 — Cloud VM Stack Verification

Add a VM terminal screenshot showing:

- Docker Compose service status
- Successful public health or API response
- No published database, frontend, or backend ports

![alt text](screenshots/As7T7ss33.png)

---

#### Screenshot 34 — EpicBook Application on Cloud VM

Add a browser screenshot showing the EpicBook application loaded through the VM public IP address.

Add your full name as a clear caption below the screenshot.

![alt text](screenshots/As7T7ss34.png)

---

### Notes

Write a short note covering:

- Cloud provider used
- VM operating system
- Public port exposed
- Security rules configured
- Confirmation that the application and backend API worked through the reverse proxy

### Task 7 Notes — Deploy and Verify the Stack on a Cloud VM

- **Cloud provider:** Amazon Web Services (AWS).
- **VM operating system:** Ubuntu Linux.
- **Public port exposed:** TCP port 80 through the Nginx reverse proxy.
- **Security rules:** SSH (port 22) is restricted to a specific IP address (`102.89.68.230/32`), while HTTP (port 80) is allowed from anywhere (`0.0.0.0/0`).
- **Application and API verification:** The EpicBook stack was deployed using Docker Compose. All four services—the reverse proxy, frontend, backend, and database—were running and healthy. A request to the public health endpoint returned `HTTP 200 OK` with `"status":"healthy"` and `"database":"connected"`.
- **Port security:** The frontend, backend, and database have no host port mappings. Public access is routed through the Nginx reverse proxy on port 80.

**Conclusion:** The EpicBook application stack was deployed on an AWS EC2 Ubuntu VM and its health endpoint was verified through the public IP address.

---

# Task 8 — Automate Deployment with CI/CD (Optional)

## Goal

Optionally automate image build, image push, and deployment through GitHub Actions or Azure Pipelines.

### Optional Evidence

#### Optional Screenshot — Successful CI/CD Pipeline Run

Add a screenshot showing a successful pipeline run with build, image push, deployment, and verification stages.

Add your screenshot here.

---

### Optional Notes

Write a short note covering:

- CI/CD platform used
- Image-tagging method
- Registry used
- Deployment trigger
- Manual approval or secret-handling approach

Write your note here.

---

# Task 9 — Perform Reliability Tests and Create an Operations Runbook

## Goal

Test controlled service failures and document safe operating procedures.

### Evidence

#### Screenshot 35 — Backend Failure and Recovery

Add a terminal screenshot showing:

- Backend failure test
- Expected unavailable response through the reverse proxy
- Backend restart
- Successful health-check recovery

![alt text](screenshots/As7T9ss35.png)

---

#### Screenshot 36 — Database Failure and Recovery

Add a terminal screenshot showing:

- Database outage test
- Failed database-dependent request
- Database restart
- Successful application recovery

![alt text](screenshots/As7T9ss36.png)

---

### Notes

Write a short operations runbook covering:

- Safe restart procedure for reverse proxy, frontend, backend, and database
- Backup and restore procedure
- Secret-rotation approach
- Database recovery procedure
- What to check when the application returns an error
- Results of backend and database reliability tests

### Task 9 Notes — Operations Runbook

**1. Safe Restart Procedure**

Before restarting any service, check its current status using `docker compose ps`. Restart only the affected service to minimize downtime:

- Reverse proxy: `docker compose restart reverse-proxy`
- Frontend: `docker compose restart frontend`
- Backend: `docker compose restart backend`
- Database: `docker compose restart database`

After restarting, run `docker compose ps` to confirm service health. Verify application access through Nginx using `curl -i http://localhost/health`. Avoid deleting containers or persistent volumes during routine restarts.

**2. Database Backup and Restore**

Create a database backup using:

`docker compose exec -T database sh -c 'MYSQL_PWD="$MYSQL_PASSWORD" mysqldump --no-tablespaces --single-transaction -u"$MYSQL_USER" "$MYSQL_DATABASE"' > backups/bookstore-before-restore.sql`

Restore the backup using:

`docker compose exec -T database sh -c 'MYSQL_PWD="$MYSQL_PASSWORD" mysql -u"$MYSQL_USER" "$MYSQL_DATABASE"' < backups/bookstore-before-restore.sql`

After restoration, verify that the expected database records are present. Store backups securely and check that each backup file is valid before relying on it.

**3. Secret Rotation**

Rotate database passwords, application secrets, and other credentials through the appropriate configuration or secret-management mechanism. Update the affected environment variables and application configuration, restart dependent services safely, and verify database connectivity and application health. Never commit secrets to GitHub or expose them in screenshots and logs.

**4. Database Recovery Procedure**

Check the database status using `docker compose ps` and inspect database logs with `docker compose logs --tail=50 database`. If the database is stopped, start it using `docker compose start database` and wait until it becomes healthy. Then verify recovery using `curl -i http://localhost/health`. If recovery fails, inspect database credentials, connection settings, logs, and persistent storage before considering a backup restore.

**5. Application Error Troubleshooting**

When the application returns an error:

- Check service status with `docker compose ps`.
- Inspect reverse-proxy logs in `logs/nginx/`.
- View backend logs using `docker compose logs --tail=50 backend`.
- View database logs using `docker compose logs --tail=50 database`.
- Test the health endpoint with `curl -i http://localhost/health`.
- Confirm that only the reverse proxy publishes public HTTP port 80 and that the frontend, backend, and database are not directly published on host ports.

Resolve the identified issue, restart only the affected service, and retest the application.

**6. Reliability Test Results**

The backend reliability test succeeded. When the backend was stopped, the reverse proxy returned `HTTP 502 Bad Gateway`. After the backend was restarted, the health endpoint returned `HTTP 200 OK` with `"status":"healthy"` and `"database":"connected"`.

The database reliability test should be documented using the actual results from Screenshot 36. After the database outage test, confirm that the database and dependent application services recover and that the health endpoint returns `HTTP 200 OK` with the database connected.

**Operational Safety:** Never use `docker compose down -v` during routine recovery because it can remove persistent database volumes and cause data loss. Protect backups and credentials, and verify service health after every recovery operation.

---

# Final Public Application URL

**EpicBook URL:** `http://16.192.157.171/`

Replace the placeholder with your working public URL.

---

# GitHub Repository URL

**Your Fork or Repository URL:** `https://github.com/Fhelobanty/theepicbook`

---

# LinkedIn Requirement

## Goal

Create a professional LinkedIn post of 6–10 lines about your EpicBook capstone deployment.

Your post must include:

- The architectural decision that most improved reliability
- Your biggest image-size reduction, with numbers
- Key production-hardening lessons
- A deployment verification image

### Evidence

**LinkedIn Post URL:** `https://www.linkedin.com/posts/aamicheal_devops-aws-docker-ugcPost-7519391637836374016-hQ_r/?highlightedUpdateUrn=urn%3Ali%3Aactivity%3A7519391640910929922&highlightedUpdateType=SOCIAL_SHARE&origin=SOCIAL_SHARE&utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAADFvgDYBsnsyE66xAyq2HzH3Jfsf19WE6JA`

#### LinkedIn Post Screenshot

![alt text](screenshots/As7T9linkedln.png)

---

# Submission Checklist

- [ ] EpicBook repository reviewed and architecture diagram created
- [ ] Environment variables, ports, persistence, and health-check details documented
- [ ] Backend and frontend production Dockerfiles created
- [ ] Backend runs as a non-root user
- [ ] Docker image-size comparison completed
- [ ] Docker Compose stack includes reverse proxy, frontend, backend, and database
- [ ] `front-tier` and `back-tier` networks configured
- [ ] `db_data` named volume configured
- [ ] MySQL, backend, frontend, and reverse-proxy health checks configured
- [ ] Startup dependencies use `service_healthy`
- [ ] Nginx or Traefik selected as the only public reverse proxy
- [ ] Only reverse-proxy port 80 is publicly published
- [ ] Same-origin routing configured and CORS used only when required
- [ ] Backup, restore, and persistence testing completed
- [ ] Reverse-proxy and backend logs verified
- [ ] Cloud VM deployment verified through the public IP
- [ ] Backend and database reliability tests completed
- [ ] Screenshots 1–36 included
- [ ] Required notes completed
- [ ] LinkedIn post URL and screenshot included
- [ ] Full name visible in required screenshots or captions
- [ ] No passwords, tokens, private keys, account IDs, or other sensitive information exposed

---

## 📌 About DMI & CloudAdvisory

DevOps Micro Internship (DMI) is a project-based DevOps program run by Pravin Mishra (The CloudAdvisory) focused on real-world execution, systems thinking, and career readiness.

It helps learners build strong DevOps foundations with hands-on experience.

---

## 📌 Resources

- 🌐 DMI Official Website: https://dmi.pravinmishra.com?utm_source=github&utm_medium=readme  
- 🎓 University: https://university.pravinmishra.com?utm_source=github&utm_medium=readme  
- 💬 Discord Community: https://discord.pravinmishra.com?utm_source=github&utm_medium=readme  
- 📝 Blog: https://dmi.pravinmishra.com/blog?utm_source=github&utm_medium=readme  
- ▶️ YouTube Playlist: https://www.youtube.com/playlist?list=PLFeSNDtI4Cho  
- 🔗 Pravin Mishra (LinkedIn): https://www.linkedin.com/in/pravin-mishra-aws-trainer/  
- 🏢 CloudAdvisory (LinkedIn): https://www.linkedin.com/company/thecloudadvisory/

---

*This submission is part of DevOps Micro Internship (DMI) — Agentic AI Track.*
