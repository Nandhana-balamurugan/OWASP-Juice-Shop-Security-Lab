# Task 03 – Sanitized Command Log

## Objective
To record the commands used for passive reconnaissance of my locally hosted OWASP Juice Shop application.

## 1. Check Running Container

```powershell
docker ps --filter "name=juice-shop"
```

**Observation:** Juice Shop container was running.

## 2. Check Port Binding

```powershell
docker port juice-shop
```

**Observation:** Application port 3000 was bound to 127.0.0.1:3000.

## 3. Identify Docker Image and Container Status

```powershell
docker inspect juice-shop --format 'Image={{.Config.Image}} | Status={{.State.Status}}'
```

**Observation:** Image was bkimminich/juice-shop and container status was running.

## 4. Identify Container Network

```powershell
docker inspect juice-shop --format '{{json .NetworkSettings.Networks}}'
```

**Observation:** Container was connected to Docker's default bridge network with IP 172.17.0.2.

## 5. Identify Application Version

```powershell
docker exec juice-shop /nodejs/bin/node -p "require('./package.json').version"
```

**Output:** 20.3.0

## 6. Identify Node.js Runtime Version

```powershell
docker exec juice-shop /nodejs/bin/node --version
```

**Output:** v24.21.0

## 7. Inspect HTTP Response Headers

```powershell
curl.exe -I http://127.0.0.1:3000/
```

**Observation:** HTTP 200 OK. Response headers included X-Content-Type-Options, X-Frame-Options and Access-Control-Allow-Origin.

## 8. Verify Local Port Accessibility

```powershell
Test-NetConnection 127.0.0.1 -Port 3000
```

**Observation:** TCP connection to the local application port succeeded.

## 9. Browser-Based Reconnaissance

Used Chrome Developer Tools → Network → Fetch/XHR to observe application requests.

Observed endpoints included:

- /rest/admin/application-version
- /rest/admin/application-configuration
- /api/Challenges/
- /rest/products/search?q=apple
- /rest/languages
- /api/Quantitys/
- /socket.io/
- /assets/i18n/en.json

## 10. Safety and Sanitization

- Only the locally hosted lab application was inspected.
- No public IP addresses or third-party systems were scanned.
- Socket.IO session IDs and other potentially sensitive values were excluded from this log.
- No destructive or intrusive testing was performed.

## Conclusion

The commands and browser observations helped identify the target application, runtime, network configuration, HTTP service, response headers, and exposed API routes.
