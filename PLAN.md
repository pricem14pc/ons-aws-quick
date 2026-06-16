# Technical Architecture & Implementation Plan

## 1. System Topology
The application consists of a decoupled widget client communicating via HTTPS/Web Socket with a hardened containerized backend orchestration service.

## 2. Security Architecture

### 2.2 Token Authentication Protocol
* **Handshake**: The client widget initializes by invoking `POST /api/v1/auth/session` containing an authorized static site origin key.
* **Issuance**: Backend returns an ephemeral, cryptographically signed JSON Web Token (JWT) using the `RS256` algorithm.
* **Storage**: Frontend caches the JWT in memory or scoped `sessionStorage`. It must never be stored in persistent `localStorage`.
* **Transport**: All subsequent stateless HTTP headers must provide authorization using the standard syntax: `Authorization: Bearer <JWT>`.

### 2.3 Data Encryption Engineering
* **In Transit**: All client-server communication must be encrypted using TLS 1.3 with strong cipher suites (e.g., AES-256-GCM).
* **At Rest**: Sensitive data stored in backend databases must be encrypted using AES-256. Database backups must also be encrypted and access-controlled.
* **Key Management**: Encryption keys must be rotated every 90 days and stored securely
