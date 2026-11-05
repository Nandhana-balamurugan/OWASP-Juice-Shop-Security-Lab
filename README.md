# OWASP Juice Shop Security Lab

A locally hosted cybersecurity practice environment using OWASP Juice Shop, Docker Desktop and Windows.

## 1. Project Overview

This project demonstrates the deployment and security configuration of a controlled local web application testing lab.

The target is OWASP Juice Shop, an intentionally vulnerable web application designed for security education.

## 2. Objectives

- Deploy OWASP Juice Shop locally using Docker.
- Bind the published application port to localhost.
- Verify that the application is not reachable through the host's LAN address.
- Document the network topology and configuration.
- Define Rules of Engagement (RoE).
- Maintain evidence of configuration and verification.
- Prepare a safe environment for authorized security testing.

## 3. Tools and Technologies

- OWASP Juice Shop
- Docker Desktop
- Windows PowerShell
- WSL 2
- Google Chrome
- GitHub

## 4. Target Configuration

| Item | Configuration |
|---|---|
| Application | OWASP Juice Shop |
| Container | `juice-shop` |
| Docker network | `bridge` |
| Container IP observed | `172.17.0.2` |
| Application port | `3000` |
| Host binding | `127.0.0.1:3000` |
| Local application URL | `http://127.0.0.1:3000/#/` |

## 5. Deployment

The application was deployed using Docker:

```powershell
docker run -d --name juice-shop -p 127.0.0.1:3000:3000 bkimminich/juice-shop
```

The application was successfully accessed through a browser on the host computer.

## 6. Network Access Restriction

The published application port is explicitly bound to `127.0.0.1`, rather than all host network interfaces.

Verification performed:

- Confirmed the Docker port binding.
- Confirmed local connectivity using `Test-NetConnection 127.0.0.1 -Port 3000`.
- Tested the host's LAN address on port 3000; the TCP connection failed.
- Tested from a separate phone connected to the same Wi-Fi; the application could not be reached.

**Security boundary:** These tests verify that the published Juice Shop web port is not reachable through the host's LAN address. They do not prove that every possible network path to the container is blocked.

Outbound internet access from the main Juice Shop container has not been blocked or verified.

See [Network Topology](docs/network-topology.md) for configuration and test details.

## 7. Rules of Engagement

All testing is restricted to the locally deployed OWASP Juice Shop instance.

The approved scope, permitted activities, prohibited actions and stop conditions are documented in [Rules of Engagement](docs/rules-of-engagement.md).

## 8. Evidence and Verification

Commands, observations and verification results are documented in [Evidence](docs/evidence.md).

## 9. Project Status

- [x] Local Juice Shop deployment
- [x] Browser access verified
- [x] Localhost port binding verified
- [x] Host LAN access test performed
- [x] Same-Wi-Fi phone access test performed
- [x] Rules of Engagement documented
- [x] Network topology documented
- [x] Evidence and verification documented
- [x] Baseline snapshot documented
- [x] Evidence screenshots uploaded

## 10. Safety Notice

This lab is intended strictly for authorized cybersecurity education and practice. Testing must remain within the defined scope. Public websites, third-party systems and unrelated devices are not authorized targets.
