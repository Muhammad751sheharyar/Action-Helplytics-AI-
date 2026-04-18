# Helplytics AI - Architecture Document

## 1. Architecture Style

**MERN + JavaScript**, modular feature-based clean architecture.

- Frontend: React + Vite + JavaScript + React Router + Zustand/Context + Tailwind CSS.
- Backend: Node.js + Express + JavaScript.
- Database: MongoDB (Atlas/local).
- Auth: JWT (access token) with hashed passwords.
- Deployment target: Vercel/Netlify (frontend) + Render/Railway/Fly (backend).

## 2. High-Level System

1. Client consumes REST APIs.
2. Backend contains route -> controller -> service -> repository layering.
3. Mongo stores users, requests, messages, notifications, trust signals.
4. AI engine is a service module (rules-based NLP-lite).

## 3. Feature Modules

1. **Auth**: login/signup/demo identity.
2. **Users/Profile**: onboarding, profile edit, trust/badges.
3. **Requests**: create, list, filters, detail, solved state.
4. **Interactions**: "I can help", helper association, messaging.
5. **AI Center**: trends, urgency counts, recommendations.
6. **Leaderboard**: rankings and contribution summaries.
7. **Notifications**: status and match alerts.
8. **Admin (bonus)**: moderation and analytics endpoints.

## 4. Suggested Repository Structure

```text
helplytics-ai/
  client/
    src/
      app/
      pages/
      features/
      components/
      styles/
      lib/
  server/
    src/
      app.js
      config/
      modules/
        auth/
        users/
        requests/
        interactions/
        messages/
        leaderboard/
        notifications/
        ai/
      shared/
      middlewares/
```

## 5. Data Model (MongoDB ERD)

## 5.1 users

- \_id
- fullName
- email (unique)
- passwordHash
- role (`need_help` | `can_help` | `both`)
- skills: string[]
- interests: string[]
- location
- trustScore (0-100)
- badges: string[]
- contributionCount
- createdAt, updatedAt

## 5.2 requests

- \_id
- requesterId (ref users)
- title
- description
- category
- urgency (`low` | `medium` | `high`)
- tags: string[]
- status (`open` | `solved`)
- helperIds: ObjectId[]
- aiSummary
- aiMeta: { suggestedCategory, detectedUrgency, suggestedTags, rewriteHint }
- location
- createdAt, updatedAt, solvedAt

## 5.3 messages

- \_id
- requestId (ref requests)
- fromUserId (ref users)
- toUserId (ref users)
- body
- createdAt

## 5.4 notifications

- \_id
- userId (ref users)
- type (`status` | `match` | `request` | `insight`)
- title
- message
- isRead
- createdAt

## 5.5 trust_events

- \_id
- userId (ref users)
- requestId (optional ref requests)
- delta
- reason
- createdAt

## 6. API Route Map (v1)

| Method | Route                               | Purpose                                |
| ------ | ----------------------------------- | -------------------------------------- |
| POST   | /api/v1/auth/signup                 | Create account                         |
| POST   | /api/v1/auth/login                  | Authenticate user                      |
| POST   | /api/v1/auth/demo-session           | Start demo identity session            |
| GET    | /api/v1/users/me                    | Current profile                        |
| PATCH  | /api/v1/users/me                    | Update profile/onboarding fields       |
| GET    | /api/v1/requests                    | List requests with filters             |
| POST   | /api/v1/requests                    | Create request                         |
| GET    | /api/v1/requests/:id                | Request details                        |
| PATCH  | /api/v1/requests/:id                | Update request                         |
| POST   | /api/v1/requests/:id/help           | Mark current user as helper            |
| POST   | /api/v1/requests/:id/solve          | Mark request solved                    |
| GET    | /api/v1/messages                    | List conversations/messages            |
| POST   | /api/v1/messages                    | Send message                           |
| GET    | /api/v1/leaderboard                 | Ranked helper list                     |
| GET    | /api/v1/notifications               | Notification feed                      |
| PATCH  | /api/v1/notifications/:id/read      | Mark single read                       |
| POST   | /api/v1/ai/analyze-request          | Categorization, urgency, tags, rewrite |
| GET    | /api/v1/ai/insights                 | Trends and recommendation snapshot     |
| GET    | /api/v1/admin/analytics             | Admin analytics (bonus)                |
| PATCH  | /api/v1/admin/requests/:id/moderate | Admin moderation (bonus)               |

## 7. AI Engine (Deterministic, Hackathon-Safe)

1. **Categorization**: keyword dictionary by category.
2. **Urgency detection**: deadline/intensity phrase scoring.
3. **Tag suggestion**: extracted skills/tools/keywords.
4. **Rewrite hint**: template-based prompt to improve clarity.

All outputs are explainable and generated without external paid AI dependency.

## 8. UI Architecture

1. Reusable design tokens for colors, spacing, radii, shadows, typography.
2. Shared page shell (top nav + content wrapper).
3. Reusable primitives: Card, Badge, Pill, Button, SectionTitle, Input, Select, TextArea.
4. Page-specific feature components with strict composition rules to maintain screenshot fidelity.

## 9. Security & Quality Baseline

1. Password hashing (bcrypt).
2. JWT verification middleware.
3. Request payload validation (zod/joi).
4. CORS allowlist + helmet + rate limiting.
5. Centralized error handler with consistent JSON error responses.

## 10. CI/CD-Ready

1. Lint, build, and test scripts in both client/server.
2. Environment templates (`.env.example`).
3. Automated checks via GitHub Actions workflow.

## 11. Pixel-Perfect Implementation Contract

1. Build against provided image references first.
2. Lock desktop baseline sizing and spacing before responsive adaptation (**1600x900** reference viewport).
3. Do not alter hierarchy, card ordering, CTA placement, or visual density from references.
