# Nexus Platform

Full-stack investor and entrepreneur collaboration platform.

## Final Output

- Functional web app with authentication, profiles, meetings, video calling, document chamber, payment simulation, and security features.
- Frontend and backend repository structure.
- Deployment-ready frontend and backend configuration.
- API documentation and Postman collection.
- Final demo presentation material.

## Source Files

This repository contains a complete source handoff in [SOURCE_BUNDLE.md](SOURCE_BUNDLE.md). Copy each section from that file into the matching path to recreate the full project structure.

## Tech Stack

- Frontend: React, Vite, Tailwind CSS, React Router, Lucide icons
- Backend: Node.js HTTP API
- Storage: Browser localStorage for frontend demo state, in-memory API data for backend demo
- Security demo: sanitized request bodies, scrypt password hashing, signed JWT-style tokens, mock 2FA, role-protected profile update route, security headers

## Run Frontend

```bash
cd client
npm install
npm run dev
```

Frontend URL:

```text
http://127.0.0.1:5173/
```

## Run Backend

```bash
cd sever
npm run dev
```

Backend URL:

```text
http://127.0.0.1:5000/
```

## Demo Login

Entrepreneur:

```text
Email: ayesha@nexus.test
Password: demo123
```

Investor:

```text
Email: daniel@nexus.test
Password: demo123
Mock OTP: 913428
```

## Main App Routes

- `/` - dashboard
- `/login` - authentication
- `/register` - profile creation
- `/meetings` - meeting scheduling calendar workflow
- `/documents` - document chamber with e-signature metadata
- `/videocall` - video room demo
- `/payments` - payment simulation, transaction history, security, deployment checklist
- `/api-docs` - API documentation route map
- `/presentation` - final demo presentation

## Handoff Documents

Included inside [SOURCE_BUNDLE.md](SOURCE_BUNDLE.md):

- `docs/API_DOCUMENTATION.md`
- `docs/DEPLOYMENT.md`
- `docs/FINAL_DELIVERABLES.md`
- `docs/DEMO_PRESENTATION.md`
- `docs/Nexus.postman_collection.json`
