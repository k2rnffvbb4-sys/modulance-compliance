Modulance Quality — 5-Week Customer Validation Readiness Assessment
Reporting only. No implementation. Assessment date: 13 June 2026 Target: Customer validation begins Week 5 (end of week commencing ~14 July 2026) Programs in scope: XXX.ai Platform Readiness · Modulance Customer Validation Readiness

1. Current State Summary
What Exists Today
Area	Status	Notes
XXX.ai v0.3 Program Workspace	Implemented	Multi-program structure live
Builder Report Ingestion	Implemented	Ingestion pipeline functional
Architecture Repository	Implemented	Schema and storage layer present
Advisor	Implemented	Core advisor workflow operational
Builder Instruction Queue	Implemented	Queue mechanism in place
Operational Data Protection	Implemented	Base-level protection active
Multi-program structure	Implemented	XXX.ai Platform Readiness + Modulance Customer Validation Readiness programs exist
Organization isolation	Not implemented	20-table schema migration pending; no org-scoped queries; no JWT middleware
Customer identity (xxx.ai)	Not implemented	3 minimum endpoints not yet built; no JWKS; no org AI config endpoint
Multi-org AI config	Not implemented	resolveAiConfig not built; global key still in use
Interpretation-config isolation	Not implemented	Global singleton; no org-scoped Map
Admin route hardening	Not implemented	No requireRole guards on admin routes
Customer org provisioning	Not implemented	No real customer org exists in any system
Internal two-org validation	Not implemented	Week 4 gate not yet runnable
Baseline Assessment
The platform has a functional single-tenant implementation. The entire multi-tenancy isolation layer — identity, schema, query filters, AI config, and admin hardening — is unbuilt. This is the dominant risk to the 5-week target. The existing implementations (Advisor, Builder Report Ingestion, Architecture Repository, Instruction Queue) are valuable but do not reduce the critical path because they are single-tenant features that will need to be org-scoped before a second organization can safely use them.

2. Critical Path Analysis
The Single Dominant Chain
XXX.ai identity endpoints live → JWT middleware testable in Modulance → 20-table schema migration + backfill → ~30 query filter sites patched → interpretation-config singleton replaced → resolveAiConfig built + AI call chains threaded → admin routes hardened → all isolation tests pass → internal two-org validation (Week 4 gate) → real customer provisioned → customer validation begins
Every step in this chain is a hard dependency on the step before it. There are no shortcuts. The chain has 10 sequential gates before customer access is possible.

Where Parallelism Exists
The following work can run in parallel once the schema migration is complete:

Query filter pass (Groups A, B, C, D, E, F) — can be split across two engineers
Interpretation-config refactor — independent of query filter work once schema is done
Admin route hardening — independent of query filter work once JWT middleware is live
Transitive isolation tests — can be written speculatively before the code is complete
Longest Dependency Chain
XXX.ai identity endpoints → JWT middleware → schema migration → backfill → query filters → resolveAiConfig → isolation tests → two-org validation → customer provisioning

Estimated minimum elapsed time if everything goes perfectly: 4 weeks. This leaves one week for customer onboarding and validation. There is no schedule float.

Highest-Risk Single Point
The XXX.ai identity endpoints are an external dependency on a different codebase. If they slip by even 3–4 days, the entire downstream chain compresses into the remaining time. This is the highest-risk item in the plan.

3. XXX.ai Platform Readiness Assessment
What XXX.ai Must Deliver for Customer Validation
Deliverable	Status	Effort Estimate	Week Required
POST /auth/login — issues RS256 JWT with 7 claims	Not built	1 pd	Week 1
GET /.well-known/jwks.json — JWKS public key endpoint	Not built	0.5 pd	Week 1
GET /api/orgs/:organizationId/ai-config — org AI config	Not built	1 pd	Week 1
Organization record for Internal Org A	Not built	0.25 pd	Week 1
Organization record for Customer-like Test Org B	Not built	0.25 pd	Week 3
Organization record for real customer	Not built	0.25 pd	Week 5
Customer admin user + membership record	Not built	0.25 pd	Week 5
Customer AI provider config (customer's own key)	Not built	0.25 pd	Week 5
Total XXX.ai effort for customer validation: ~3.75 pd

XXX.ai Readiness Assessment
XXX.ai must deliver the 3 minimum endpoints in Week 1. This is a hard external dependency. The v0.3 Program Workspace, Builder Report Ingestion, Architecture Repository, Advisor, and Instruction Queue are valuable platform capabilities but are not on the critical path to customer validation. They do not unblock any Modulance isolation work.

XXX.ai Platform Readiness for 5-week target: Achievable if endpoints are prioritized in Week 1. At risk if any other XXX.ai work competes for the same engineering time.

4. Modulance Customer Validation Readiness Assessment
Implementation Work Remaining
Work Area	Files Affected	Effort	Week
JWT middleware + requireRole + getIdentity	3 new files + entry.ts	2 pd	Week 1
Schema migrations (20 tables)	schema.ts + migration file	2 pd	Week 1
Backfill all existing rows	New script	1 pd	Week 1
Snapshot org-awareness	import-snapshot/POST.ts	0.5 pd	Week 1
Group A query filters (primary chain + raw SQL line 181)	5 files	2 pd	Week 2
Group B query filters (authoring + digital twin)	~12 files	2 pd	Week 2
Group C/D query filters (KO engine + product pipeline)	~10 files	2 pd	Week 2
Group E/F query filters (product intelligence + standards)	~8 files	2 pd	Week 2
INSERT stamps (14 sites)	~14 files	1 pd	Week 2
interpretation-config singleton → org-scoped Map	1 core file + 4 callers	1 pd	Week 2
interpretation-run-store singleton → org-scoped Map	1 core file + 2 callers	0.5 pd	Week 2
resolveAiConfig function + 2-min TTL cache	1 new file	1 pd	Week 3
AI call chain threading (4 chains, 6 files)	6 files	1 pd	Week 3
Admin route hardening (10 route groups)	entry.ts + 8 admin handlers	1.5 pd	Week 3
Transitive isolation tests (T-EX-1 through T-EX-14)	Test files	2 pd	Week 3
Full T-ISO suite run (T-ISO-1 through T-ISO-12)	QA execution	1 pd	Week 3
Provision Test Org B identity in xxx.ai	Ops	0.5 pd	Week 3
Week 4 internal two-org validation (59 assertions)	QA execution	6 pd	Week 4
Real customer org provisioned in xxx.ai	Ops	0.5 pd	Week 5
JWT end-to-end with real customer credentials	QA	0.5 pd	Week 5
Audit events wiring (5 event types)	1 new file + 5 handlers	1 pd	Week 5
Snapshot + recovery with customer org present	Ops + QA	0.5 pd	Week 5
Total remaining Modulance implementation effort: ~33.5 pd across 5 weeks

Modulance Readiness Assessment
The implementation work is well-defined and scoped. The risk is not ambiguity — it is volume and sequential dependency. Weeks 1 and 2 are the most loaded weeks (~18 pd combined) and both depend on XXX.ai delivering endpoints in Week 1. Week 3 is the last implementation week and must end with all 14 STOP criteria passing. Week 4 is validation-only. Week 5 is onboarding.

Modulance Customer Validation Readiness for 5-week target: Achievable with a focused two-engineer team if XXX.ai endpoints land in Week 1 and no blocking defects emerge in Week 4.

5. Risks
R-1 — XXX.ai Endpoint Delay (Critical)
Description: The 3 minimum XXX.ai endpoints are an external dependency. If they are not live by end of Week 1, the JWT middleware cannot be tested end-to-end, and the entire downstream chain compresses.

Estimated impact: 1-day slip in XXX.ai endpoints = 1-day slip in customer validation. No buffer exists.

Dependency: Hard. Nothing in Weeks 2–5 can be fully validated without live XXX.ai endpoints.

Risk if not completed on time: Customer validation slips beyond Week 5.

Mitigation: Mock the JWKS endpoint locally for unit testing of JWT middleware. This allows Week 1 JWT middleware work to proceed in parallel with XXX.ai endpoint delivery. End-to-end integration testing still requires live endpoints.

R-2 — Raw SQL Line 181 (promote/POST.ts) (High)
Description: The highest-risk single line in the codebase. A raw SQL UPDATE with no org filter. If this line is missed or incorrectly patched, Org A can mutate Org B annotations. This is a data integrity and security defect, not a functional bug.

Estimated impact: If discovered in Week 4 validation, requires a code fix, re-deploy, and re-run of the full mutation test suite (V-MUT-1 through V-MUT-9). Estimated 1–2 day delay.

Dependency: Must be patched in Week 2 Group A filter pass. Requires second-engineer review before merge.

Risk if not completed: Cross-org data mutation is possible. Customer validation cannot proceed.

R-3 — Ephemeral DB Container Recycle (High)
Description: The preview DB is wiped on container recycle (~every 1h40m). Schema migrations and backfill must be re-run after every recycle. If a snapshot is not exported immediately after backfill, the migration work is lost.

Estimated impact: Each missed snapshot costs 30–60 minutes of re-work. In a compressed 5-week schedule, repeated re-work is a meaningful risk.

Dependency: Snapshot export must be the last step of every migration session.

Risk if not completed: Migration work is silently lost; team discovers the loss when testing fails.

R-4 — Week 4 Defect Discovery (Medium-High)
Description: Week 4 runs 59 test assertions across 8 test groups. If any exit criterion fails, Week 5 is blocked until the defect is fixed and the affected test group is re-run in full. The Week 4 schedule has no buffer for defect remediation.

Estimated impact: A single blocking defect in Week 4 could push customer access by 3–5 days.

Dependency: All 14 STOP criteria must pass at end of Week 3 to give Week 4 a clean starting state.

Risk if not completed: Customer validation slips. Real customer is not provisioned until Week 4 exit criteria pass.

R-5 — isGptAvailable() Synchronous-to-Async Conversion (Medium)
Description: isGptAvailable() is currently synchronous. After the resolveAiConfig refactor in Week 3, it must become async. There are 6 call sites. If any call site is missed, the function silently returns a stale or incorrect value.

Estimated impact: If missed, GPT extraction may use the wrong org's AI config or fail silently for one org while appearing to work for another.

Dependency: Must be completed as part of Week 3 resolveAiConfig work.

Risk if not completed: AI config leakage between orgs. Fails V-AI-5 and V-AI-6 in Week 4.

R-6 — Drizzle ORM Silent Failures (Medium)
Description: Two known Drizzle + mysql2 driver bugs: (1) .update() silently produces affectedRows=0; (2) inArray silently fails for single-element arrays. All UPDATE/DELETE operations must use db.execute(sql.raw(...)). All array queries must use per-ID eq() loops.

Estimated impact: Silent data failures that pass unit tests but fail integration tests. Difficult to diagnose.

Dependency: Must be applied consistently across all 30+ query filter sites in Week 2.

Risk if not completed: Isolation tests pass in unit testing but fail in Week 4 integration validation.

R-7 — Vite SSR Bracket-Path Bug (Low-Medium)
Description: Handlers in [id]-named directories must use #db/client.js and #db/schema.js import aliases. If any new handler files are created in bracket-path directories during the Week 2–3 filter pass without using these aliases, they will fail silently in SSR.

Estimated impact: Localized to specific routes. Detectable in development but easy to miss in a high-volume code change week.

Dependency: Must be enforced as a code review checklist item during Week 2.

Risk if not completed: Specific API routes return 500 errors in production. Detectable in Week 4 validation.

6. Missing Work
M-1 — XXX.ai: 3 Minimum Identity Endpoints
Description: POST /auth/login, GET /.well-known/jwks.json, GET /api/orgs/:organizationId/ai-config do not exist. These are the foundation of the entire multi-org identity model.

Estimated effort: 2.5 pd (XXX.ai engineering)

Dependency: Blocks all JWT middleware work in Modulance.

Risk if not completed: The entire isolation architecture cannot be validated. Customer validation is impossible.

M-2 — Modulance: JWT Middleware Stack
Description: jwtAuthMiddleware, requireRole, getIdentity do not exist. Without these, every API route is unauthenticated and org-unaware.

Estimated effort: 2 pd

Dependency: Requires XXX.ai JWKS endpoint URL (can be mocked for unit tests).

Risk if not completed: No org isolation is possible. All query filter work is meaningless without identity context.

M-3 — 20-Table Schema Migration
Description: organization_id column does not exist on any of the 20 org-scoped tables. Without this column, no query filter can be applied.

Estimated effort: 2 pd

Dependency: Independent of JWT middleware. Can run in parallel.

Risk if not completed: The entire isolation architecture has no data layer to enforce against.

M-4 — ~30 Query Filter Sites
Description: Every SELECT, UPDATE, DELETE across ~30 sites in ~15 files returns data for all organizations. No org boundary exists at the query level.

Estimated effort: 8 pd (split across 2 engineers)

Dependency: Requires schema migration + backfill complete. Requires JWT middleware for identity context.

Risk if not completed: Cross-org data visibility and mutation are possible. Customer validation is a security incident waiting to happen.

M-5 — resolveAiConfig + AI Call Chain Threading
Description: All AI operations currently use a global OpenAI key. There is no per-org AI configuration. resolveAiConfig does not exist.

Estimated effort: 2 pd

Dependency: Requires XXX.ai GET /api/orgs/:organizationId/ai-config endpoint live.

Risk if not completed: All orgs share one AI key. AI config leakage between orgs. Fails Week 4 V-AI tests.

M-6 — Interpretation-Config and Run-Store Singleton Replacement
Description: Both interpretation-config.ts and interpretation-run-store.ts are global singletons. They leak interpretation mode and run history across orgs.

Estimated effort: 1.5 pd

Dependency: Requires JWT middleware for org identity.

Risk if not completed: Org A can see Org B's interpretation mode and run history. Fails Week 4 V-INTERP tests.

M-7 — Admin Route Hardening
Description: 10 admin route groups have no requireRole('admin') guard. Any authenticated user can access diagnostic, cleanup, reset, and seed endpoints.

Estimated effort: 1.5 pd

Dependency: Requires JWT middleware.

Risk if not completed: Customer users can access admin diagnostic data for all orgs. Fails Week 4 V-ADMIN tests.

M-8 — Internal Two-Org Validation (Week 4 Gate)
Description: 59 test assertions across 8 test groups using Internal Org A and Customer-like Test Org B. This gate does not exist yet and cannot be run until all Week 3 STOP criteria pass.

Estimated effort: 6 pd (QA execution)

Dependency: All 14 STOP criteria must pass at end of Week 3.

Risk if not completed: Real customer is exposed to an unvalidated isolation boundary. This is the primary safety gate before customer access.

M-9 — Audit Events Wiring
Description: No audit events are emitted for any KO lifecycle action. Recommended before customer access for traceability.

Estimated effort: 1 pd

Dependency: Requires XXX.ai audit events table and endpoint. Requires JWT middleware for identity.

Risk if not completed: No audit trail for customer actions. Acceptable for initial validation but creates a gap in operational traceability.

7. Readiness Work Breakdown Structure
Level 1 — Work Packages
ID	Work Package	Program	Owner	Weeks
WP-1	Identity & Access	XXX.ai Platform Readiness	XXX.ai BE	Week 1
WP-2	Organization Isolation — Schema & Data	Modulance	Modulance BE	Week 1
WP-3	Organization Isolation — Query Layer	Modulance	Modulance BE + FS	Week 2
WP-4	AI Configuration Isolation	Modulance + XXX.ai	Modulance BE	Week 3
WP-5	Admin & Security Hardening	Modulance	Modulance BE	Week 3
WP-6	Isolation Validation	Modulance	QA	Week 3–4
WP-7	Customer Onboarding	XXX.ai + Modulance	Ops + QA	Week 5
Level 2 — Sprints
WP-1: Identity & Access
Sprint ID	Sprint Name	Objective	Expected Outcome
WP1-S1	XXX.ai Minimum Endpoints	Deliver the 3 endpoints required for JWT-based org identity	Modulance can validate RS256 JWTs and resolve org AI config
WP1-S2	Org Provisioning — Internal	Create Internal Org A and Test Org B records in xxx.ai	Both orgs have valid JWTs and AI configs
WP1-S3	Org Provisioning — Customer	Create real customer org, user, and AI config in xxx.ai	Customer can authenticate and receive a valid JWT
WP-2: Organization Isolation — Schema & Data
Sprint ID	Sprint Name	Objective	Expected Outcome
WP2-S1	JWT Middleware Stack	Build jwtAuthMiddleware, requireRole, getIdentity in Modulance	All API routes have org identity context
WP2-S2	Schema Migration	Add organization_id to all 20 tables	Column exists; indexes created
WP2-S3	Backfill & Snapshot	Stamp all existing rows with Internal Org A ID; export snapshot	Zero NULL organization_id rows; snapshot saved
WP-3: Organization Isolation — Query Layer
Sprint ID	Sprint Name	Objective	Expected Outcome
WP3-S1	Group A Filters (Primary Chain)	Patch projects, source-documents, annotations, canonical-ko, promote raw SQL	Highest-risk query sites isolated
WP3-S2	Group B Filters (Authoring Surface)	Patch digital-twin, evidence-anchors, pdf-coordinate-anchors	Authoring surface isolated
WP3-S3	Group C/D Filters (KO Engine + Product Pipeline)	Patch KO service, product pipeline, knowledge-acquisition service	KO engine isolated
WP3-S4	Group E/F Filters (Intelligence Layer)	Patch product-intelligence, standards-intelligence, deliverable-intelligence	Intelligence layer isolated
WP3-S5	INSERT Stamps	Stamp organization_id on all 14 INSERT sites	All new rows carry org ID
WP3-S6	Singleton Replacement	Replace interpretation-config and run-store global singletons with org-scoped Maps	Interpretation state isolated per org
WP-4: AI Configuration Isolation
Sprint ID	Sprint Name	Objective	Expected Outcome
WP4-S1	resolveAiConfig Function	Build org-scoped AI config resolver with 2-min TTL cache; hard error on missing config	All AI calls use org-specific key
WP4-S2	AI Call Chain Threading	Thread organizationId through all 4 AI call chains (6 files)	No AI call uses global key
WP-5: Admin & Security Hardening
Sprint ID	Sprint Name	Objective	Expected Outcome
WP5-S1	Admin Route Guards	Apply requireRole('admin') to all 10 admin route groups	Member-role tokens cannot access admin routes
WP5-S2	Admin Query Scoping	Scope all admin diagnostic queries to requesting org	Admin routes return only requesting org's data
WP5-S3	Snapshot Org-Awareness	Ensure export/import snapshot passes organization_id through correctly	Snapshots are org-isolated
WP-6: Isolation Validation
Sprint ID	Sprint Name	Objective	Expected Outcome
WP6-S1	STOP Criteria Verification	Verify all 14 STOP criteria pass	Green light for Week 4 gate
WP6-S2	Transitive Isolation Tests	Run T-EX-1 through T-EX-14	All transitive isolation tests pass
WP6-S3	Internal Two-Org Validation	Run all 59 Week 4 assertions using Org A and Test Org B	All 8 exit criteria pass; customer access gate opens
WP-7: Customer Onboarding
Sprint ID	Sprint Name	Objective	Expected Outcome
WP7-S1	Customer Org Provisioning	Create real customer org in xxx.ai with AI config	Customer can authenticate
WP7-S2	Customer JWT Verification	Run T-JWT-1 through T-JWT-6 with real customer credentials	Customer JWT accepted by Modulance
WP7-S3	Audit Events	Wire 5 audit event types to xxx.ai audit log	Customer actions are traceable
WP7-S4	Customer Access Grant	Deliver credentials; verify first project creation	Customer validation begins
Level 3 — Tasks
WP1-S1: XXX.ai Minimum Endpoints
Task	Effort	Blocking Dependencies
Implement POST /auth/login — RS256 JWT with 7 claims (userId, organizationId, membershipId, role, issuer, audience, expiry)	1 pd	None
Implement GET /.well-known/jwks.json — return active RS256 public key(s)	0.5 pd	None
Implement GET /api/orgs/:organizationId/ai-config — service-token authenticated; return org AI provider config	1 pd	None
Deploy endpoints to a URL accessible by Modulance dev environment	0 pd (ops)	All 3 above
WP1-S2: Org Provisioning — Internal
Task	Effort	Blocking Dependencies
Create Internal Org A record in xxx.ai organizations table	0.1 pd	WP1-S1 complete
Create Internal Org A admin user + membership record	0.1 pd	Above
Configure Internal Org A AI provider config	0.1 pd	Above
Create Customer-like Test Org B record + admin user + membership	0.25 pd	WP1-S1 complete
Configure Test Org B AI provider config	0.1 pd	Above
Verify both JWTs valid and accepted by Modulance JWT middleware	0.25 pd	WP2-S1 complete
WP1-S3: Org Provisioning — Customer
Task	Effort	Blocking Dependencies
Create real customer org record in xxx.ai	0.1 pd	WP6-S3 all exit criteria pass
Create customer admin user + membership with customer's actual email	0.1 pd	Above
Configure customer AI provider config with customer's own key	0.1 pd	Above
Issue customer admin's first JWT	0.05 pd	Above
Verify resolveAiConfig(customerOrgId) returns customer key, not internal key	0.1 pd	Above
WP2-S1: JWT Middleware Stack
Task	Effort	Blocking Dependencies
Create src/server/middleware/jwt-auth.ts — JWKS validation, 5-min cache, 7-claim extraction	1 pd	WP1-S1 JWKS URL known (can mock for unit tests)
Create src/server/middleware/require-role.ts — role guard returning 403	0.5 pd	Above
Create src/server/middleware/get-identity.ts — getIdentity(res) helper	0.25 pd	Above
Register app.use('/api', jwtAuthMiddleware) in src/server/entry.ts	0.1 pd	Above
Apply requireRole('admin') to 10 admin route groups in entry.ts	0.25 pd	Above
Unit tests: T-JWT-1 through T-JWT-6, T-ROLE-1 through T-ROLE-5	0.5 pd	Above
WP2-S2: Schema Migration
Task	Effort	Blocking Dependencies
Add organizationId field to all 20 tables in src/server/db/schema.ts (nullable initially)	0.5 pd	None
Write migration file: 20 ALTER TABLE ... ADD COLUMN organization_id VARCHAR(36) NULL	0.75 pd	Above
Write migration file: 20 CREATE INDEX idx_<table>_org ON <table>(organization_id)	0.25 pd	Above
Run migration against preview DB	0.1 pd	Above
Verify SHOW COLUMNS FROM <table> confirms column on all 20 tables	0.1 pd	Above
WP2-S3: Backfill & Snapshot
Task	Effort	Blocking Dependencies
Write src/server/db/backfill-org-id.ts — idempotent UPDATE for all 20 tables	0.5 pd	WP2-S2 complete
Run backfill script	0.1 pd	Above
Verify SELECT COUNT(*) FROM <table> WHERE organization_id IS NULL = 0 for all 20 tables	0.1 pd	Above
Export snapshot tagged week1-post-backfill	0.1 pd	Above
Verify snapshot org-awareness in import-snapshot/POST.ts	0.5 pd	Above
WP3-S1: Group A Filters
Task	Effort	Blocking Dependencies
Patch projects/GET.ts, [id]/GET.ts, POST.ts — add org filter	0.5 pd	WP2-S1, WP2-S3
Patch source-documents/GET.ts (all 4 branches including unscoped line 67)	0.5 pd	Above
Patch source-documents/[id]/GET.ts, DELETE.ts, archive/PUT.ts, impact/GET.ts, file/GET.ts	0.5 pd	Above
Patch canonical-ko/registry/GET.ts, compare-merge/POST.ts	0.5 pd	Above
Patch annotations/[id]/promote/POST.ts line 181 raw SQL UPDATE — add AND organization_id = '${identity.organizationId}'	0.5 pd	Above
Second-engineer review of line 181 patch before merge	0 pd (review)	Above
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
Patch pdf/upload/POST.ts — fix `productId?.trim()		null`
Patch product-intelligence/service.ts, deliverable-intelligence/service.ts, standards-intelligence/service.ts (line 201)	0.5 pd	Above
Patch product-knowledge-objects/GET.ts	0.25 pd	Above
WP3-S5: INSERT Stamps
Task	Effort	Blocking Dependencies
Audit all 14 INSERT sites — confirm organization_id is stamped from getIdentity(res).organizationId	0.5 pd	WP2-S1, WP2-S3
Patch any INSERT site missing the stamp	0.5 pd	Above
Verify SELECT COUNT(*) FROM <table> WHERE organization_id IS NULL = 0 after test inserts	0.25 pd	Above
WP3-S6: Singleton Replacement
Task	Effort	Blocking Dependencies
Refactor interpretation-config.ts — global singleton → Map<string, KnowledgeAcquisitionConfig>; all 4 exported functions accept organizationId; isGptAvailable() becomes async	0.75 pd	WP2-S1
Update 4 callers of interpretation-config to pass organizationId	0.25 pd	Above
Refactor interpretation-run-store.ts — global singleton → Map<string, InterpretationRunRecord[]>; all 4 exported functions accept organizationId	0.5 pd	Above
Update 2 callers of interpretation-run-store to pass organizationId	0.1 pd	Above
WP4-S1: resolveAiConfig Function
Task	Effort	Blocking Dependencies
Create src/server/ai/resolve-ai-config.ts — org-scoped Map cache, 2-min TTL, calls xxx.ai via service token	1 pd	WP1-S1 (GET /api/orgs/:organizationId/ai-config live)
Implement hard error on missing org config — no fallback to getSecret('OPENAI_API_KEY')	0.25 pd	Above
Update isGptAvailable(organizationId) in interpretation-config.ts to call resolveAiConfig internally (async)	0.25 pd	Above
Update all 6 isGptAvailable() call sites to await the async version	0.5 pd	Above
WP4-S2: AI Call Chain Threading
Task	Effort	Blocking Dependencies
Thread organizationId into runGptExtraction(productId, sourceId, text, config, organizationId)	0.25 pd	WP4-S1
Thread organizationId into buildDigitalTwin(sourceDocId, organizationId)	0.25 pd	Above
Thread organizationId into interpretLayout(pages, organizationId)	0.25 pd	Above
Thread organizationId into generateEvidenceAnchors(twinId, organizationId)	0.25 pd	Above
Update gpt-extraction-engine.ts lines 738, 920 to use resolveAiConfig	0.25 pd	Above
Update ai-layout-interpreter.ts lines 69, 417 to use resolveAiConfig	0.25 pd	Above
Update digital-twin-builder.ts line 114 to use resolveAiConfig	0.1 pd	Above
Update layout-intelligence/config/PUT.ts line 25 and gpt-diagnostic/GET.ts lines 29, 32	0.1 pd	Above
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
Patch ko/dev/seed-products/POST.ts — gate to admin + internal org only	0.25 pd	Above
WP5-S3: Snapshot Org-Awareness
Task	Effort	Blocking Dependencies
Verify import-snapshot/POST.ts stamps organization_id on all INSERT rows	0.25 pd	WP2-S1, WP2-S3
Verify snapshot import validates snapshot org ID matches requesting org ID	0.25 pd	Above
Export clean baseline snapshot tagged week4-baseline	0.1 pd	WP3 complete
WP6-S1: STOP Criteria Verification
Task	Effort	Blocking Dependencies
Verify S-1 through S-5 (schema, backfill, JWT)	0.25 pd	WP2 complete
Verify S-6 through S-9 (query filters, singletons)	0.5 pd	WP3 complete
Verify S-10 through S-14 (AI config, admin, transitive tests)	0.5 pd	WP4, WP5 complete
WP6-S2: Transitive Isolation Tests
Task	Effort	Blocking Dependencies
Run T-EX-1 through T-EX-14 (transitive child/join table isolation)	2 pd	WP3 complete
Fix any failing transitive test	Variable	Above
Re-run after fixes	0.5 pd	Above
WP6-S3: Internal Two-Org Validation
Task	Effort	Blocking Dependencies
Restore week4-baseline snapshot; verify Org A intact, Org B empty	0.5 pd	WP1-S2 complete, WP5-S3 complete
Run V-VIS-1 through V-VIS-10 (cross-org visibility)	1 pd	Above
Run V-MUT-1 through V-MUT-9 (cross-org mutation)	1 pd	Above
Run V-AI-1 through V-AI-7 (AI config leakage)	1 pd	WP4 complete
Run V-INTERP-1 through V-INTERP-5 (interpretation isolation)	0.5 pd	WP3-S6 complete
Run V-ADMIN-1 through V-ADMIN-6 (admin route isolation)	0.5 pd	WP5 complete
Run V-SNAP-1 through V-SNAP-5 (snapshot isolation)	0.5 pd	WP5-S3 complete
Run V-FLOW-1 through V-FLOW-12 (customer-like end-to-end flow as Org B)	1 pd	All above pass
Remediate any failing exit criterion; re-run affected test group	Variable	Above
WP7-S1 through WP7-S4: Customer Onboarding
Task	Effort	Blocking Dependencies
Create real customer org + user + membership in xxx.ai	0.5 pd	WP6-S3 all exit criteria pass
Configure customer AI provider config	0.1 pd	Above
Run T-JWT-1 through T-JWT-6 with real customer JWT	0.5 pd	Above
Wire 5 audit event types (doc.uploaded, ko.created, ko.status_changed, ko.canonicalized ×2)	1 pd	WP2-S1
Verify snapshot/restore with customer org present	0.5 pd	Above
Deliver customer credentials; verify first project creation	0.1 pd	All above
8. Dependency Map
Work Package Level
Work Package	Depends On	Blocks	Critical Path
WP-1: Identity & Access	None	WP-2 (JWT middleware), WP-4 (AI config)	Yes
WP-2: Schema & Data	WP-1 (JWKS URL needed for JWT middleware)	WP-3, WP-5, WP-6	Yes
WP-3: Query Layer	WP-2	WP-6	Yes
WP-4: AI Config Isolation	WP-1 (ai-config endpoint), WP-3-S6 (interpretation-config)	WP-6	Yes
WP-5: Admin Hardening	WP-2	WP-6	Yes (parallel with WP-3, WP-4)
WP-6: Isolation Validation	WP-3, WP-4, WP-5	WP-7	Yes
WP-7: Customer Onboarding	WP-6 (all exit criteria pass), WP-1-S3	None	Yes
Sprint Level Dependency Map
Sprint	Depends On (Hard)	Depends On (Soft)	Blocks	Critical Path
WP1-S1: XXX.ai Endpoints	None	None	WP1-S2, WP2-S1 (end-to-end), WP4-S1	Yes
WP1-S2: Internal Org Provisioning	WP1-S1, WP2-S1	None	WP6-S3	Yes
WP1-S3: Customer Org Provisioning	WP6-S3 pass	None	WP7-S1	Yes
WP2-S1: JWT Middleware	WP1-S1 (JWKS URL; mockable)	None	WP3-S1 through WP3-S6, WP5-S1	Yes
WP2-S2: Schema Migration	None	None	WP2-S3	Yes
WP2-S3: Backfill & Snapshot	WP2-S2	None	WP3-S1 through WP3-S6	Yes
WP3-S1: Group A Filters	WP2-S1, WP2-S3	None	WP6-S1, WP6-S2	Yes
WP3-S2: Group B Filters	WP2-S1, WP2-S3	None	WP6-S2	Yes (parallel with S1)
WP3-S3: Group C/D Filters	WP2-S1, WP2-S3	None	WP6-S2	Yes (parallel with S1, S2)
WP3-S4: Group E/F Filters	WP2-S1, WP2-S3	None	WP6-S2	Yes (parallel with S1, S2, S3)
WP3-S5: INSERT Stamps	WP2-S1, WP2-S3	None	WP6-S1	Yes (parallel with filter groups)
WP3-S6: Singleton Replacement	WP2-S1	None	WP4-S1	Yes
WP4-S1: resolveAiConfig	WP1-S1 (ai-config endpoint), WP3-S6	None	WP4-S2, WP6-S3	Yes
WP4-S2: AI Call Chain Threading	WP4-S1	None	WP6-S3	Yes
WP5-S1: Admin Route Guards	WP2-S1	None	WP6-S3	Yes (parallel with WP3)
WP5-S2: Admin Query Scoping	WP2-S1, WP2-S3	None	WP6-S3	Yes (parallel with WP3)
WP5-S3: Snapshot Org-Awareness	WP2-S1, WP2-S3	None	WP6-S3	Yes
WP6-S1: STOP Criteria Verification	WP3, WP4, WP5	WP6-S3	WP6-S3	Yes
WP6-S2: Transitive Isolation Tests	WP3	None	WP6-S1	Yes
WP6-S3: Two-Org Validation	WP6-S1, WP6-S2, WP1-S2	WP7	WP7	Yes
WP7-S1: Customer Org Provisioning	WP6-S3 pass, WP1-S3	None	WP7-S2	Yes
WP7-S2: Customer JWT Verification	WP7-S1	None	WP7-S4	Yes
WP7-S3: Audit Events	WP2-S1	None	WP7-S4	No (recommended, not blocking)
WP7-S4: Customer Access Grant	WP7-S1, WP7-S2	None	None	Yes
9. Cross-Program Dependency Matrix
Source Program	Source Package	Source Sprint	Source Task	Dep Type	Target Program	Target Package	Target Sprint	Target Task
XXX.ai Platform Readiness	WP-1: Identity & Access	WP1-S1	POST /auth/login live	Hard	Modulance CVR	WP-2: Schema & Data	WP2-S1	JWT middleware end-to-end test
XXX.ai Platform Readiness	WP-1: Identity & Access	WP1-S1	GET /.well-known/jwks.json live	Hard	Modulance CVR	WP-2: Schema & Data	WP2-S1	JWT middleware JWKS validation
XXX.ai Platform Readiness	WP-1: Identity & Access	WP1-S1	GET /api/orgs/:organizationId/ai-config live	Hard	Modulance CVR	WP-4: AI Config	WP4-S1	resolveAiConfig function
XXX.ai Platform Readiness	WP-1: Identity & Access	WP1-S2	Test Org B provisioned in xxx.ai	Hard	Modulance CVR	WP-6: Isolation Validation	WP6-S3	Internal two-org validation baseline
XXX.ai Platform Readiness	WP-1: Identity & Access	WP1-S2	Test Org B JWT valid	Hard	Modulance CVR	WP-6: Isolation Validation	WP6-S3	V-AI-1 through V-AI-7
XXX.ai Platform Readiness	WP-1: Identity & Access	WP1-S3	Real customer org + user + AI config	Hard	Modulance CVR	WP-7: Customer Onboarding	WP7-S1	Customer org provisioned in Modulance context
Modulance CVR	WP-2: Schema & Data	WP2-S1	JWT middleware live	Hard	XXX.ai Platform Readiness	WP-1: Identity & Access	WP1-S2	Verify both org JWTs accepted by Modulance
Modulance CVR	WP-6: Isolation Validation	WP6-S3	All 8 exit criteria pass	Hard	XXX.ai Platform Readiness	WP-1: Identity & Access	WP1-S3	Real customer org provisioning authorized
Modulance CVR	WP-4: AI Config	WP4-S1	resolveAiConfig hard-errors on missing config	Hard	XXX.ai Platform Readiness	WP-1: Identity & Access	WP1-S2	Test Org B AI config must exist before WP4-S1 can be validated
Modulance CVR	WP-7: Customer Onboarding	WP7-S3	Audit events wiring	Soft	XXX.ai Platform Readiness	WP-1: Identity & Access	WP1-S1	xxx.ai audit events endpoint must exist
XXX.ai Platform Readiness	WP-1: Identity & Access	WP1-S1	All 3 endpoints deployed	Hard	Modulance CVR	WP-3: Query Layer	WP3-S6	Singleton replacement (needs org identity)
XXX.ai Platform Readiness	WP-1: Identity & Access	WP1-S1	All 3 endpoints deployed	Soft	Modulance CVR	WP-5: Admin Hardening	WP5-S1	Admin route guards (needs role from JWT)
Cross-Program Dependency Analysis
Highest-risk cross-program dependency:

XXX.ai WP1-S1 (POST /auth/login + JWKS + ai-config endpoints) → Modulance WP2-S1 (JWT middleware) → Modulance WP3 (all query filters) → Modulance WP4 (AI config) → Modulance WP6 (validation gate) → Modulance WP7 (customer access)

This is a single external dependency that sits at the head of the entire critical path. A 2-day slip in WP1-S1 propagates as a 2-day slip to every downstream item with no recovery mechanism.

Longest dependency chain:

XXX.ai WP1-S1 → Modulance WP2-S1 → WP2-S2 → WP2-S3 → WP3-S1 → WP3-S6 → WP4-S1 → WP4-S2 → WP6-S1 → WP6-S3 → WP7-S1 → WP7-S4
12 sequential gates. Minimum elapsed time with no defects: 4 weeks.

Dependencies that threaten the 5-week validation target:

WP1-S1 delay (external; highest risk)
WP6-S3 defect discovery requiring code fix + re-run (internal; medium risk)
WP3-S1 raw SQL line 181 missed or incorrectly patched (internal; high risk if missed)
Dependencies that can be eliminated through parallelization:

WP2-S2 (schema migration) can run in parallel with WP2-S1 (JWT middleware) — no dependency between them
WP3-S2, WP3-S3, WP3-S4, WP3-S5 can all run in parallel with WP3-S1 once WP2-S3 is complete — split across two engineers
WP5-S1, WP5-S2, WP5-S3 can run in parallel with WP3 and WP4 — independent of query filter work
WP7-S3 (audit events) can begin as soon as WP2-S1 is complete — does not need to wait for WP6-S3
Dependencies that should become explicit commitments:

XXX.ai WP1-S1 complete by end of Week 1, Day 3 — this is the single commitment that most protects the 5-week target. A written commitment with a specific date removes ambiguity.
WP6-S3 begins no later than Week 4, Day 1 — if Week 3 overruns, Week 4 validation must still start on schedule or the customer access date slips.
WP3-S1 raw SQL line 181 reviewed by a second engineer before merge — this should be a formal code review gate, not a best-effort check.
10. Customer Validation Gate
Condition	Current Status	Blocking Dependency	Gate Type
XXX.ai identity endpoints live	Not built	WP1-S1	Hard
JWT middleware validates RS256 tokens	Not built	WP2-S1	Hard
JWT payload carries all 7 required claims	Not built	WP1-S1, WP2-S1	Hard
organization_id on all 20 tables	Not built	WP2-S2	Hard
All existing rows backfilled	Not built	WP2-S3	Hard
All 31 query sites org-filtered	Not built	WP3-S1 through WP3-S4	Hard
All 14 INSERT sites stamp org ID	Not built	WP3-S5	Hard
interpretation-config org-scoped	Not built	WP3-S6	Hard
interpretation-run-store org-scoped	Not built	WP3-S6	Hard
resolveAiConfig hard-errors on missing config	Not built	WP4-S1	Hard
All AI call chains use org-specific key	Not built	WP4-S2	Hard
All admin routes gated by requireRole('admin')	Not built	WP5-S1	Hard
Seed/dev routes blocked for non-internal orgs	Not built	WP5-S2	Hard
All transitive isolation tests pass	Not built	WP6-S2	Hard
All 8 Week 4 exit criteria pass (59 assertions)	Not built	WP6-S3	Hard gate — no customer access until this passes
Real customer org provisioned in xxx.ai	Not built	WP1-S3	Hard
Customer JWT accepted by Modulance	Not built	WP7-S2	Hard
Current status of gate: 0 of 17 conditions met.

Governing rule: No real customer access is allowed until all 8 Week 4 exit criteria pass in full.

<!-- END_EXECUTABLE_PLAN -->

11. Overall Assessment
Confidence: 62%
Customer validation can begin in 5 weeks with 62% confidence under current conditions.

Main Supporting Factors
1. Work is well-defined. The implementation scope is fully specified. There is no ambiguity about what needs to be built. Every file, every line, every test is identified. This is a significant advantage — the team is not discovering scope during execution.

2. Parallelism is available in Week 2. The query filter pass (~30 sites) can be split across two engineers working simultaneously on different groups. This is the highest-volume week and the parallelism is real and exploitable.

3. The existing platform is functional. The single-tenant implementation works. The isolation work is additive — it does not require rewriting existing features, only adding org filters and replacing singletons. This reduces the risk of regressions.

4. The Week 4 gate is well-designed. 59 test assertions across 8 test groups give high confidence that if Week 4 passes, the customer is entering a genuinely isolated environment. The gate is not a formality.

5. Effort estimates are realistic. Total remaining effort (~33.5 pd across 5 weeks) is achievable with a two-engineer team working at normal capacity. There is no heroic effort assumption.

Main Threats
1. XXX.ai endpoint delivery (external, uncontrolled). This is the single largest threat. If the 3 minimum endpoints are not live by end of Week 1, the entire downstream chain compresses. There is no recovery mechanism. Confidence drops to approximately 30% if WP1-S1 slips by more than 3 days.

2. Week 4 defect discovery. If any of the 59 Week 4 assertions fail, Week 5 is blocked until the defect is fixed and the affected test group is re-run. The Week 4 schedule has no buffer. A single blocking defect costs 2–4 days.

3. Ephemeral DB container recycles. Every schema migration session must end with a snapshot export. If this discipline breaks down, migration work is silently lost and must be redone. In a compressed schedule, repeated re-work is a meaningful risk.

4. Raw SQL line 181 in promote/POST.ts. This is the highest-risk single line in the codebase. If it is missed or incorrectly patched, cross-org mutation is possible. It must be caught in Week 2 and reviewed by a second engineer.

5. No schedule float. The critical path has 10 sequential gates and fills all 5 weeks. Any slip anywhere propagates directly to the customer access date. There is no buffer week.

Recommended Focus Areas
Priority 1 — Secure the XXX.ai commitment. Before any other planning, obtain a written commitment from XXX.ai that WP1-S1 (all 3 endpoints) will be complete by end of Week 1, Day 3. This is the single action that most protects the 5-week target. If this commitment cannot be obtained, the confidence rating drops significantly and the plan should be revised.

Priority 2 — Parallelize Week 2 aggressively. Assign Group A filters (WP3-S1) to one engineer and Groups B, C/D, E/F (WP3-S2 through WP3-S4) to a second engineer. Both start simultaneously on Day 1 of Week 2. This is the only week where parallelism meaningfully compresses the schedule.

Priority 3 — Treat raw SQL line 181 as a formal code review gate. Do not merge WP3-S1 without a second-engineer review of the promote/POST.ts line 181 patch. This is the highest-risk single change in the entire plan.

Priority 4 — Export a snapshot after every migration session. Make this a non-negotiable operational discipline from Week 1 onward. The ephemeral DB is the most operationally fragile part of the environment.

Priority 5 — Begin Week 4 validation on schedule regardless of Week 3 overrun. If Week 3 implementation work is not fully complete by end of Week 3, triage ruthlessly. The Week 4 gate must start on time. Items that are not on the critical path to the 59 validation assertions can slip to Week 5 or beyond.

Assessment complete. No implementation performed.*
