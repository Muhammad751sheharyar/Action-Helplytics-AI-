# Helplytics AI - Product Requirements Document (PRD)

## 1. Product Summary

Helplytics AI is a community support platform where users can ask for help, offer help, and track contribution impact.  
Target build is a **premium, production-style hackathon MVP** with strict UI fidelity to the provided reference images.

## 2. Problem

Learners and builders need timely support, but community help is scattered and unstructured. Skilled members are available but no single workflow connects need -> match -> conversation -> resolution -> recognition.

## 3. Vision

Create a multi-page, AI-assisted platform that feels like a real SaaS product and enables:

1. Fast request creation and discovery.
2. Better matching between requesters and helpers.
3. Visible contribution tracking via trust, badges, and leaderboard.

## 4. Users & Roles

1. **Need Help**: posts requests, receives support, marks solved.
2. **Can Help**: discovers requests, offers help, contributes.
3. **Both**: switches between requester and helper flows.
4. **Admin (bonus)**: moderation and high-level analytics.

## 5. Goals

1. Pixel-perfect UI matching all provided screens.
2. Complete multi-page product flow with clear navigation.
3. Functional core workflows on MERN stack.
4. At least one AI-like capability (implemented as deterministic intelligence engine).

## 6. Non-Goals (Hackathon Scope Guardrails)

1. Real-time chat websockets are optional; polling/threaded messaging is acceptable for MVP.
2. Enterprise-grade RBAC and billing are out of scope.
3. Full moderation automation is out of scope.

## 7. Mandatory Pages & Feature Requirements

## 7.1 Landing Page

- Hero + product pitch + CTA.
- Community stats cards.
- Featured requests preview.
- Navigation to Explore, Leaderboard, AI Center, Auth.

## 7.2 Authentication Page

- Login/Signup-like entry.
- Role selection: Need Help / Can Help / Both.
- Demo identity quick-select.

## 7.3 Onboarding Page

- Name, skills, interests, location.
- AI suggestions for help areas and needed support areas.

## 7.4 Dashboard Page

- Stats cards, recent requests, AI insights, quick actions.

## 7.5 Explore / Feed Page

- Request list.
- Filters: category, urgency, skills, location.
- Request cards with tags, status, and details CTA.

## 7.6 Create Request Page

- Inputs: title, description, tags, category, urgency.
- AI assist: category suggestion, tag suggestion, rewrite hint.

## 7.7 Request Detail Page

- Full request info.
- AI summary block.
- Helper list.
- Actions: "I can help", "Mark as solved".

## 7.8 Messaging Page

- Conversation list and message send panel.

## 7.9 Leaderboard Page

- Top helpers with rankings.
- Trust score and badges.

## 7.10 AI Center Page

- Insight cards and recommendation list.
- Trend and urgency highlights.

## 7.11 Notifications Page

- Feed of status changes, matches, and request updates.

## 7.12 Profile Page

- User info, skills, contributions, trust score, badges.
- Editable identity section.

## 8. Bonus Features (Implement at least 2)

1. Trust score system.
2. Leaderboard.
3. AI suggestions engine.
4. Notification system.

## 9. AI Requirements (Mandatory)

MVP intelligence engine must provide at least one of:

1. Keyword-based categorization.
2. Urgency detection.
3. Suggested tags.
4. Request rewrite guidance.

For this build, all four are included as deterministic rule-based features (fast, explainable, hackathon-safe).

## 10. UX & Visual Requirements (Strict)

1. UI must match provided image layouts and spacing with pixel-accurate intent.
2. No browser-default styling; premium SaaS finish is required.
3. Typography: Inter/Outfit style hierarchy.
4. Aesthetic direction: Linear/Stripe/Vercel-inspired card system.
5. Preserve card radii, surface layering, tag pills, and gradient CTAs from references.
6. Keep top navigation behavior consistent across all pages.

## 11. Functional Requirements Summary

1. Create/read/update help requests.
2. Explore and filter requests.
3. Offer help and mark solved.
4. Track contributions and trust scores.
5. View notifications, leaderboard, and profile.
6. Persist user session and platform data.

## 12. Non-Functional Requirements

1. MERN stack with JavaScript across client/server.
2. Clean modular architecture.
3. Fast page load and optimized API payloads.
4. Basic security hardening (input validation, auth, CORS config, rate-limit baseline).
5. CI-ready structure and environment-based config.

## 13. Success Criteria

1. All mandatory pages implemented and navigable.
2. Core flows execute end-to-end without blockers.
3. AI-like recommendations visibly integrated.
4. UI fidelity accepted against provided references.
5. Demo-ready deployment package.

## 14. Open Decisions Requiring Confirmation

No pending open decisions.

## 15. Locked Visual Baseline
1. Pixel-perfect reference viewport is locked to **1600x900**.
2. Dashboard and Onboarding will be implemented in the same visual language as provided screenshots unless new references are supplied.
