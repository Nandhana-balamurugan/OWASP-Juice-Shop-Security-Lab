# OWASP Juice Shop Security Lab

## 1. Project Overview

This project documents the setup of a local cybersecurity practice lab using OWASP Juice Shop and Docker Desktop.

The objective is to build a controlled environment for learning web application security testing, documenting network configuration, and following ethical testing guidelines.

## 2. Lab Objectives

- Deploy OWASP Juice Shop locally using Docker.
- Configure and verify restricted network access.
- Document the lab network topology.
- Define Rules of Engagement (RoE).
- Prepare a repeatable baseline for future security testing.

## 3. Tools and Technologies

- OWASP Juice Shop
- Docker Desktop
- Windows
- Google Chrome
- GitHub

## 4. Target Details

| Item | Configuration |
|---|---|
| Target | OWASP Juice Shop |
| Deployment | Docker container |
| Container name | juice-shop |
| Application port | 3000 |
| Local URL | http://127.0.0.1:3000/#/ |
| Host binding | 127.0.0.1:3000 |

## 5. Setup and Verification

The Juice Shop Docker image was downloaded and the container was started successfully.

Command used:

```powershell
docker run -d --name juice-shop -p 127.0.0.1:3000:3000 bkimminich/juice-shop
```

Verification performed:

```powershell
docker port juice-shop
Test-NetConnection 127.0.0.1 -Port 3000
```

The application was successfully accessed through the local browser.

## 6. Network Isolation Status

The application port is currently bound to the localhost interface (127.0.0.1), restricting direct access through the host's LAN interfaces.

**Important:** Outbound internet access from the Docker container has not yet been blocked or verified. Full network isolation is still in progress.

## 7. Rules of Engagement

Testing will be restricted to the locally deployed OWASP Juice Shop instance owned and controlled by the project author.

### Allowed Activities
- Local application exploration.
- Passive inspection of application responses.
- Authorized web security testing against the local target.
- Documentation of observations and findings.

### Exclusions
- Public websites and third-party systems.
- Other devices and networks.
- Denial-of-service testing.
- Destructive activities or unauthorized data access.
- Testing outside the defined local target.

### Stop Conditions
- Unexpected access to external systems.
- Any impact on systems outside the lab.
- Unexpected service disruption.
- Loss of control over the testing environment.

Testing must stop immediately if any of these conditions occur.

## 8. Project Status

- [x] Local OWASP Juice Shop deployment.
- [x] Local browser access verified.
- [x] Localhost port binding verified.
- [ ] Outbound network isolation.
- [ ] Network topology documentation.
- [ ] Complete Rules of Engagement verification.
- [ ] Baseline snapshot.
- [ ] Final submission review.

## 9. Safety Notice

This environment is intended strictly for authorized cybersecurity education and practice. All testing must remain within the defined local lab scope.

---

**Project:** OWASP Juice Shop Security Lab  
**Purpose:** Ethical Hacking Practice and Network Isolation Documentation
