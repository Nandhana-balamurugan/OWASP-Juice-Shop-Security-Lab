# Baseline Snapshot — OWASP Juice Shop

## 1. Purpose

This document records the initial state of the locally deployed OWASP Juice Shop before further security testing.

## 2. Environment

- Host OS: Windows
- Container platform: Docker Desktop
- Application: OWASP Juice Shop
- Container name: `juice-shop`
- Docker network: `bridge`
- Container IP observed: `172.17.0.2`
- Application port: `3000`
- Host binding: `127.0.0.1:3000`

## 3. Initial Application State

- Juice Shop successfully starts in Docker.
- The homepage loads through the local browser.
- Localhost connectivity is successful.
- The published application port is not reachable through the tested host LAN address.

## 4. Baseline Evidence

Refer to the screenshots in this folder:

- `01-juice-shop-homepage.png`
- `02-docker-container-running.png`
- `03-docker-port-binding.png`
- `04-localhost-connection-success.png`
- `05-lan-access-blocked.png`

## 5. Scope and Limitations

This snapshot records the observed initial configuration. It is not a complete security assessment or proof that every possible network path is blocked.

Further testing must follow the approved Rules of Engagement.
