# Task 03 – Local Reconnaissance and Service Inventory

## 1. Objective

To perform passive reconnaissance on a locally hosted OWASP Juice Shop application and document its exposed service, technology details, HTTP headers, API routes, and visible inputs.

## 2. Target Information

| Item | Observation |
|---|---|
| Application | OWASP Juice Shop |
| Target URL | http://127.0.0.1:3000 |
| Application Version | 20.3.0 |
| Runtime | Node.js v24.21.0 |
| Docker Image | bkimminich/juice-shop |
| Host Binding | 127.0.0.1:3000 |
| Container IP | 172.17.0.2 |
| Container Network | Docker bridge |
| HTTP Status | 200 OK |

## 3. Service Inventory

| Service / Component | Port / Endpoint | Method | Observation |
|---|---|---|---|
| HTTP Web Application | 3000 | GET | Application accessible locally |
| Application Version API | /rest/admin/application-version | GET | Version-related information |
| Application Configuration API | /rest/admin/application-configuration | GET | Application configuration data |
| Challenges API | /api/Challenges/ | GET | Challenge metadata |
| Product Search API | /rest/products/search?q=apple | GET | Product search results |
| Languages API | /rest/languages | GET | Supported language information |
| Quantity API | /api/Quantitys/ | GET | Product quantity information |
| Socket.IO | /socket.io/ | POST | Real-time communication |
| Translation Resource | /assets/i18n/en.json | GET | English UI translation data |

## 4. HTTP Response Headers

The following headers were observed:

- Access-Control-Allow-Origin: *
- X-Content-Type-Options: nosniff
- X-Frame-Options: SAMEORIGIN
- Feature-Policy: payment 'self'
- Content-Type: text/html; charset=UTF-8
- Cache-Control: public, max-age=0

## 5. Visible Input

| Input | Location | Observation |
|---|---|---|
| Product search | /rest/products/search?q=apple | Search parameter `q` accepts a product search term |

## 6. Preliminary Risk Hypotheses

These are observations for further review, not confirmed vulnerabilities.

1. Publicly accessible configuration information may reveal implementation details.
2. Application version information may help identify the software version.
3. Product search parameters should be reviewed for appropriate input handling.
4. API responses containing product quantities and purchase limits should be reviewed for access control.
5. Real-time Socket.IO communication should be reviewed for appropriate authentication and authorization.

## 7. Lab Isolation and Scope

- Testing was performed against my own locally hosted OWASP Juice Shop instance.
- The application is bound to 127.0.0.1:3000 on the host.
- The container currently uses Docker's default bridge network.
- A separate internal Docker network named `juice-shop-isolated` exists, but the running Juice Shop container is not connected to it.
- Access from another device on the same Wi-Fi was tested and the application was not reachable through the laptop's Wi-Fi address on port 3000.
- No public targets or third-party systems were tested.

## 8. Conclusion

Passive reconnaissance identified the local web service, application and runtime versions, HTTP response headers, API endpoints, and visible input parameters. These observations provide a baseline attack-surface inventory for further authorized security assessment.

No vulnerability is confirmed by this reconnaissance activity.
