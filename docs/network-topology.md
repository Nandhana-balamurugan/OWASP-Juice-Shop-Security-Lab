# Network Topology — OWASP Juice Shop Security Lab

## 1. Environment

- Host operating system: Windows
- Container platform: Docker Desktop
- Backend: WSL 2
- Target application: OWASP Juice Shop
- Container name: `juice-shop`

## 2. Network Diagram

```text
             Local Windows Computer
                      |
                      |
             Browser (Chrome)
                      |
                      |
             127.0.0.1:3000
                      |
                      |
              Docker Port Mapping
                      |
                      |
              172.17.0.2:3000
                      |
                      |
              OWASP Juice Shop
                 Container
                      |
                      |
              Docker bridge
                172.17.0.0/16


      Other devices on the same Wi-Fi
                      |
                      X
             Published port not
                reachable
```

## 3. Docker Configuration

The container was launched using:

```powershell
docker run -d --name juice-shop -p 127.0.0.1:3000:3000 bkimminich/juice-shop
```

Observed configuration:

- Docker network: `bridge`
- Container IP: `172.17.0.2`
- Container port: `3000`
- Host IP binding: `127.0.0.1`
- Host port: `3000`

## 4. Access Control Verification

### Local access

The application was successfully opened using:

`http://127.0.0.1:3000/#/`

### Host LAN access

A TCP connection test against the host's Wi-Fi IP address on port 3000 failed.

### Separate-device access

A phone connected to the same Wi-Fi network attempted to access the host's LAN IP on port 3000. The browser displayed a site-unreachable error.

These tests support the conclusion that the published application port is restricted to localhost.

## 5. Network Isolation Scope

The main Juice Shop container remains connected to Docker's default bridge network.

A separate Docker network named `juice-shop-isolated` was created and tested with a temporary container. Its configuration reported `Internal: true`, and outbound connectivity tests from the temporary container failed.

This was a separate experiment. The main Juice Shop container was not moved to that network.

## 6. Security Boundary

The verified restriction applies to the published web application port. It should not be interpreted as proof that the container has no outbound connectivity or that every possible access path is blocked.

The lab is intended for local, authorized educational testing.
