---
Created: 2025-06-23T20:22
---
## **Unit Testing**

- **What it is:** Tests **individual functions or components** in isolation.
- **Goal:** Ensure each piece of logic works as expected.
- **Example:** Testing a `sum(a, b)` function.
- **Tools:** Jest, Mocha, Jasmine, PyTest, JUnit

  

## **Integration Testing**

- **What it is:** Tests **how different units/modules work together**.
- **Goal:** Ensure components interact correctly (e.g., DB + API).
- **Example:** Testing an endpoint that calls the database.
- **Tools:** Supertest (Node), Postman, TestContainers, PyTest

  

## **End-to-End (E2E) Testing**

- **What it is:** Simulates **real user interactions** from start to finish.
- **Goal:** Validate entire app flow (frontend + backend + DB).
- **Example:** Fill a form, submit, check if data saves and UI updates.
- **Tools:** Cypress, Playwright, Selenium, Puppeteer

  

## **Manual Testing**

- **What it is:** Testing done **by humans**, not automation.
- **Goal:** Catch unexpected bugs, UI/UX issues, edge cases.
- **Example:** QA testers exploring the app manually.

  

## **Smoke Testing**

- **What it is:** Basic tests to check if the **main functions work**.
- **Goal:** Make sure app isn’t “broken” after a new build/deploy.
- **Example:** Does the homepage load? Can users log in?

  

## **Regression Testing**

- **What it is:** Retesting after changes to make sure **old features still work**.
- **Goal:** Prevent new code from breaking existing features.
- **Example:** After adding a new feature, retest all related pages.

  

## **Security Testing**

- **What it is:** Test for **vulnerabilities**, **unauthorized access**, etc.
- **Goal:** Protect data, validate authentication, prevent attacks.
- **Example:** Try SQL injection or access restricted routes.

  

## **Performance / Load Testing**

- **What it is:** Tests how the system behaves under **high load**.
- **Goal:** Identify bottlenecks and ensure speed/scalability.
- **Example:** Simulate 1,000 users logging in at once.
- **Tools:** JMeter, Artillery, k6

  

## **Acceptance Testing (UAT)**

- **What it is:** Tests if the app **meets business requirements**.
- **Goal:** Ensure it's acceptable for release.
- **Example:** Business stakeholder verifies a feature before launch.

  

## Summary Table

|   |   |   |   |
|---|---|---|---|
|Type|Focus|Automation?|Tools/Examples|
|Unit|Functions/components|✅|Jest, Mocha, PyTest|
|Integration|Between modules|✅|Supertest, Postman|
|End-to-End (E2E)|Full user flow|✅|Cypress, Playwright, Selenium|
|Manual|Human-driven testing|❌|QA teams|
|Smoke|Basic sanity checks|✅|Bash scripts, Jest, Cypress|
|Regression|Catch unintended bugs|✅|Any of the above (rerun tests)|
|Security|Access control, attacks|✅/❌|OWASP ZAP, manual probing|
|Performance|Load/stress|✅|JMeter, k6|
|Acceptance (UAT)|Business expectations|✅/❌|QA checklists, demo reviews|