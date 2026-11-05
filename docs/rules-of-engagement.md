# Rules of Engagement (RoE)

## OWASP Juice Shop Security Lab

## 1. Purpose

These Rules of Engagement define the authorized scope and safety boundaries for cybersecurity practice using the locally deployed OWASP Juice Shop application.

## 2. Authorized Target

- Application: OWASP Juice Shop
- Environment: Local Docker container
- Container name: `juice-shop`
- Application URL: `http://127.0.0.1:3000/`
- Host operating system: Windows
- Testing owner: Student operating the lab

Only this intentionally vulnerable application is included in the authorized scope.

## 3. Permitted Activities

The following activities are permitted against the local Juice Shop instance:

- Manual application exploration.
- Identifying security weaknesses.
- Testing input validation.
- Testing authentication and authorization behaviour.
- Inspecting application responses and errors.
- Using browser developer tools.
- Performing non-destructive security tests.
- Recording observations and preparing remediation recommendations.

## 4. Prohibited Activities

The following activities are strictly excluded:

- Testing public websites or third-party systems.
- Attacking college, institutional or workplace networks.
- Attacking other devices on the local network.
- Denial-of-service or stress testing.
- Destructive actions that damage the application or data.
- Unauthorized collection or exposure of personal information.
- Testing outside the defined target.

## 5. Stop Conditions

Testing must stop immediately if:

- The application becomes unstable or unavailable.
- An activity unexpectedly affects another system.
- The target becomes accessible through an unintended network path.
- Real personal or sensitive information is encountered.
- The tester loses control of the lab environment.

## 6. Authorization

The student is authorized to test the locally deployed OWASP Juice Shop instance that they created and control.

No other system, network, application or device is included in this authorization.

## 7. Safety Commitment

All activities will remain within the defined local lab scope and will follow responsible cybersecurity learning practices.
