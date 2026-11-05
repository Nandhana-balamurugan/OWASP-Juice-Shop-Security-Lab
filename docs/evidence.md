# Evidence and Verification

## OWASP Juice Shop Security Lab

This document records the commands and observations used to verify the local deployment and localhost-only access restriction.

## 1. Container Deployment

Command:

```powershell
docker run -d --name juice-shop -p 127.0.0.1:3000:3000 bkimminich/juice-shop
```

Observation: Docker returned a container ID and the application started successfully.

## 2. Container Status and Port Binding

Command:

```powershell
docker inspect juice-shop --format "Status={{.State.Status}} | Networks={{json .NetworkSettings.Networks}} | Ports={{json .NetworkSettings.Ports}}"
```

Observed:

- Status: running
- Docker network: bridge
- Container IP: 172.17.0.2
- Published port: 127.0.0.1:3000

## 3. Docker Port Verification

Command:

```powershell
docker port juice-shop
```

Observed:

```text
3000/tcp -> 127.0.0.1:3000
```

## 4. Local Connectivity Test

Command:

```powershell
Test-NetConnection 127.0.0.1 -Port 3000
```

Observation: TCP connection succeeded.

The application also loaded successfully in the local browser.

## 5. Host LAN Connectivity Test

Command:

```powershell
Test-NetConnection <HOST_LAN_IP> -Port 3000
```

Observation:

- Ping succeeded.
- TCP connection to port 3000 failed.
- `TcpTestSucceeded` was `False`.

The actual private LAN IP is intentionally omitted from this public evidence document.

## 6. Separate-Device Test

A phone connected to the same Wi-Fi network attempted to open:

`http://<HOST_LAN_IP>:3000`

Observation: Chrome displayed a site-unreachable error.

## 7. Verification Conclusion

The local application was accessible through the host's loopback address, while attempts to reach the published application port through the host's LAN address failed.

These results support localhost-only access for the published Juice Shop web port.

They do not prove that all network traffic to or from the container is blocked.

## 8. Evidence Attachments

Recommended screenshots to add:

1. Juice Shop homepage open at `127.0.0.1:3000`.
2. Docker port mapping showing `127.0.0.1:3000`.
3. Successful localhost TCP connection.
4. Failed host LAN TCP connection.
5. Phone browser showing the failed same-Wi-Fi access attempt.

Before uploading screenshots, hide personal information, unrelated browser tabs, private IP details and other sensitive information where appropriate.
