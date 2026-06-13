Modulance Quality — Full Dependency Report
Reporting only. No implementation. Scope: Every Work Package, Sprint, and Task from the 5-Week Readiness Assessment, with complete internal and cross-program dependency classification.

Part 1 — Work Package Dependency Detail
WP-1: Identity & Access
Program: XXX.ai Platform Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
None	—	WP1-S2 (org provisioning)	Yes
None	—	Modulance WP2-S1 (JWT middleware end-to-end)	Yes
None	—	Modulance WP4-S1 (resolveAiConfig)	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
None	—
Blocks (Cross-Program)	Type
Modulance / WP-2: Schema & Data / WP2-S1 / JWT middleware JWKS validation	Hard
Modulance / WP-2: Schema & Data / WP2-S1 / JWT middleware end-to-end test	Hard
Modulance / WP-4: AI Config / WP4-S1 / resolveAiConfig function	Hard
Modulance / WP-3: Query Layer / WP3-S6 / Singleton replacement (org identity required)	Hard
Modulance / WP-5: Admin Hardening / WP5-S1 / Admin route guards (role from JWT)	Hard
Modulance / WP-6: Isolation Validation / WP6-S3 / Two-org validation baseline	Hard
Modulance / WP-7: Customer Onboarding / WP7-S1 / Customer org provisioned	Hard
WP-2: Organization Isolation — Schema & Data
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP1-S1 (JWKS URL — mockable for unit tests)	Soft	WP3-S1 through WP3-S6	Yes
WP2-S2 must complete before WP2-S3	Hard	WP2-S3 (backfill)	Yes
WP2-S3 must complete before WP3 begins	Hard	All of WP-3	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S1 / GET /.well-known/jwks.json live (for end-to-end JWT validation)	Soft (mockable for unit tests; hard for integration)
Blocks (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S2 / Verify both org JWTs accepted by Modulance	Hard
WP-3: Organization Isolation — Query Layer
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP2-S1 (JWT middleware — identity context required)	Hard	All WP-3 sprints	Yes
WP2-S3 (backfill complete — column must exist and be populated)	Hard	All WP-3 sprints	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S1 / All 3 endpoints deployed (transitively via WP2-S1)	Hard
Blocks (Cross-Program)	Type
None directly — WP-3 output is consumed by WP-6 which then gates WP-7 and XXX.ai WP1-S3	Informational
WP-4: AI Configuration Isolation
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP3-S6 (interpretation-config singleton replaced — async isGptAvailable required)	Hard	WP4-S1	Yes
WP4-S1 must complete before WP4-S2	Hard	WP4-S2	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S1 / GET /api/orgs/:organizationId/ai-config live	Hard
XXX.ai / WP-1 / WP1-S2 / Test Org B AI config must exist before WP4-S1 can be validated	Hard
Blocks (Cross-Program)	Type
None — WP-4 output feeds WP-6 which gates XXX.ai WP1-S3	Informational
WP-5: Admin & Security Hardening
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP2-S1 (JWT middleware — role claim required)	Hard	WP5-S1, WP5-S2	Yes (parallel with WP-3)
WP2-S3 (backfill — org filter on admin queries)	Hard	WP5-S2	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S1 / JWT carries role claim	Hard
Blocks (Cross-Program)	Type
None directly	—
WP-6: Isolation Validation
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP3 complete (all query filter groups)	Hard	WP6-S1, WP6-S2, WP6-S3	Yes
WP4 complete (AI config isolation)	Hard	WP6-S3 (V-AI test group)	Yes
WP5 complete (admin hardening)	Hard	WP6-S3 (V-ADMIN test group)	Yes
WP6-S1 (STOP criteria) must pass before WP6-S3	Hard	WP6-S3	Yes
WP6-S2 (transitive tests) must pass before WP6-S3	Hard	WP6-S3	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S2 / Test Org B provisioned + JWT valid	Hard
XXX.ai / WP-1 / WP1-S2 / Test Org B AI config exists	Hard
Blocks (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S3 / Real customer org provisioning authorized (gate condition)	Hard
WP-7: Customer Onboarding
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP6-S3 all 8 exit criteria pass	Hard	WP7-S1	Yes
WP7-S1 before WP7-S2	Hard	WP7-S2	Yes
WP7-S2 before WP7-S4	Hard	WP7-S4	Yes
WP2-S1 (JWT middleware — audit events need identity)	Hard	WP7-S3	No (parallel, not blocking WP7-S4)
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S3 / Real customer org + user + AI config created	Hard
XXX.ai / WP-1 / WP1-S3 / Customer JWT issued	Hard
Blocks (Cross-Program)	Type
None — WP-7 is the terminal work package	—
Part 2 — Sprint Dependency Detail
WP1-S1: XXX.ai Minimum Endpoints
Program: XXX.ai Platform Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
None	—	WP1-S2 (org provisioning)	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
None	—
Blocks (Cross-Program)	Type
Modulance / WP-2 / WP2-S1 / JWT middleware JWKS validation (end-to-end)	Hard
Modulance / WP-4 / WP4-S1 / resolveAiConfig calls ai-config endpoint	Hard
Modulance / WP-3 / WP3-S6 / Singleton replacement needs org identity	Hard
Modulance / WP-5 / WP5-S1 / Admin route guards need role claim from JWT	Hard
WP1-S2: Org Provisioning — Internal
Program: XXX.ai Platform Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP1-S1 complete	Hard	WP1-S3 (customer provisioning)	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
Modulance / WP-2 / WP2-S1 / JWT middleware live (to verify JWTs are accepted)	Hard
Blocks (Cross-Program)	Type
Modulance / WP-6 / WP6-S3 / Two-org validation baseline restore	Hard
Modulance / WP-6 / WP6-S3 / V-AI-1 through V-AI-7 (Test Org B AI config required)	Hard
WP1-S3: Org Provisioning — Customer
Program: XXX.ai Platform Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP1-S2 (internal orgs provisioned first)	Soft	WP7-S1	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
Modulance / WP-6 / WP6-S3 / All 8 exit criteria pass (authorization gate)	Hard
Blocks (Cross-Program)	Type
Modulance / WP-7 / WP7-S1 / Customer org provisioned in Modulance context	Hard
Modulance / WP-7 / WP7-S2 / Customer JWT verification	Hard
WP2-S1: JWT Middleware Stack
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP1-S1 JWKS URL (mockable for unit tests)	Soft	WP3-S1 through WP3-S6	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S1 / GET /.well-known/jwks.json live	Soft (mock for unit; hard for integration)
XXX.ai / WP-1 / WP1-S1 / POST /auth/login issues valid RS256 JWT	Soft (mock for unit; hard for integration)
Blocks (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S2 / Verify both org JWTs accepted by Modulance	Hard
WP2-S2: Schema Migration
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
None (fully independent — can run in parallel with WP2-S1)	—	WP2-S3	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
None	—
Blocks (Cross-Program)	Type
None directly	—
WP2-S3: Backfill & Snapshot
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP2-S2 complete (column must exist)	Hard	WP3-S1 through WP3-S5	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
None	—
Blocks (Cross-Program)	Type
None directly	—
WP3-S1: Group A Filters (Primary Chain)
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP2-S1 (identity context)	Hard	WP6-S1, WP6-S2	Yes
WP2-S3 (column populated)	Hard	WP6-S1, WP6-S2	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S1 / All 3 endpoints (transitively via WP2-S1)	Hard
Blocks (Cross-Program)	Type
None directly	—
Note: Contains the highest-risk single task in the entire plan — promote/POST.ts line 181 raw SQL UPDATE. Second-engineer review required before merge.

WP3-S2: Group B Filters (Authoring Surface)
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP2-S1 (identity context)	Hard	WP6-S2	Yes (parallel with WP3-S1)
WP2-S3 (column populated)	Hard	WP6-S2	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S1 (transitively via WP2-S1)	Hard
Blocks (Cross-Program)	Type
None directly	—
WP3-S3: Group C/D Filters (KO Engine + Product Pipeline)
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP2-S1 (identity context)	Hard	WP6-S2	Yes (parallel with WP3-S1, WP3-S2)
WP2-S3 (column populated)	Hard	WP6-S2	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S1 (transitively via WP2-S1)	Hard
Blocks (Cross-Program)	Type
None directly	—
WP3-S4: Group E/F Filters (Intelligence Layer)
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP2-S1 (identity context)	Hard	WP6-S2	Yes (parallel with WP3-S1 through WP3-S3)
WP2-S3 (column populated)	Hard	WP6-S2	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S1 (transitively via WP2-S1)	Hard
Blocks (Cross-Program)	Type
None directly	—
WP3-S5: INSERT Stamps
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP2-S1 (identity context for stamp source)	Hard	WP6-S1	Yes (parallel with filter groups)
WP2-S3 (column populated)	Hard	WP6-S1	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S1 (transitively via WP2-S1)	Hard
Blocks (Cross-Program)	Type
None directly	—
WP3-S6: Singleton Replacement
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP2-S1 (org identity needed to key the Map)	Hard	WP4-S1	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S1 / JWT carries organizationId claim	Hard
Blocks (Cross-Program)	Type
None directly	—
WP4-S1: resolveAiConfig Function
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP3-S6 (interpretation-config must be async-ready)	Hard	WP4-S2	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S1 / GET /api/orgs/:organizationId/ai-config live	Hard
XXX.ai / WP-1 / WP1-S2 / Test Org B AI config exists (for validation of hard-error behavior)	Hard
Blocks (Cross-Program)	Type
None directly	—
WP4-S2: AI Call Chain Threading
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP4-S1 complete	Hard	WP6-S3 (V-AI test group)	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S1 / ai-config endpoint (transitively via WP4-S1)	Hard
Blocks (Cross-Program)	Type
None directly	—
WP5-S1: Admin Route Guards
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP2-S1 (role claim from JWT)	Hard	WP6-S3 (V-ADMIN test group)	Yes (parallel with WP-3)
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S1 / JWT carries role claim	Hard
Blocks (Cross-Program)	Type
None directly	—
WP5-S2: Admin Query Scoping
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP2-S1 (identity context)	Hard	WP6-S3 (V-ADMIN test group)	Yes (parallel with WP-3)
WP2-S3 (column populated)	Hard	WP6-S3	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S1 (transitively via WP2-S1)	Hard
Blocks (Cross-Program)	Type
None directly	—
WP5-S3: Snapshot Org-Awareness
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP2-S1 (identity context)	Hard	WP6-S3 (V-SNAP test group)	Yes
WP2-S3 (column populated)	Hard	WP6-S3	Yes
WP3 complete (clean baseline snapshot requires all filters in place)	Hard	WP6-S3	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S1 (transitively via WP2-S1)	Hard
Blocks (Cross-Program)	Type
None directly	—
WP6-S1: STOP Criteria Verification
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP2 complete (S-1 through S-5)	Hard	WP6-S3	Yes
WP3 complete (S-6 through S-9)	Hard	WP6-S3	Yes
WP4 + WP5 complete (S-10 through S-14)	Hard	WP6-S3	Yes
WP6-S2 (transitive tests must pass before STOP sign-off)	Hard	WP6-S3	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S2 / Both internal org JWTs valid (S-2 verification)	Hard
Blocks (Cross-Program)	Type
None directly	—
WP6-S2: Transitive Isolation Tests
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP3 complete (all query filter groups)	Hard	WP6-S1	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S2 / Test Org B JWT valid (needed to run cross-org assertions)	Hard
Blocks (Cross-Program)	Type
None directly	—
WP6-S3: Internal Two-Org Validation
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP6-S1 all STOP criteria pass	Hard	WP7	Yes
WP6-S2 all transitive tests pass	Hard	WP7	Yes
WP5-S3 (week4-baseline snapshot ready)	Hard	WP7	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S2 / Internal Org A JWT valid	Hard
XXX.ai / WP-1 / WP1-S2 / Test Org B JWT valid	Hard
XXX.ai / WP-1 / WP1-S2 / Test Org B AI config exists	Hard
Blocks (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S3 / Real customer org provisioning (gate condition — all 8 exit criteria must pass first)	Hard
Modulance / WP-7 / WP7-S1 / Customer org provisioned in Modulance context	Hard
WP7-S1: Customer Org Provisioning
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP6-S3 all 8 exit criteria pass	Hard	WP7-S2	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S3 / Real customer org + user + membership created	Hard
XXX.ai / WP-1 / WP1-S3 / Customer AI provider config set	Hard
Blocks (Cross-Program)	Type
None — terminal	—
WP7-S2: Customer JWT Verification
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP7-S1 complete	Hard	WP7-S4	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S3 / Customer JWT issued	Hard
Blocks (Cross-Program)	Type
None — terminal	—
WP7-S3: Audit Events
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP2-S1 (identity context for event attribution)	Hard	WP7-S4 (recommended, not hard-blocking)	No
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S1 / xxx.ai audit events endpoint (if events are forwarded to xxx.ai)	Soft
Blocks (Cross-Program)	Type
None	—
WP7-S4: Customer Access Grant
Program: Modulance Customer Validation Readiness

Internal Dependencies

Depends On	Type	Blocks	Critical Path
WP7-S1 complete	Hard	None — terminal	Yes
WP7-S2 complete	Hard	None — terminal	Yes
Cross-Program Dependencies

Depends On (Cross-Program)	Type
XXX.ai / WP-1 / WP1-S3 / All customer identity artifacts live	Hard
Blocks (Cross-Program)	Type
None — terminal	—
Part 3 — Task Dependency Detail
WP1-S1 Tasks
Task: Implement POST /auth/login — RS256 JWT with 7 claims Program: XXX.ai Platform Readiness

Field	Value
Depends On (Internal)	None
Blocks (Internal)	WP1-S1 deployment task
Depends On (Cross-Program)	None
Blocks (Cross-Program)	Modulance / WP-2 / WP2-S1 / JWT middleware end-to-end test
Dependency Type	Hard (blocks Modulance integration)
Critical Path	Yes
Task: Implement GET /.well-known/jwks.json Program: XXX.ai Platform Readiness

Field	Value
Depends On (Internal)	None (parallel with login endpoint)
Blocks (Internal)	WP1-S1 deployment task
Depends On (Cross-Program)	None
Blocks (Cross-Program)	Modulance / WP-2 / WP2-S1 / JWT middleware JWKS validation
Dependency Type	Hard
Critical Path	Yes
Task: Implement GET /api/orgs/:organizationId/ai-config Program: XXX.ai Platform Readiness

Field	Value
Depends On (Internal)	None (parallel with other endpoints)
Blocks (Internal)	WP1-S1 deployment task
Depends On (Cross-Program)	None
Blocks (Cross-Program)	Modulance / WP-4 / WP4-S1 / resolveAiConfig function
Dependency Type	Hard
Critical Path	Yes
Task: Deploy all 3 endpoints to URL accessible by Modulance dev environment Program: XXX.ai Platform Readiness

Field	Value
Depends On (Internal)	All 3 endpoint implementations above
Blocks (Internal)	WP1-S2
Depends On (Cross-Program)	None
Blocks (Cross-Program)	Modulance / WP-2 / WP2-S1 (end-to-end integration)
Dependency Type	Hard
Critical Path	Yes
WP1-S2 Tasks
Task: Create Internal Org A record in xxx.ai organizations table Program: XXX.ai Platform Readiness

Field	Value
Depends On (Internal)	WP1-S1 deployed
Blocks (Internal)	Org A admin user + membership task
Depends On (Cross-Program)	None
Blocks (Cross-Program)	Modulance / WP-2 / WP2-S3 / Backfill stamps all rows with Org A ID
Dependency Type	Hard
Critical Path	Yes
Task: Create Internal Org A admin user + membership record Program: XXX.ai Platform Readiness

Field	Value
Depends On (Internal)	Org A record created
Blocks (Internal)	Org A AI config task
Depends On (Cross-Program)	None
Blocks (Cross-Program)	Modulance / WP-6 / WP6-S3 / V-VIS and V-MUT test groups (Org A actor)
Dependency Type	Hard
Critical Path	Yes
Task: Configure Internal Org A AI provider config Program: XXX.ai Platform Readiness

Field	Value
Depends On (Internal)	Org A user + membership created
Blocks (Internal)	None
Depends On (Cross-Program)	None
Blocks (Cross-Program)	Modulance / WP-4 / WP4-S1 / resolveAiConfig validation for Org A
Dependency Type	Hard
Critical Path	Yes
Task: Create Customer-like Test Org B record + admin user + membership Program: XXX.ai Platform Readiness

Field	Value
Depends On (Internal)	WP1-S1 deployed
Blocks (Internal)	Test Org B AI config task
Depends On (Cross-Program)	None
Blocks (Cross-Program)	Modulance / WP-6 / WP6-S3 / Two-org validation baseline (Org B actor required)
Dependency Type	Hard
Critical Path	Yes
Task: Configure Test Org B AI provider config Program: XXX.ai Platform Readiness

Field	Value
Depends On (Internal)	Test Org B record + user created
Blocks (Internal)	None
Depends On (Cross-Program)	None
Blocks (Cross-Program)	Modulance / WP-4 / WP4-S1 / resolveAiConfig hard-error validation (Org B config must exist)
Dependency Type	Hard
Critical Path	Yes
Task: Verify both JWTs valid and accepted by Modulance JWT middleware Program: XXX.ai Platform Readiness

Field	Value
Depends On (Internal)	Both org records + users created
Blocks (Internal)	WP1-S3 (confidence gate)
Depends On (Cross-Program)	Modulance / WP-2 / WP2-S1 / JWT middleware live
Dependency Type	Hard (bidirectional — both programs must be ready simultaneously)
Critical Path	Yes
WP1-S3 Tasks
Task: Create real customer org record in xxx.ai Program: XXX.ai Platform Readiness

Field	Value
Depends On (Internal)	WP1-S2 complete
Blocks (Internal)	Customer admin user task
Depends On (Cross-Program)	Modulance / WP-6 / WP6-S3 / All 8 exit criteria pass
Dependency Type	Hard (governing rule: no customer provisioning until Week 4 gate passes)
Critical Path	Yes
Blocks (Cross-Program)	Modulance / WP-7 / WP7-S1 / Customer org provisioned in Modulance context
Task: Create customer admin user + membership with customer's actual email Program: XXX.ai Platform Readiness

Field	Value
Depends On (Internal)	Customer org record created
Blocks (Internal)	Customer AI config task
Depends On (Cross-Program)	Modulance / WP-6 / WP6-S3 pass
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	Modulance / WP-7 / WP7-S2 / Customer JWT verification
Task: Configure customer AI provider config with customer's own key Program: XXX.ai Platform Readiness

Field	Value
Depends On (Internal)	Customer user + membership created
Blocks (Internal)	JWT issuance task
Depends On (Cross-Program)	Modulance / WP-6 / WP6-S3 pass
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	Modulance / WP-4 / WP4-S1 / resolveAiConfig(customerOrgId) returns customer key
Task: Issue customer admin's first JWT Program: XXX.ai Platform Readiness

Field	Value
Depends On (Internal)	Customer user + AI config created
Blocks (Internal)	None
Depends On (Cross-Program)	None
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	Modulance / WP-7 / WP7-S2 / T-JWT-1 through T-JWT-6
Task: Verify resolveAiConfig(customerOrgId) returns customer key, not internal key Program: XXX.ai Platform Readiness

Field	Value
Depends On (Internal)	Customer JWT issued
Blocks (Internal)	None
Depends On (Cross-Program)	Modulance / WP-4 / WP4-S1 / resolveAiConfig function live
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	Modulance / WP-7 / WP7-S4 / Customer access grant
WP2-S1 Tasks
Task: Create src/server/middleware/jwt-auth.ts — JWKS validation, 5-min cache, 7-claim extraction Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	None (JWKS URL can be mocked for unit tests)
Blocks (Internal)	require-role.ts, get-identity.ts, entry.ts registration
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 / GET /.well-known/jwks.json live (hard for integration; soft for unit)
Dependency Type	Soft (unit) / Hard (integration)
Critical Path	Yes
Blocks (Cross-Program)	XXX.ai / WP-1 / WP1-S2 / Verify both org JWTs accepted
Task: Create src/server/middleware/require-role.ts Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	jwt-auth.ts complete (role claim must be extracted first)
Blocks (Internal)	entry.ts admin route registration
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 / JWT carries role claim
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Create src/server/middleware/get-identity.ts Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	jwt-auth.ts complete
Blocks (Internal)	All query filter tasks (identity context source)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 / JWT carries organizationId claim
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Register app.use('/api', jwtAuthMiddleware) in src/server/entry.ts Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	All 3 middleware files complete
Blocks (Internal)	All API route testing
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 / All 3 endpoints deployed
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	XXX.ai / WP-1 / WP1-S2 / JWT acceptance verification
Task: Unit tests T-JWT-1 through T-JWT-6, T-ROLE-1 through T-ROLE-5 Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	All middleware files + entry.ts registration
Blocks (Internal)	WP2-S3 (confidence gate before backfill)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (for integration variants of tests)
Dependency Type	Soft (mock for unit; hard for integration)
Critical Path	Yes
Blocks (Cross-Program)	None directly
WP2-S2 Tasks
Task: Add organizationId field to all 20 tables in schema.ts (nullable initially) Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	None — fully independent
Blocks (Internal)	Migration file task
Depends On (Cross-Program)	None
Dependency Type	—
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Write migration file — 20 ALTER TABLE ... ADD COLUMN statements Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	Schema.ts updated
Blocks (Internal)	Index migration task
Depends On (Cross-Program)	None
Dependency Type	—
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Write migration file — 20 CREATE INDEX statements Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	Column migration file complete
Blocks (Internal)	Migration execution task
Depends On (Cross-Program)	None
Dependency Type	—
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Run migration against preview DB Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	Both migration files complete
Blocks (Internal)	Column verification task
Depends On (Cross-Program)	None
Dependency Type	—
Critical Path	Yes
Blocks (Cross-Program)	None directly
Note: Preview DB is ephemeral (~1h40m recycle). Migration must be re-run after every container recycle until snapshot is exported in WP2-S3.

Task: Verify SHOW COLUMNS FROM <table> confirms column on all 20 tables Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	Migration executed
Blocks (Internal)	WP2-S3 (backfill cannot start until column confirmed)
Depends On (Cross-Program)	None
Dependency Type	—
Critical Path	Yes
Blocks (Cross-Program)	None directly
WP2-S3 Tasks
Task: Write src/server/db/backfill-org-id.ts — idempotent UPDATE for all 20 tables Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S2 column verified
Blocks (Internal)	Backfill execution task
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S2 / Internal Org A ID known (needed as the backfill value)
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Run backfill script Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	Backfill script written
Blocks (Internal)	NULL verification task
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S2 / Org A ID value available
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Verify SELECT COUNT(*) FROM <table> WHERE organization_id IS NULL = 0 for all 20 tables Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	Backfill run complete
Blocks (Internal)	Snapshot export task
Depends On (Cross-Program)	None
Dependency Type	—
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Export snapshot tagged week1-post-backfill Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	NULL verification passes
Blocks (Internal)	WP3 (safe starting state)
Depends On (Cross-Program)	None
Dependency Type	—
Critical Path	Yes
Blocks (Cross-Program)	None directly
Note: This snapshot is the safety net against ephemeral DB recycles. Must be exported immediately after NULL verification passes. No WP3 work should begin without this snapshot confirmed.

Task: Verify snapshot org-awareness in import-snapshot/POST.ts Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	Snapshot exported; WP2-S1 complete (identity context)
Blocks (Internal)	WP5-S3 (snapshot org-awareness hardening)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (identity context for import validation)
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
WP3-S1 Tasks
Task: Patch projects/GET.ts, [id]/GET.ts, POST.ts — add org filter Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1 (getIdentity), WP2-S3 (column populated)
Blocks (Internal)	WP6-S1 (S-6 STOP criterion)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively via WP2-S1)
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Patch source-documents/GET.ts (all 4 branches including unscoped line 67) Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S2 (T-EX transitive tests)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Patch source-documents/[id]/GET.ts, DELETE.ts, archive/PUT.ts, impact/GET.ts, file/GET.ts Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S2
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Patch canonical-ko/registry/GET.ts, compare-merge/POST.ts Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S2
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Patch annotations/[id]/promote/POST.ts line 181 raw SQL UPDATE — add AND organization_id = '${identity.organizationId}' Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S3 (V-MUT-1 through V-MUT-9 — cross-org mutation tests)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Note: Highest-risk single task in the entire plan. Second-engineer review required before merge. Failure to patch this line means cross-org annotation mutation is possible. Customer validation cannot proceed safely if this is missed.

Task: Second-engineer review of line 181 patch before merge Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	Line 181 patch written
Blocks (Internal)	Merge to main; WP6-S3 V-MUT suite
Depends On (Cross-Program)	None
Dependency Type	Hard (formal gate, not optional)
Critical Path	Yes
Blocks (Cross-Program)	None directly
WP3-S2 Tasks
Task: Patch annotations/GET.ts, overlay/GET.ts, [id]/GET.ts, [id]/PUT.ts, [id]/DELETE.ts, [id]/review/PUT.ts, POST.ts Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S2 (T-EX-3 through T-EX-7)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes (parallel with WP3-S1)
Blocks (Cross-Program)	None directly
Task: Patch digital-twin/list/GET.ts, traceability/GET.ts, by-source/[sourceDocId]/GET.ts, [twinId]/GET.ts, [twinId]/reprocess/POST.ts Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S2
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes (parallel)
Blocks (Cross-Program)	None directly
Note: Handlers in [twinId]-named directory must use #db/client.js and #db/schema.js import aliases (Vite SSR bracket-path bug). Code review checklist item.

Task: Patch evidence-anchors/GET.ts, generate-gpt/POST.ts Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S2
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes (parallel)
Blocks (Cross-Program)	None directly
Task: Patch pdf-coordinate-anchors/GET.ts, POST.ts Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S2
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes (parallel)
Blocks (Cross-Program)	None directly
WP3-S3 Tasks
Task: Patch kpis/service.ts (11 query sites) + kpis/GET.ts Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S2
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes (parallel)
Blocks (Cross-Program)	None directly
Task: Patch platform-snapshot/GET.ts Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S2
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes (parallel)
Blocks (Cross-Program)	None directly
Task: Patch ko/service.ts + all KO API handlers Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S2 (T-EX-8 through T-EX-11)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes (parallel)
Blocks (Cross-Program)	None directly
Task: Patch product-knowledge-acquisition/service.ts — fix full-table scans at lines 312–313 Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S2
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes (parallel)
Blocks (Cross-Program)	None directly
Task: Patch knowledge-acquisition/service.ts Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S2
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes (parallel)
Blocks (Cross-Program)	None directly
WP3-S4 Tasks
Task: Patch products/service.ts + product API handlers Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S2
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes (parallel)
Blocks (Cross-Program)	None directly
Task: Patch requirements/service.ts + requirements API handlers Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S2
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes (parallel)
Blocks (Cross-Program)	None directly
Task: Patch pdf/stats/GET.ts, pdf/source-documents/GET.ts, pdf/source-documents/[id]/GET.ts Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S2
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes (parallel)
Blocks (Cross-Program)	None directly
Note: pdf/source-documents/[id]/GET.ts is in a bracket-path directory — must use #db/client.js and #db/schema.js aliases.

Task: Patch pdf/upload/POST.ts — fix productId?.trim() || null Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S2
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes (parallel)
Blocks (Cross-Program)	None directly
Task: Patch product-intelligence/service.ts, deliverable-intelligence/service.ts, standards-intelligence/service.ts (line 201) Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S2
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes (parallel)
Blocks (Cross-Program)	None directly
Task: Patch product-knowledge-objects/GET.ts Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S2
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes (parallel)
Blocks (Cross-Program)	None directly
WP3-S5 Tasks
Task: Audit all 14 INSERT sites — confirm organization_id stamped from getIdentity(res).organizationId Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1 (getIdentity available), WP2-S3 (column exists)
Blocks (Internal)	Patch task
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes (parallel with filter groups)
Blocks (Cross-Program)	None directly
Task: Patch any INSERT site missing the stamp Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	Audit complete
Blocks (Internal)	NULL verification task
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Verify SELECT COUNT(*) FROM <table> WHERE organization_id IS NULL = 0 after test inserts Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	All INSERT patches applied
Blocks (Internal)	WP6-S1 (S-8 STOP criterion)
Depends On (Cross-Program)	None
Dependency Type	—
Critical Path	Yes
Blocks (Cross-Program)	None directly
WP3-S6 Tasks
Task: Refactor interpretation-config.ts — global singleton → Map<string, KnowledgeAcquisitionConfig>; isGptAvailable() becomes async Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1 (organizationId available as Map key)
Blocks (Internal)	Caller update task; WP4-S1
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 / JWT carries organizationId
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Update 4 callers of interpretation-config to pass organizationId Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	interpretation-config refactored
Blocks (Internal)	WP4-S1
Depends On (Cross-Program)	None
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Refactor interpretation-run-store.ts — global singleton → Map<string, InterpretationRunRecord[]> Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1
Blocks (Internal)	Caller update task
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 / JWT carries organizationId
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Update 2 callers of interpretation-run-store to pass organizationId Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	run-store refactored
Blocks (Internal)	WP6-S3 (V-INTERP test group)
Depends On (Cross-Program)	None
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
WP4-S1 Tasks
Task: Create src/server/ai/resolve-ai-config.ts — org-scoped Map cache, 2-min TTL, calls xxx.ai via service token Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP3-S6 complete (interpretation-config async-ready)
Blocks (Internal)	Hard-error implementation task
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 / GET /api/orgs/:organizationId/ai-config live
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	XXX.ai / WP-1 / WP1-S3 / Verify resolveAiConfig(customerOrgId) returns customer key
Task: Implement hard error on missing org config — no fallback to getSecret('OPENAI_API_KEY') Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	resolve-ai-config.ts created
Blocks (Internal)	isGptAvailable async update
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S2 / Test Org B AI config exists (needed to validate hard-error path does NOT fire for valid orgs)
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Update isGptAvailable(organizationId) in interpretation-config.ts to call resolveAiConfig internally (async) Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	resolve-ai-config.ts + hard-error complete
Blocks (Internal)	6 call site updates
Depends On (Cross-Program)	None
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Update all 6 isGptAvailable() call sites to await the async version Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	isGptAvailable async signature complete
Blocks (Internal)	WP4-S2
Depends On (Cross-Program)	None
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Note: All 6 call sites must be converted. A missed call site silently returns a stale synchronous value. This is a silent failure mode — no compile error, no runtime exception, wrong behavior.

WP4-S2 Tasks
Task: Thread organizationId into runGptExtraction(productId, sourceId, text, config, organizationId) Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP4-S1 complete
Blocks (Internal)	gpt-extraction-engine.ts update
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively via WP4-S1)
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Thread organizationId into buildDigitalTwin, interpretLayout, generateEvidenceAnchors Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP4-S1 complete
Blocks (Internal)	Respective engine file updates
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Update gpt-extraction-engine.ts lines 738, 920 to use resolveAiConfig Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	organizationId threaded into runGptExtraction
Blocks (Internal)	WP6-S3 (V-AI-1 through V-AI-7)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 / ai-config endpoint
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Update ai-layout-interpreter.ts lines 69, 417 to use resolveAiConfig Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	organizationId threaded into interpretLayout
Blocks (Internal)	WP6-S3 (V-AI test group)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 / ai-config endpoint
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Update digital-twin-builder.ts line 114, layout-intelligence/config/PUT.ts line 25, gpt-diagnostic/GET.ts lines 29, 32 Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	organizationId threaded into respective call chains
Blocks (Internal)	WP6-S3 (V-AI test group)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 / ai-config endpoint
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
WP5-S1 Tasks
Task: Verify requireRole('admin') applied to all 10 admin route groups in entry.ts Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1 (require-role middleware)
Blocks (Internal)	Role test task
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 / JWT carries role claim
Dependency Type	Hard
Critical Path	Yes (parallel with WP-3)
Blocks (Cross-Program)	None directly
Task: Test: member-role token → 403 on all admin routes Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	requireRole applied to all 10 groups
Blocks (Internal)	WP6-S3 (V-ADMIN-1 through V-ADMIN-6)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S2 / Member-role JWT available for testing
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
WP5-S2 Tasks
Task: Patch admin/diag-annotations/GET.ts — add org filter Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S3 (V-ADMIN test group)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes (parallel with WP-3)
Blocks (Cross-Program)	None directly
Task: Patch admin/diag-canonical/GET.ts line 30 — add org filter Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S3 (V-ADMIN test group)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes (parallel)
Blocks (Cross-Program)	None directly
Task: Patch admin/diag-candidates/GET.ts line 37 — add org filter Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S3 (V-ADMIN test group)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes (parallel)
Blocks (Cross-Program)	None directly
Task: Patch admin/cleanup-ka-test-data/POST.ts — validate scope parameters belong to requesting org Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S3 (V-ADMIN test group)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes (parallel)
Blocks (Cross-Program)	None directly
Task: Patch admin/reset-ka-full/POST.ts — scope reset to requesting org only Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP6-S3 (V-ADMIN test group)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes (parallel)
Blocks (Cross-Program)	None directly
Task: Patch admin/export-snapshot/GET.ts — add org filter to all SELECT * queries Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	WP5-S3 (snapshot org-awareness), WP6-S3 (V-SNAP test group)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Patch ko/dev/seed-products/POST.ts — gate to admin + internal org only Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1 (requireRole + getIdentity)
Blocks (Internal)	WP6-S3 (V-ADMIN-5)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes (parallel)
Blocks (Cross-Program)	None directly
WP5-S3 Tasks
Task: Verify import-snapshot/POST.ts stamps organization_id on all INSERT rows Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1, WP2-S3
Blocks (Internal)	Snapshot import validation task
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 (transitively)
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Verify snapshot import validates snapshot org ID matches requesting org ID Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	Import stamp verification complete
Blocks (Internal)	Clean baseline snapshot export
Depends On (Cross-Program)	None
Dependency Type	—
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Export clean baseline snapshot tagged week4-baseline Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP3 complete (all filters in place); WP5-S2 export-snapshot patched
Blocks (Internal)	WP6-S3 (baseline restore is first step of two-org validation)
Depends On (Cross-Program)	None
Dependency Type	—
Critical Path	Yes
Blocks (Cross-Program)	None directly
WP6-S1 Tasks
Task: Verify S-1 through S-5 (schema, backfill, JWT) Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2 complete
Blocks (Internal)	WP6-S3 (partial gate)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S2 / Both org JWTs valid (S-2 verification)
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Verify S-6 through S-9 (query filters, singletons) Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP3 complete
Blocks (Internal)	WP6-S3 (partial gate)
Depends On (Cross-Program)	None
Dependency Type	—
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Verify S-10 through S-14 (AI config, admin, transitive tests) Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP4 complete, WP5 complete, WP6-S2 complete
Blocks (Internal)	WP6-S3 (final gate)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S2 / Test Org B AI config exists
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
WP6-S2 Tasks
Task: Run T-EX-1 through T-EX-14 (transitive child/join table isolation) Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP3 complete
Blocks (Internal)	WP6-S1 (S-14 STOP criterion)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S2 / Test Org B JWT valid
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Fix any failing transitive test Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	T-EX run complete; defect identified
Blocks (Internal)	Re-run task
Depends On (Cross-Program)	None
Dependency Type	Hard (conditional — only if failures exist)
Critical Path	Yes (if triggered)
Blocks (Cross-Program)	None directly
Task: Re-run T-EX suite after fixes Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	Fixes applied
Blocks (Internal)	WP6-S1 sign-off
Depends On (Cross-Program)	None
Dependency Type	Hard (conditional)
Critical Path	Yes (if triggered)
Blocks (Cross-Program)	None directly
WP6-S3 Tasks
Task: Restore week4-baseline snapshot; verify Org A intact, Org B empty Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP5-S3 week4-baseline snapshot exported
Blocks (Internal)	All V-test groups
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S2 / Both org JWTs valid
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Run V-VIS-1 through V-VIS-10 (cross-org visibility) Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	Baseline restored
Blocks (Internal)	EC-1 exit criterion
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S2 / Org A + Org B JWTs valid
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Run V-MUT-1 through V-MUT-9 (cross-org mutation) Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	Baseline restored; WP3-S1 line 181 patch merged and reviewed
Blocks (Internal)	EC-2 exit criterion
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S2 / Org A + Org B JWTs valid
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Run V-AI-1 through V-AI-7 (AI config leakage) Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP4 complete
Blocks (Internal)	EC-3 exit criterion
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S2 / Test Org B AI config exists
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Run V-INTERP-1 through V-INTERP-5 (interpretation isolation) Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP3-S6 complete
Blocks (Internal)	EC-4 + EC-5 exit criteria
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S2 / Both org JWTs valid
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Run V-ADMIN-1 through V-ADMIN-6 (admin route isolation) Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP5 complete
Blocks (Internal)	EC-6 exit criterion
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S2 / Member-role JWT for Org B
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Run V-SNAP-1 through V-SNAP-5 (snapshot isolation) Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP5-S3 complete
Blocks (Internal)	EC-7 exit criterion
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S2 / Both org JWTs valid
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Run V-FLOW-1 through V-FLOW-12 (customer-like end-to-end flow as Org B) Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	All V-VIS, V-MUT, V-AI, V-INTERP, V-ADMIN, V-SNAP groups pass
Blocks (Internal)	EC-8 exit criterion
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S2 / Test Org B full identity (JWT + AI config)
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Remediate any failing exit criterion; re-run affected test group Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	Defect identified in V-test run
Blocks (Internal)	WP7 (all 8 exit criteria must pass before WP7 begins)
Depends On (Cross-Program)	None
Dependency Type	Hard (conditional)
Critical Path	Yes (if triggered)
Blocks (Cross-Program)	XXX.ai / WP-1 / WP1-S3 / Customer org provisioning remains blocked until all 8 pass
WP7-S1 Tasks
Task: Create real customer org + user + membership in xxx.ai Program: Modulance Customer Validation Readiness (Ops)

Field	Value
Depends On (Internal)	WP6-S3 all 8 exit criteria pass
Blocks (Internal)	Customer AI config task
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S3 / Customer org record created
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
Task: Configure customer AI provider config Program: Modulance Customer Validation Readiness (Ops)

Field	Value
Depends On (Internal)	Customer org + user created
Blocks (Internal)	WP7-S2
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S3 / Customer AI config set in xxx.ai
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
WP7-S2 Tasks
Task: Run T-JWT-1 through T-JWT-6 with real customer JWT Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP7-S1 complete
Blocks (Internal)	WP7-S4
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S3 / Customer JWT issued
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
WP7-S3 Tasks
Task: Wire 5 audit event types to xxx.ai audit log Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP2-S1 (identity context for event attribution)
Blocks (Internal)	WP7-S4 (recommended, not hard-blocking)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S1 / xxx.ai audit events endpoint (if forwarding to xxx.ai)
Dependency Type	Soft
Critical Path	No
Blocks (Cross-Program)	None directly
Task: Verify snapshot/restore with customer org present Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP7-S1 complete; WP5-S3 snapshot org-awareness verified
Blocks (Internal)	WP7-S4 (confidence gate)
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S3 / Customer JWT valid
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None directly
WP7-S4 Tasks
Task: Deliver customer credentials; verify first project creation Program: Modulance Customer Validation Readiness

Field	Value
Depends On (Internal)	WP7-S1, WP7-S2 complete
Blocks (Internal)	None — terminal
Depends On (Cross-Program)	XXX.ai / WP-1 / WP1-S3 / All customer identity artifacts live
Dependency Type	Hard
Critical Path	Yes
Blocks (Cross-Program)	None — terminal
Part 4 — Cross-Program Dependency Matrix
#	Source Program	Source Package	Source Sprint	Source Task	Dep Type	Target Program	Target Package	Target Sprint	Target Task
X-01	XXX.ai	WP-1: Identity & Access	WP1-S1	POST /auth/login live	Hard	Modulance CVR	WP-2: Schema & Data	WP2-S1	JWT middleware end-to-end test
X-02	XXX.ai	WP-1: Identity & Access	WP1-S1	GET /.well-known/jwks.json live	Hard	Modulance CVR	WP-2: Schema & Data	WP2-S1	JWT middleware JWKS validation
X-03	XXX.ai	WP-1: Identity & Access	WP1-S1	GET /api/orgs/:organizationId/ai-config live	Hard	Modulance CVR	WP-4: AI Config	WP4-S1	resolveAiConfig function
X-04	XXX.ai	WP-1: Identity & Access	WP1-S1	JWT carries organizationId claim	Hard	Modulance CVR	WP-3: Query Layer	WP3-S6	Singleton replacement (Map key)
X-05	XXX.ai	WP-1: Identity & Access	WP1-S1	JWT carries role claim	Hard	Modulance CVR	WP-5: Admin Hardening	WP5-S1	Admin route guards
X-06	XXX.ai	WP-1: Identity & Access	WP1-S1	All 3 endpoints deployed to accessible URL	Hard	Modulance CVR	WP-2: Schema & Data	WP2-S1	JWT middleware integration test (not just unit)
X-07	XXX.ai	WP-1: Identity & Access	WP1-S2	Internal Org A ID value known	Hard	Modulance CVR	WP-2: Schema & Data	WP2-S3	Backfill script (Org A ID is the backfill value)
X-08	XXX.ai	WP-1: Identity & Access	WP1-S2	Internal Org A JWT valid	Hard	Modulance CVR	WP-6: Isolation Validation	WP6-S3	V-VIS and V-MUT test groups (Org A actor)
X-09	XXX.ai	WP-1: Identity & Access	WP1-S2	Test Org B JWT valid	Hard	Modulance CVR	WP-6: Isolation Validation	WP6-S3	Two-org validation baseline; all V-test groups
X-10	XXX.ai	WP-1: Identity & Access	WP1-S2	Test Org B AI config exists	Hard	Modulance CVR	WP-4: AI Config	WP4-S1	Hard-error validation (Org B config must exist to verify hard-error does NOT fire for valid orgs)
X-11	XXX.ai	WP-1: Identity & Access	WP1-S2	Test Org B AI config exists	Hard	Modulance CVR	WP-6: Isolation Validation	WP6-S3	V-AI-1 through V-AI-7
X-12	XXX.ai	WP-1: Identity & Access	WP1-S2	Member-role JWT for Org B	Hard	Modulance CVR	WP-5: Admin Hardening	WP5-S1	Test: member-role token → 403 on admin routes
X-13	XXX.ai	WP-1: Identity & Access	WP1-S2	Member-role JWT for Org B	Hard	Modulance CVR	WP-6: Isolation Validation	WP6-S3	V-ADMIN-1 through V-ADMIN-6
X-14	XXX.ai	WP-1: Identity & Access	WP1-S3	Real customer org record created	Hard	Modulance CVR	WP-7: Customer Onboarding	WP7-S1	Customer org provisioned in Modulance context
X-15	XXX.ai	WP-1: Identity & Access	WP1-S3	Customer JWT issued	Hard	Modulance CVR	WP-7: Customer Onboarding	WP7-S2	T-JWT-1 through T-JWT-6 with real customer
X-16	XXX.ai	WP-1: Identity & Access	WP1-S3	Customer AI config set	Hard	Modulance CVR	WP-7: Customer Onboarding	WP7-S3	Verify resolveAiConfig(customerOrgId) returns customer key
X-17	XXX.ai	WP-1: Identity & Access	WP1-S3	All customer identity artifacts live	Hard	Modulance CVR	WP-7: Customer Onboarding	WP7-S4	Customer access grant
X-18	Modulance CVR	WP-2: Schema & Data	WP2-S1	JWT middleware live	Hard	XXX.ai	WP-1: Identity & Access	WP1-S2	Verify both org JWTs accepted by Modulance
X-19	Modulance CVR	WP-6: Isolation Validation	WP6-S3	All 8 exit criteria pass	Hard	XXX.ai	WP-1: Identity & Access	WP1-S3	Real customer org provisioning authorized (governing rule)
X-20	Modulance CVR	WP-4: AI Config	WP4-S1	resolveAiConfig live	Hard	XXX.ai	WP-1: Identity & Access	WP1-S3	Verify resolveAiConfig(customerOrgId) returns customer key
X-21	XXX.ai	WP-1: Identity & Access	WP1-S1	xxx.ai audit events endpoint (if forwarding)	Soft	Modulance CVR	WP-7: Customer Onboarding	WP7-S3	Wire 5 audit event types
X-22	Modulance CVR	WP-6: Isolation Validation	WP6-S3	All 8 exit criteria pass	Hard	Modulance CVR	WP-7: Customer Onboarding	WP7-S1	Customer org provisioned (internal gate)
Part 5 — Cross-Program Dependency Analysis
Highest-Risk Cross-Program Dependency
X-01 / X-02 / X-03 / X-06 (treated as a single risk event): XXX.ai WP1-S1 — all 3 endpoints deployed

These four matrix entries are effectively one risk: if XXX.ai does not deliver and deploy all 3 endpoints by end of Week 1, Day 3, the following Modulance work cannot be completed on schedule:

WP2-S1 JWT middleware (integration testing blocked)
WP4-S1 resolveAiConfig (hard blocked)
WP3-S6 singleton replacement (hard blocked)
WP5-S1 admin route guards (hard blocked)
Every one of these feeds into WP6-S3 (Week 4 gate), which feeds into WP7 (customer access). There is no recovery path. A 3-day slip in WP1-S1 propagates as a 3-day slip to customer validation with no mechanism to absorb it.

Classification: Hard dependency. External program. No Modulance-side mitigation beyond mocking JWKS for unit tests.

Longest Dependency Chain
X-01/X-02/X-03: XXX.ai WP1-S1 (all 3 endpoints) → X-06: Modulance WP2-S1 (JWT middleware integration) → X-07: Modulance WP2-S3 (backfill — Org A ID required) → Modulance WP3-S1 (Group A filters) → Modulance WP3-S6 (singleton replacement) → Modulance WP4-S1 (resolveAiConfig) → Modulance WP4-S2 (AI call chain threading) → Modulance WP6-S1 (STOP criteria — S-10 through S-14) → X-09: XXX.ai WP1-S2 (Test Org B JWT valid) → Modulance WP6-S3 (two-org validation — all 59 assertions) → X-19: Modulance WP6-S3 pass gates XXX.ai WP1-S3 → X-14: XXX.ai WP1-S3 (customer org created) → Modulance WP7-S1 (customer org provisioned) → Modulance WP7-S2 (customer JWT verification) → Modulance WP7-S4 (customer access grant)
14 sequential cross-program and internal gates. This is the full critical path from first external dependency to customer access. No step can be skipped or reordered.

Dependencies That Threaten the 5-Week Validation Target
Matrix ID	Dependency	Threat Mechanism	Severity
X-01/X-02/X-03/X-06	XXX.ai WP1-S1 endpoints	External; any slip propagates with no buffer	Critical
X-09	Test Org B JWT valid (WP1-S2)	Required for Week 4 gate; if provisioning is delayed, 59 assertions cannot run	High
X-10/X-11	Test Org B AI config exists	Required for V-AI test group; missing config means EC-3 cannot be verified	High
X-19	WP6-S3 pass gates WP1-S3	If Week 4 gate has defects requiring remediation, WP1-S3 and all of WP7 slip	High
X-18	Modulance WP2-S1 gates XXX.ai WP1-S2 verification	Bidirectional dependency — both programs must be ready simultaneously for verification step	Medium
Dependencies That Can Be Eliminated Through Parallelization
Opportunity	How	Saves
WP2-S2 (schema migration) has no dependency on WP2-S1 (JWT middleware)	Run both in parallel from Week 1, Day 1	Up to 2 pd of elapsed time in Week 1
WP3-S2, WP3-S3, WP3-S4, WP3-S5 have no dependency on WP3-S1 (only on WP2-S1 + WP2-S3)	Assign to second engineer; all 4 groups run in parallel with WP3-S1	Up to 6 pd of elapsed time in Week 2
WP5-S1, WP5-S2, WP5-S3 have no dependency on WP3 or WP4 (only on WP2-S1 + WP2-S3)	Run in parallel with WP3 and WP4 throughout Week 2–3	Up to 3 pd of elapsed time in Week 3
WP7-S3 (audit events) depends only on WP2-S1 — not on WP6-S3	Begin audit events wiring as soon as WP2-S1 is complete (Week 1 end)	Removes audit events from Week 5 critical path
XXX.ai WP1-S2 (internal org provisioning) can begin as soon as WP1-S1 is deployed — does not need to wait for Modulance WP2-S1	Provision Org A and Test Org B immediately after endpoint deployment	Removes 0.5 pd from Week 1 critical path
Dependencies That Should Become Explicit Commitments
Commitment	Owner	Deadline	Consequence of Miss
C-1: XXX.ai delivers and deploys all 3 minimum endpoints	XXX.ai engineering	End of Week 1, Day 3	Entire downstream chain compresses; 5-week target at risk
C-2: XXX.ai provisions Internal Org A and Test Org B with valid JWTs and AI configs	XXX.ai ops	End of Week 1, Day 5	Week 4 two-org validation cannot begin on schedule
C-3: Modulance WP3-S1 line 181 patch reviewed by second engineer before merge	Modulance engineering	Week 2, Day 3	Cross-org mutation risk; V-MUT suite may fail in Week 4
C-4: Modulance exports week1-post-backfill snapshot immediately after NULL verification passes	Modulance engineering	Week 1, Day 5	Ephemeral DB recycle destroys migration work; re-work required
C-5: Modulance exports week4-baseline snapshot before Week 4 begins	Modulance engineering	Week 3, Day 5	Week 4 two-org validation cannot restore to a clean baseline
C-6: Week 4 two-org validation begins no later than Week 4, Day 1 regardless of Week 3 overrun	Modulance QA	Week 4, Day 1	Customer access slips beyond Week 5
C-7: XXX.ai provisions real customer org only after all 8 Week 4 exit criteria pass	XXX.ai ops + Modulance QA	Week 5, Day 1 (conditional)	Governing rule violation; customer exposed to unvalidated isolation boundary
C-8: XXX.ai WP1-S3 customer AI config uses customer's own key, not internal key	XXX.ai ops	Week 5, Day 1	resolveAiConfig(customerOrgId) returns wrong key; V-AI-7 equivalent fails for real customer
Report complete. No implementation performed.*

Completed




no code change, no implementation, report only. 5-Week Readiness Assessment

Context:

Customer validation is targeted in approximately 5 weeks.

Current state:

XXX.ai v0.3 Program Workspace implemented

Builder Report Ingestion implemented

Architecture Repository implemented

Advisor implemented

Builder Instruction Queue implemented

Operational Data Protection implemented

Multi-program structure exists:

XXX.ai Platform Readiness
Modulance Customer Validation Readiness
Objective:

Assess readiness to reach customer validation in 5 weeks.

Do not implement.

Return a report only.

Sections:

Current State Summary

Critical Path Analysis

XXX.ai Platform Readiness Assessment

Modulance Customer Validation Readiness Assessment

Risks

Missing Work

For each item:

Description
Estimated effort
Dependency
Risk if not completed
Readiness Work Breakdown Structure
Split all remaining work into three levels:

Level 1 — Work Package

Examples:

Identity & Access
Customer Onboarding
Organization Isolation
Advisor Workflow
Validation Readiness
Level 2 — Sprint

For each Work Package:

Sprint name
Objective
Expected outcome
Level 3 — Tasks

For each Sprint:

Concrete implementation tasks
Estimated effort
Blocking dependencies
Dependency Map
For every Work Package and Sprint:

Show:

Depends On
Blocks
Critical Path (Yes/No)
Identify:

Longest dependency chain
Highest-risk dependency
Tasks that can run in parallel
Customer Validation Gate
Define:

Conditions required before customer access
Current status of each condition
Blocking dependencies
Overall Assessment
Return:

Confidence (%) that customer validation can begin in 5 weeks
Main supporting factors
Main threats
Recommended focus areas
Important:

Optimize for customer validation readiness.

Do not optimize for architecture purity.

Do not optimize for future platform capabilities.

Focus on the minimum work required to successfully onboard and validate with the first real customer.

Structure the remaining work as:

Work Package → Sprint → Task

and include explicit dependency mapping.
Show full message
Modulance Quality — 5-Week Customer Validation Readiness Assessment
Report only. No implementation. Assessment date: Saturday, 13 June 2026 Target: Customer validation begins end of Week 5 Programs in scope: XXX.ai Platform Readiness · Modulance Customer Validation Readiness

1. Current State Summary
What Exists Today
Area	Status	Notes
XXX.ai v0.3 Program Workspace	Implemented	Multi-program structure live
Builder Report Ingestion	Implemented	Ingestion pipeline functional
Architecture Repository	Implemented	Schema and storage layer present
Advisor	Implemented	Core advisor workflow operational
Builder Instruction Queue	Implemented	Queue mechanism in place
Operational Data Protection	Implemented	Base-level protection active
Multi-program structure	Implemented	Both programs exist
Organization isolation	Not implemented	20-table schema migration pending; no org-scoped queries; no JWT middleware
Customer identity (xxx.ai)	Not implemented	3 minimum endpoints not yet built
Multi-org AI config	Not implemented	resolveAiConfig not built; global key still in use
Interpretation-config isolation	Not implemented	Global singleton; no org-scoped Map
Admin route hardening	Not implemented	No requireRole guards
Customer org provisioning	Not implemented	No real customer org exists
Internal two-org validation	Not implemented	Week 4 gate not yet runnable
Baseline Assessment
The platform has a functional single-tenant implementation. The entire multi-tenancy isolation layer — identity, schema, query filters, AI config, and admin hardening — is unbuilt. The existing implementations (Advisor, Builder Report Ingestion, Architecture Repository, Instruction Queue) are valuable but do not reduce the critical path because they are single-tenant features that will need to be org-scoped before a second organization can safely use them.

2. Critical Path Analysis
The Single Dominant Chain
XXX.ai identity endpoints live → JWT middleware testable in Modulance → 20-table schema migration + backfill → ~30 query filter sites patched → interpretation-config singleton replaced → resolveAiConfig built + AI call chains threaded → admin routes hardened → all isolation tests pass → internal two-org validation (Week 4 gate) → real customer provisioned → customer validation begins
Every step is a hard dependency on the step before it. There are 10 sequential gates before customer access is possible. There is no schedule float anywhere in this chain.

Where Parallelism Exists
Once WP2-S1 (JWT middleware) and WP2-S3 (backfill) are complete:

Query filter groups B, C/D, E/F can run in parallel with Group A — split across two engineers
Admin hardening (WP-5) can run in parallel with all of WP-3 and WP-4
Audit events wiring (WP7-S3) can begin as soon as WP2-S1 is complete — does not need to wait for Week 4 gate
WP2-S2 (schema migration) can run in parallel with WP2-S1 (JWT middleware) — no dependency between them
Highest-Risk Single Point
The XXX.ai identity endpoints are an external dependency on a different codebase. A 3-day slip in WP1-S1 propagates as a 3-day slip to customer validation with no recovery mechanism.

3. XXX.ai Platform Readiness Assessment
Minimum Deliverables Required
Deliverable	Status	Effort	Week Required
POST /auth/login — RS256 JWT with 7 claims	Not built	1 pd	Week 1
GET /.well-known/jwks.json — JWKS public key	Not built	0.5 pd	Week 1
GET /api/orgs/:organizationId/ai-config — org AI config	Not built	1 pd	Week 1
Internal Org A record + user + membership	Not built	0.25 pd	Week 1
Test Org B record + user + membership + AI config	Not built	0.5 pd	Week 3
Real customer org + user + AI config	Not built	0.5 pd	Week 5 (conditional on Week 4 gate)
Total XXX.ai effort: ~3.75 pd

Assessment: Achievable if the 3 minimum endpoints are prioritized in Week 1. At risk if any other XXX.ai work competes for the same engineering time in Week 1.

4. Modulance Customer Validation Readiness Assessment
Implementation Work Remaining
Work Area	Effort	Week
JWT middleware + requireRole + getIdentity	2 pd	Week 1
Schema migrations (20 tables)	2 pd	Week 1
Backfill all existing rows + snapshot	1.5 pd	Week 1
Group A query filters (primary chain + raw SQL line 181)	2 pd	Week 2
Group B query filters (authoring + digital twin)	2 pd	Week 2
Group C/D query filters (KO engine + product pipeline)	2 pd	Week 2
Group E/F query filters (product intelligence + standards)	2 pd	Week 2
INSERT stamps (14 sites)	1 pd	Week 2
interpretation-config + run-store singleton replacement	1.5 pd	Week 2
resolveAiConfig + 2-min TTL cache	1 pd	Week 3
AI call chain threading (4 chains, 6 files)	1 pd	Week 3
Admin route hardening (10 route groups)	1.5 pd	Week 3
Transitive isolation tests (T-EX-1 through T-EX-14)	2 pd	Week 3
STOP criteria verification (14 criteria)	1 pd	Week 3
Internal two-org validation (59 assertions, 8 groups)	6 pd	Week 4
Customer org provisioning + JWT verification	1 pd	Week 5
Audit events wiring (5 event types)	1 pd	Week 5
Snapshot + recovery with customer org present	0.5 pd	Week 5
Total remaining Modulance effort: ~31 pd across 5 weeks

Assessment: Achievable with a focused two-engineer team if XXX.ai endpoints land in Week 1 and no blocking defects emerge in Week 4.

5. Risks
R-1 — XXX.ai Endpoint Delay (Critical)
Description: The 3 minimum XXX.ai endpoints are an external dependency. If not live by end of Week 1, the entire downstream chain compresses with no buffer.

Impact: 1-day slip = 1-day slip to customer validation.

Mitigation: Mock the JWKS endpoint locally for JWT middleware unit tests. End-to-end integration testing still requires live endpoints.

R-2 — Raw SQL Line 181 promote/POST.ts (High)
Description: Highest-risk single line in the codebase. A raw SQL UPDATE with no org filter. If missed or incorrectly patched, Org A can mutate Org B annotations.

Impact: If discovered in Week 4, requires code fix + re-deploy + full V-MUT re-run. Estimated 1–2 day delay.

Mitigation: Second-engineer review required before merge. Treat as a formal code review gate.

R-3 — Ephemeral DB Container Recycle (High)
Description: Preview DB is wiped on container recycle (~every 1h40m). If a snapshot is not exported immediately after backfill, migration work is lost.

Impact: Each missed snapshot costs 30–60 minutes of re-work.

Mitigation: Snapshot export must be the last step of every migration session. Non-negotiable operational discipline.

R-4 — Week 4 Defect Discovery (Medium-High)
Description: Week 4 runs 59 test assertions across 8 test groups. A single blocking defect requires code fix + re-run of the affected group. Week 4 has no buffer.

Impact: One blocking defect pushes customer access by 3–5 days.

Mitigation: All 14 STOP criteria must pass at end of Week 3 to give Week 4 a clean starting state.

R-5 — isGptAvailable() Synchronous-to-Async Conversion (Medium)
Description: isGptAvailable() is currently synchronous. After the resolveAiConfig refactor, it must become async. There are 6 call sites. A missed call site silently returns a stale or incorrect value — no compile error, no runtime exception.

Impact: AI config leakage between orgs. Fails V-AI-5 and V-AI-6 in Week 4.

R-6 — Drizzle ORM Silent Failures (Medium)
Description: Two known Drizzle + mysql2 driver bugs: (1) .update() silently produces affectedRows=0; (2) inArray silently fails for single-element arrays. All UPDATE/DELETE must use db.execute(sql.raw(...)). All array queries must use per-ID eq() loops.

Impact: Silent data failures that pass unit tests but fail Week 4 integration validation.

R-7 — Vite SSR Bracket-Path Bug (Low-Medium)
Description: Handlers in [id]-named directories must use #db/client.js and #db/schema.js import aliases. New handler files created in bracket-path directories during the Week 2–3 filter pass without these aliases will fail silently in SSR.

Impact: Specific API routes return 500 errors. Detectable in Week 4 validation.

6. Missing Work
M-1 — XXX.ai: 3 Minimum Identity Endpoints
Description: POST /auth/login, GET /.well-known/jwks.json, GET /api/orgs/:organizationId/ai-config do not exist.

Effort: 2.5 pd (XXX.ai engineering)

Risk if not completed: Customer validation is impossible. The entire isolation architecture cannot be validated.

M-2 — JWT Middleware Stack
Description: jwtAuthMiddleware, requireRole, getIdentity do not exist. Without these, every API route is unauthenticated and org-unaware.

Effort: 2 pd

Risk if not completed: No org isolation is possible. All query filter work is meaningless without identity context.

M-3 — 20-Table Schema Migration
Description: organization_id column does not exist on any of the 20 org-scoped tables.

Effort: 2 pd

Risk if not completed: No query filter can be applied. The entire isolation architecture has no data layer.

M-4 — ~30 Query Filter Sites
Description: Every SELECT, UPDATE, DELETE across ~30 sites returns data for all organizations.

Effort: 8 pd (split across 2 engineers)

Risk if not completed: Cross-org data visibility and mutation are possible. Customer validation is a security incident.

M-5 — resolveAiConfig + AI Call Chain Threading
Description: All AI operations use a global OpenAI key. No per-org AI configuration exists.

Effort: 2 pd

Risk if not completed: AI config leakage between orgs. Fails Week 4 V-AI tests.

M-6 — Singleton Replacement
Description: interpretation-config.ts and interpretation-run-store.ts are global singletons. They leak interpretation mode and run history across orgs.

Effort: 1.5 pd

Risk if not completed: Org A can see Org B's interpretation mode and run history.

M-7 — Admin Route Hardening
Description: 10 admin route groups have no requireRole('admin') guard.

Effort: 1.5 pd

Risk if not completed: Customer users can access admin diagnostic data for all orgs.

M-8 — Internal Two-Org Validation Gate
Description: 59 test assertions across 8 test groups. Cannot be run until all 14 STOP criteria pass.

Effort: 6 pd (QA execution)

Risk if not completed: Real customer is exposed to an unvalidated isolation boundary.

7. Readiness Work Breakdown Structure
Level 1 — Work Packages
ID	Work Package	Program	Owner	Weeks
WP-1	Identity & Access	XXX.ai Platform Readiness	XXX.ai BE	Week 1
WP-2	Organization Isolation — Schema & Data	Modulance CVR	Modulance BE	Week 1
WP-3	Organization Isolation — Query Layer	Modulance CVR	Modulance BE + FS	Week 2
WP-4	AI Configuration Isolation	Modulance CVR	Modulance BE	Week 3
WP-5	Admin & Security Hardening	Modulance CVR	Modulance BE	Week 3
WP-6	Isolation Validation	Modulance CVR	QA	Week 3–4
WP-7	Customer Onboarding	XXX.ai + Modulance	Ops + QA	Week 5
Level 2 — Sprints
WP-1: Identity & Access
Sprint ID	Sprint Name	Objective	Expected Outcome
WP1-S1	XXX.ai Minimum Endpoints	Deliver the 3 endpoints required for JWT-based org identity	Modulance can validate RS256 JWTs and resolve org AI config
WP1-S2	Org Provisioning — Internal	Create Internal Org A and Test Org B records in xxx.ai	Both orgs have valid JWTs and AI configs
WP1-S3	Org Provisioning — Customer	Create real customer org, user, and AI config in xxx.ai	Customer can authenticate and receive a valid JWT
WP-2: Organization Isolation — Schema & Data
Sprint ID	Sprint Name	Objective	Expected Outcome
WP2-S1	JWT Middleware Stack	Build jwtAuthMiddleware, requireRole, getIdentity	All API routes have org identity context
WP2-S2	Schema Migration	Add organization_id to all 20 tables	Column exists; indexes created
WP2-S3	Backfill & Snapshot	Stamp all existing rows with Internal Org A ID; export snapshot	Zero NULL organization_id rows; snapshot saved
WP-3: Organization Isolation — Query Layer
Sprint ID	Sprint Name	Objective	Expected Outcome
WP3-S1	Group A Filters (Primary Chain)	Patch projects, source-documents, annotations, canonical-ko, promote raw SQL	Highest-risk query sites isolated
WP3-S2	Group B Filters (Authoring Surface)	Patch digital-twin, evidence-anchors, pdf-coordinate-anchors	Authoring surface isolated
WP3-S3	Group C/D Filters (KO Engine + Product Pipeline)	Patch KO service, product pipeline, knowledge-acquisition service	KO engine isolated
WP3-S4	Group E/F Filters (Intelligence Layer)	Patch product-intelligence, standards-intelligence, deliverable-intelligence	Intelligence layer isolated
WP3-S5	INSERT Stamps	Stamp organization_id on all 14 INSERT sites	All new rows carry org ID
WP3-S6	Singleton Replacement	Replace interpretation-config and run-store global singletons	Interpretation state isolated per org
WP-4: AI Configuration Isolation
Sprint ID	Sprint Name	Objective	Expected Outcome
WP4-S1	resolveAiConfig Function	Build org-scoped AI config resolver with 2-min TTL cache; hard error on missing config	All AI calls use org-specific key
WP4-S2	AI Call Chain Threading	Thread organizationId through all 4 AI call chains (6 files)	No AI call uses global key
WP-5: Admin & Security Hardening
Sprint ID	Sprint Name	Objective	Expected Outcome
WP5-S1	Admin Route Guards	Apply requireRole('admin') to all 10 admin route groups	Member-role tokens cannot access admin routes
WP5-S2	Admin Query Scoping	Scope all admin diagnostic queries to requesting org	Admin routes return only requesting org's data
WP5-S3	Snapshot Org-Awareness	Ensure export/import snapshot is org-isolated	Snapshots are org-isolated
WP-6: Isolation Validation
Sprint ID	Sprint Name	Objective	Expected Outcome
WP6-S1	STOP Criteria Verification	Verify all 14 STOP criteria pass	Green light for Week 4 gate
WP6-S2	Transitive Isolation Tests	Run T-EX-1 through T-EX-14	All transitive isolation tests pass
WP6-S3	Internal Two-Org Validation	Run all 59 Week 4 assertions using Org A and Test Org B	All 8 exit criteria pass; customer access gate opens
WP-7: Customer Onboarding
Sprint ID	Sprint Name	Objective	Expected Outcome
WP7-S1	Customer Org Provisioning	Create real customer org in xxx.ai with AI config	Customer can authenticate
WP7-S2	Customer JWT Verification	Run T-JWT-1 through T-JWT-6 with real customer credentials	Customer JWT accepted by Modulance
WP7-S3	Audit Events	Wire 5 audit event types	Customer actions are traceable
WP7-S4	Customer Access Grant	Deliver credentials; verify first project creation	Customer validation begins
Level 3 — Tasks
WP1-S1: XXX.ai Minimum Endpoints
Task	Effort	Blocking Dependencies
Implement POST /auth/login — RS256 JWT with 7 claims	1 pd	None
Implement GET /.well-known/jwks.json	0.5 pd	None
Implement GET /api/orgs/:organizationId/ai-config	1 pd	None
Deploy all 3 endpoints to URL accessible by Modulance dev environment	0 pd (ops)	All 3 above
WP1-S2: Org Provisioning — Internal
Task	Effort	Blocking Dependencies
Create Internal Org A record + admin user + membership	0.25 pd	WP1-S1 deployed
Configure Internal Org A AI provider config	0.1 pd	Above
Create Test Org B record + admin user + membership	0.25 pd	WP1-S1 deployed
Configure Test Org B AI provider config	0.1 pd	Above
Verify both JWTs valid and accepted by Modulance JWT middleware	0.25 pd	WP2-S1 complete
WP1-S3: Org Provisioning — Customer
Task	Effort	Blocking Dependencies
Create real customer org record + admin user + membership	0.25 pd	WP6-S3 all 8 exit criteria pass
Configure customer AI provider config with customer's own key	0.1 pd	Above
Issue customer admin's first JWT	0.05 pd	Above
Verify resolveAiConfig(customerOrgId) returns customer key, not internal key	0.1 pd	WP4-S1 live
WP2-S1: JWT Middleware Stack
Task	Effort	Blocking Dependencies
Create jwt-auth.ts — JWKS validation, 5-min cache, 7-claim extraction	1 pd	WP1-S1 JWKS URL (mockable for unit tests)
Create require-role.ts — role guard returning 403	0.5 pd	Above
Create get-identity.ts — getIdentity(res) helper	0.25 pd	Above
Register app.use('/api', jwtAuthMiddleware) in entry.ts	0.1 pd	Above
Unit tests T-JWT-1 through T-JWT-6, T-ROLE-1 through T-ROLE-5	0.5 pd	Above
WP2-S2: Schema Migration
Task	Effort	Blocking Dependencies
Add organizationId field to all 20 tables in schema.ts (nullable initially)	0.5 pd	None — parallel with WP2-S1
Write migration: 20 ALTER TABLE ... ADD COLUMN organization_id VARCHAR(36) NULL	0.75 pd	Above
Write migration: 20 CREATE INDEX idx_<table>_org ON <table>(organization_id)	0.25 pd	Above
Run migration against preview DB; verify SHOW COLUMNS on all 20 tables	0.25 pd	Above
WP2-S3: Backfill & Snapshot
Task	Effort	Blocking Dependencies
Write backfill-org-id.ts — idempotent UPDATE for all 20 tables	0.5 pd	WP2-S2 complete; WP1-S2 Org A ID known
Run backfill script	0.1 pd	Above
Verify SELECT COUNT(*) FROM <table> WHERE organization_id IS NULL = 0 for all 20 tables	0.1 pd	Above
Export snapshot tagged week1-post-backfill	0.1 pd	Above
Verify snapshot org-awareness in import-snapshot/POST.ts	0.5 pd	WP2-S1 complete
WP3-S1: Group A Filters
Task	Effort	Blocking Dependencies
Patch projects/GET.ts, [id]/GET.ts, POST.ts	0.5 pd	WP2-S1, WP2-S3
Patch source-documents/GET.ts (all 4 branches including unscoped line 67)	0.5 pd	Above
Patch source-documents/[id]/GET.ts, DELETE.ts, archive/PUT.ts, impact/GET.ts, file/GET.ts	0.5 pd	Above
Patch canonical-ko/registry/GET.ts, compare-merge/POST.ts	0.5 pd	Above
Patch annotations/[id]/promote/POST.ts line 181 — add AND organization_id = '${identity.organizationId}'	0.5 pd	Above
Second-engineer review of line 181 patch before merge	0 pd (review gate)	Above
WP3-S2: Group B Filters
Task	Effort	Blocking Dependencies
Patch annotations/GET.ts, overlay/GET.ts, [id]/GET.ts, [id]/PUT.ts, [id]/DELETE.ts, [id]/review/PUT.ts, POST.ts	1 pd	WP2-S1, WP2-S3
Patch digital-twin/list/GET.ts, traceability/GET.ts, by-source/[sourceDocId]/GET.ts, [twinId]/GET.ts, [twinId]/reprocess/POST.ts	0.75 pd	Above
Patch evidence-anchors/GET.ts, generate-gpt/POST.ts	0.25 pd	Above
Patch pdf-coordinate-anchors/GET.ts, POST.ts	0.25 pd	Above
WP3-S3: Group C/D Filters
Task	Effort	Blocking Dependencies
Patch kpis/service.ts (11 query sites) + kpis/GET.ts	0.5 pd	WP2-S1, WP2-S3
Patch platform-snapshot/GET.ts	0.25 pd	Above
Patch ko/service.ts + all KO API handlers	0.75 pd	Above
Patch product-knowledge-acquisition/service.ts — fix full-table scans at lines 312–313	0.5 pd	Above
Patch knowledge-acquisition/service.ts	0.5 pd	Above
WP3-S4: Group E/F Filters
Task	Effort	Blocking Dependencies
Patch products/service.ts + product API handlers	0.5 pd	WP2-S1, WP2-S3
Patch requirements/service.ts + requirements API handlers	0.5 pd	Above
Patch pdf/stats/GET.ts, pdf/source-documents/GET.ts, pdf/source-documents/[id]/GET.ts	0.5 pd	Above
Patch pdf/upload/POST.ts — fix productId?.trim() || null	0.25 pd	Above
Patch product-intelligence/service.ts, deliverable-intelligence/service.ts, standards-intelligence/service.ts line 201	0.5 pd	Above
Patch product-knowledge-objects/GET.ts	0.25 pd	Above
WP3-S5: INSERT Stamps
Task	Effort	Blocking Dependencies
Audit all 14 INSERT sites — confirm organization_id stamped from getIdentity(res).organizationId	0.5 pd	WP2-S1, WP2-S3
Patch any INSERT site missing the stamp	0.5 pd	Above
Verify SELECT COUNT(*) FROM <table> WHERE organization_id IS NULL = 0 after test inserts	0.25 pd	Above
WP3-S6: Singleton Replacement
Task	Effort	Blocking Dependencies
Refactor interpretation-config.ts — global singleton → Map<string, KnowledgeAcquisitionConfig>; isGptAvailable() becomes async	0.75 pd	WP2-S1
Update 4 callers of interpretation-config to pass organizationId	0.25 pd	Above
Refactor interpretation-run-store.ts — global singleton → Map<string, InterpretationRunRecord[]>	0.5 pd	WP2-S1
Update 2 callers of interpretation-run-store to pass organizationId	0.1 pd	Above
WP4-S1: resolveAiConfig Function
Task	Effort	Blocking Dependencies
Create resolve-ai-config.ts — org-scoped Map cache, 2-min TTL, calls xxx.ai via service token	1 pd	WP1-S1 ai-config endpoint live; WP3-S6 complete
Implement hard error on missing org config — no fallback to global key	0.25 pd	Above
Update isGptAvailable(organizationId) to call resolveAiConfig internally (async)	0.25 pd	Above
Update all 6 isGptAvailable() call sites to await the async version	0.5 pd	Above
WP4-S2: AI Call Chain Threading
Task	Effort	Blocking Dependencies
Thread organizationId into runGptExtraction	0.25 pd	WP4-S1
Thread organizationId into buildDigitalTwin, interpretLayout, generateEvidenceAnchors	0.75 pd	WP4-S1
Update gpt-extraction-engine.ts lines 738, 920 to use resolveAiConfig	0.25 pd	Above
Update ai-layout-interpreter.ts lines 69, 417 to use resolveAiConfig	0.25 pd	Above
Update digital-twin-builder.ts line 114, layout-intelligence/config/PUT.ts line 25, gpt-diagnostic/GET.ts lines 29, 32	0.25 pd	Above
WP5-S1: Admin Route Guards
Task	Effort	Blocking Dependencies
Verify requireRole('admin') applied to all 10 admin route groups in entry.ts	0.25 pd	WP2-S1
Test: member-role token → 403 on all admin routes	0.25 pd	Above
WP5-S2: Admin Query Scoping
Task	Effort	Blocking Dependencies
Patch admin/diag-annotations/GET.ts — add org filter	0.25 pd	WP2-S1, WP2-S3
Patch admin/diag-canonical/GET.ts line 30 — add org filter	0.25 pd	Above
Patch admin/diag-candidates/GET.ts line 37 — add org filter	0.25 pd	Above
Patch admin/cleanup-ka-test-data/POST.ts — validate scope parameters belong to requesting org	0.5 pd	Above
Patch admin/reset-ka-full/POST.ts — scope reset to requesting org only	0.5 pd	Above
Patch admin/export-snapshot/GET.ts — add org filter to all SELECT * queries	0.5 pd	Above
Patch ko/dev/seed-products/POST.ts — gate to admin + internal org only	0.25 pd	WP2-S1
WP5-S3: Snapshot Org-Awareness
Task	Effort	Blocking Dependencies
Verify import-snapshot/POST.ts stamps organization_id on all INSERT rows	0.25 pd	WP2-S1, WP2-S3
Verify snapshot import validates snapshot org ID matches requesting org ID	0.25 pd	Above
Export clean baseline snapshot tagged week4-baseline	0.1 pd	WP3 complete; WP5-S2 export-snapshot patched
WP6-S1: STOP Criteria Verification
Task	Effort	Blocking Dependencies
Verify S-1 through S-5 (schema, backfill, JWT)	0.25 pd	WP2 complete
Verify S-6 through S-9 (query filters, singletons)	0.5 pd	WP3 complete
Verify S-10 through S-14 (AI config, admin, transitive tests)	0.5 pd	WP4, WP5, WP6-S2 complete
WP6-S2: Transitive Isolation Tests
Task	Effort	Blocking Dependencies
Run T-EX-1 through T-EX-14	2 pd	WP3 complete; WP1-S2 Test Org B JWT valid
Fix any failing transitive test	Variable	Above
Re-run after fixes	0.5 pd	Above
WP6-S3: Internal Two-Org Validation
Task	Effort	Blocking Dependencies
Restore week4-baseline snapshot; verify Org A intact, Org B empty	0.5 pd	WP5-S3 complete; WP1-S2 both JWTs valid
Run V-VIS-1 through V-VIS-10 (cross-org visibility)	1 pd	Above
Run V-MUT-1 through V-MUT-9 (cross-org mutation)	1 pd	WP3-S1 line 181 patch reviewed and merged
Run V-AI-1 through V-AI-7 (AI config leakage)	1 pd	WP4 complete; WP1-S2 Test Org B AI config exists
Run V-INTERP-1 through V-INTERP-5 (interpretation isolation)	0.5 pd	WP3-S6 complete
Run V-ADMIN-1 through V-ADMIN-6 (admin route isolation)	0.5 pd	WP5 complete
Run V-SNAP-1 through V-SNAP-5 (snapshot isolation)	0.5 pd	WP5-S3 complete
Run V-FLOW-1 through V-FLOW-12 (customer-like end-to-end flow as Org B)	1 pd	All above pass
Remed*		
Completed
