# Lab Evidence

This folder contains screenshots documenting the local OWASP Juice Shop security lab configuration and verification.

## Evidence List

| Screenshot | Description |
|---|---|
| 01-juice-shop-homepage.png | Juice Shop running in the browser |
| 02-docker-container-running.png | Docker containers and running status |
| 03-docker-port-binding.png | Localhost-only port binding |
| 04-localhost-connection-success.png | Successful localhost connectivity test |
| 05-lan-access-blocked.png | Failed TCP connection through host LAN IP |

## Verification Summary

- Juice Shop is accessible through `127.0.0.1:3000`.
- Docker publishes port 3000 on the localhost interface.
- The tested host LAN address does not provide access to the published application port.
- These screenshots document the tested configuration and do not prove that every possible network path is blocked.
