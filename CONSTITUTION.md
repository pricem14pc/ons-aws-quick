# Project Constitution: Integrated Chat Bot

## 1. Non-Negotiable Principles
* **Zero Guesswork**: The AI agent must fail gracefully and request human clarification via a structured prompt rather than make architectural or security assumptions.
* **No Secret Commits**: Hardcoded keys, tokens, or mock secrets in the codebase are strictly prohibited.
* **12 Factor**: App must adhere to 12 Factor principles to ensure clean contracts (e.g. explicit dependencies, environment config, build and run separation, stateless and scalable, structured logging, no divergence between dev, test and production).
* **Separation of Concerns**: The frontend widget must be an isolated, asynchronous bundle that does not block or pollute the host static website's window scope.
* **Accessibility First**: The widget must be fully compliant with WCAG 2.1 AA standards, ensuring that all users, including those with disabilities, can interact with the chat bot effectively. Progressive enhancement techniques must be employed to ensure that the widget remains functional even in environments with limited JavaScript support.
## 2. Technical Stack Boundaries
* **Use of existing frontend ONSdigital/design-system**: The widget must not define its own front-end components and must leverage existing capability from https://service-manual.ons.gov.uk/design-system and https://service-manual.ons.gov.uk/design-system any front end components must be built using the existing design system. Any new components or patterns must be limited and last resort.
* **Backend**: Node.js with Fastify (highly optimized for JSON payload processing). Alternatively Python with FastAPI.
* **Testing Framework**: Vitest for unit tests; Playwright for cross-browser accessibility and visual regression testing. Pytest if Python backend unit tests.
