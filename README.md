# OWASP Juice Shop Security Lab

A locally hosted cybersecurity practice environment using OWASP Juice Shop, Docker Desktop and Windows.

## 1. Project Overview

This project demonstrates the setup of a controlled local web application security testing lab. It documents the deployment, network configuration, access restrictions and ethical testing boundaries.

The target is OWASP Juice Shop, an intentionally vulnerable web application designed for security education.

## 2. Objectives

- Deploy OWASP Juice Shop locally using Docker.
- Restrict the published application port to localhost.
- Verify that the application is not reachable through the host's LAN address.
- Document the network topology.
- Define Rules of Engagement (RoE).
- Establish a safe environment for future authorized security testing.

## 3. Tools and Technologies

- OWASP Juice Shop
- Docker Desktop
- Windows PowerShell
- WSL 2
- Google Chrome
- GitHub

## 4. Target Configuration

| Item                  | Configuration              |
| --------------------- | -------------------------- |
| Application           | OWASP Juice Shop           |
| Container             | `juice-shop`               |
| Docker network        | `bridge`                   |
| Container IP observed | `172.17.0.2`               |
| Application port      | `3000`                     |
| Host binding          | `127.0.0.1:3000`           |
| Local application URL | `http://127.0.0.1:3000/#/` |

## 5. Deployment

The Juice Shop image was downloaded and deployed using Docker.

```powershell
docker run -d --name juice-shop -p 127.0.0.1:3000:3000 bkimminich/juice-shop
```

The application was successfully accessed through a browser on the host computer.

## 6. Network Access Restriction

The Docker port is explicitly bound to the loopback address `127.0.0.1`, rather than all host network interfaces.

This restricts access through the published application port to the local computer.

Verification performed:

- Confirmed the Docker port binding using `docker port juice-shop`.
- Confirmed local connectivity using `Test-NetConnection 127.0.0.1 -Port 3000`.
- Tested the host's LAN address on port 3000; the TCP connection failed.
- Tested from a separate phone connected to the same Wi-Fi; the application could not be reached.

**Scope of this protection:** These tests verify that the published Juice Shop web port is not reachable through the host's LAN address. They do not establish that every possible network path to the container is blocked.

Outbound internet access from the main Juice Shop container has not been blocked or verified. This is not claimed as part of the completed isolation configuration.

## 7. Rules of Engagement

All testing is restricted to the locally deployed OWASP Juice Shop instance.

The approved scope, permitted activities, exclusions and stop conditions are documented in:

- `docs/rules-of-engagement.md`

## 8. Network Topology

The actual Docker configuration and network access path are documented in:

- `docs/network-topology.md`

## 9. Evidence and Verification

Commands and observed results supporting the configuration are documented in:

- `docs/evidence.md`

## 10. Project Status

- [x] Local Juice Shop deployment
- [x] Browser access verified
- [x] Localhost port binding verified
- [x] Host LAN access test performed
- [x] Same-Wi-Fi phone access test performed
- [x] Rules of Engagement defined
- [x] Network topology documented
- [ ] Optional baseline snapshot
- [ ] Further authorized security testing and findings

## 11. Safety Notice

This lab is intended strictly for authorized cybersecurity education and practice. Testing must remain within the defined scope. No public websites, third-party systems or unrelated devices are authorized targets.
