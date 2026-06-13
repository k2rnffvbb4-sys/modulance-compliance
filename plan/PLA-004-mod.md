
org-scoped. V-ADMIN-1: Member-role Org B token returns 403 on all admin routes. V-ADMIN-2: Admin-role Org B token on diag-annotations returns only Org B annotations. V-ADMIN-3: Admin-role Org B token on diag-canonical returns only Org B data. V-ADMIN-4: Admin-role Org B token on export-snapshot returns only Org B data. V-ADMIN-5: seed-products returns 403 for Org B admin. V-ADMIN-6: reset-ka-full with Org B admin JWT deletes only Org B rows. | | Deliverable | V-ADMIN-1 through V-ADMIN-6 results. Pass/fail for each. | | Estimated Effort | 0.5 pd | | Required Capability | Modulance QA | | Dependencies | WP5 complete, WP1-S2-T3 (Org B member JWT and admin JWT) | | Verification Criteria | All 6 tests pass. Exit criterion EC-6 satisfied. |

WP6-S3-T7
Field	Value
Task ID	WP6-S3-T7
Task Title	Run V-SNAP-1 through V-SNAP-5 — snapshot isolation tests
Description	5 tests confirming snapshot operations are org-isolated. V-SNAP-1: Org A snapshot export contains only Org A rows. V-SNAP-2: Org B snapshot export contains only Org B rows. V-SNAP-3: Importing Org A snapshot with Org B JWT returns error. V-SNAP-4: Importing Org A snapshot with Org A JWT succeeds and all rows have Org A ID. V-SNAP-5: Snapshot import does not overwrite other org's data.
Deliverable	V-SNAP-1 through V-SNAP-5 results. Pass/fail for each.
Estimated Effort	0.5 pd
Required Capability	Modulance QA
Dependencies	WP5-S3 complete, WP1-S2-T3
Verification Criteria	All 5 tests pass. Exit criterion EC-7 satisfied.
WP6-S3-T8
Field	Value
Task ID	WP6-S3-T8
Task Title	Run V-FLOW-1 through V-FLOW-12 — customer-like end-to-end flow as Org B
Description	12 tests executing a complete customer-like workflow as Org B to confirm the full platform is usable and isolated. V-FLOW-1: Org B creates a project. V-FLOW-2: Org B uploads a PDF. V-FLOW-3: Org B triggers GPT extraction. V-FLOW-4: Org B views extracted annotations. V-FLOW-5: Org B promotes an annotation. V-FLOW-6: Org B creates a canonical KO. V-FLOW-7: Org B views KPIs. V-FLOW-8: Org B exports a snapshot. V-FLOW-9: Org B imports the snapshot. V-FLOW-10: Org B views platform snapshot. V-FLOW-11: Org A data is unaffected throughout all Org B operations. V-FLOW-12:# Modulance Quality — 5-Week Customer Validation Delivery Org B data is not visible to Org A.
Plan	
Audience: Modulance Engineering · Modulance QA · Modul Deliverable | V-FLOW-1 through V-FLOW-12 results. Pass/fail for each. | |ance Operations Goal: Successful customer validation within five weeks Estimated Effort | 1 pd | | Required Capability | Modulance QA | | Dependencies | Source: 5-Week Customer Validation Readiness Assessment (no WP6-S3-T2, WP6 new work added, no work-S3-T3, WP6-S3-T4, WP6-S3-T removed)

Work Package Index
|5, WP6-S3-T6, WP6-S3-T7 all ID | Work Package | Program | Weeks pass | | Verification Criteria | All 12 tests pass. Exit criterion EC-8 | |---|---|---|---| | W satisfied. |

WP6-S3-T9
Field	Value
Task ID	WP6-S3-T9
Task Title	P-1
WP group	
Description	For each exit criterion that fails (-2
WP-3	Organization Isolation — Query Layer
WP-4	AI Configuration Isolation is conditional — it exec
WP-5	Admin & Security Hardutes only if failures are found.
Deliverable	Code fix for each failing criterion. Re-run results showingening
WP-6	Isolation all 8 exit criteria pass.
Estimated Effort Validation	Modulance CVR
WP-7	Customer Onboarding
Required Capability	Modulance Backend Engineering +
WP-1 — QA |
| Dependencies | WP6-S3-T2 Identity & Access

Objective: Deliver the minimumthrough WP6-S3-T8 | | Verification Criteria | All 8 exit criteria pass XXX.ai identity infrastructure required for. Written sign-off produced. WP1-S3 Modulance to validate RS256 and WP-7 are un JWTs, resolve perblocked. |

WP-7 — Customer-org AI configuration, Onboarding
Objective: Provision the and provision internal and customer real customer organization, organizations.

Expected Outcome: All three XX verify their JWT andX.ai minimum endpoints are live and accessible AI config, wire audit events from the Modulance development environment. Internal, and grant customer access.

Expected Outcome: Real Org A and Test Org B exist customer can authenticate, create with valid JWTs and AI configs. Real a project, and use the platform. customer org is provisioned after Customer validation begins.

Gate the Week 4 gate condition: WP6-S3-T9 (all 8 exit criteria pass) must be complete before any task in this work passes.

Critical Path: Yes package begins.

WP7 — all downstream Modulance work-S1 — Customer Org Provisioning
Objective: Create depends on WP1-S the real customer org in xxx.ai and confirm1.

WP1-S1 — XXX.ai Minimum their identity artifacts are Endpoints
Objective: Build and deploy the three minimum correct.

Expected Outcome: Customer has endpoints required for JWT-based org a valid JWT and an identity and AI config resolution.

Expected Outcome: ` AI config using their own API key.

WP7-S1-T1
Field	ValuePOST /auth/login`,
Task ID	WP7-S1-T1
Task Title	Create real GET /.well-known/jw customer org + admin user +ks.json, and GET /api/orgs/:organizationId/ai-config membership in xxx.ai
Description are deployed to a URL	Execute WP1-S3 accessible by the Modulance development environment.
Depends-T1 through WP1-S3-T3 (XXX.ai operations tasks On: Nothing Blocks: W). Confirm customer orgP2-S1 (integration testing), WP4 record, admin user, and membership exist.-S1, WP3-S6

Confirm customer AI config is set with T-1.1. the customer's own API key.1
| Field | Value | | Confirm customer JWT is issued. | | Deliverable |---|---| | Task ID | T-1.1.1 | | Task Customer org provisioned Title | Implement POST. Customer JWT issued. Customer organizationId UUID /auth/login | | Description | Build the recorded. | | Estimated Effort | 0.25 pd | login endpoint on the XXX.ai platform | Required Capability | XXX.ai Operations | | Dependencies | W. Must issue anP6-S3-T9 (all 8 exit criteria pass) RS256-signed JWT containing all | | Verification Criteria | POST /auth 7 required claims/login with customer credentials: sub, organizationId, role returns valid JWT. JWT contains correct, email, name, iat, exp. Token must be verifiable using organizationId and role: 'admin'. |

WP7-S1-T2
| Field the JWKS public key endpoint. |

**Deliverable	Value
Task ID	WP7-S1-T2
Task Title	**
Description	Execute WP1-S3-T2.
Estimated Effort	1 pd Confirm `GET /api/orgs/
Required Capability	XXX.ai Backend Engineering<CustomerOrgId>/ai-config` returns the
Dependencies	None
Verification Criteria	POST with customer's own API key. Confirm the key valid credentials returns HTTP 200 and a JWT is not the internal Modulance key.
Deliverable	Customer AI config set. resolveAiConfig(customerOrgId) returns customer's own key all 7 claims; JWT signature verifies against the JWKS public key
T-1.1.2
Field	Value
**Task.	
Estimated Effort	0.1 pd
Required Capability	XXX.ai Operations ID**
Task Title	Implement `GET
Dependencies	WP7-S1-T1
Description	Build the JWKS endpoint on the XX
Verification Criteria	GET /api/orgs/<CustomerOrgId>/ai-config returnsX.ai platform. Must return the RS256 public key in HTTP 200 with customer's own apiKey.
standard JWKS format. This endpoint is used WP7-S2 — Customer JWT Verification by Modulance's `j
Objective: Confirm the customer JWT is accepted bywtAuthMiddlewareto validate incoming JWTs. | | ** Modulance and all 6 TDeliverable** |GET /.well-known/jwks.json` endpoint live; returns valid JWKS JSON-JWT tests pass with real customer credentials containing the RS256 public key | | Estimated Effort |.

Expected Outcome: Customer JWT is accepted. Customer can make authenticated 0.5 pd | | Required Capability | XXX.ai Backend Engineering | | **Dependencies API requests.

WP7-S2-T1
|** | None — parallel with T Field | Value | |---|---| | Task ID | WP7-S2-T1-1.1.1 | | Verification Criteria | GET returns HTTP 200 with | | **Task Title** | Run T-JWT-1 through T-JWT-6Content-Type: application/json; response with real customer JWT | | Description | Using contains keys array with at least one entry; key the customer JWT issued in WP7-S1-T1, re kty is RSA;-run the 6 JWT verification tests against Modulance jwtAuthMiddleware can fetch the live Modulance environment. Confirm: T and cache the key |

T-1-JWT-1: customer JWT passes middleware.1.3
Field	Value
Task ID	T-1.1.3
. T-JWT-2: expired customer JWT returns Task Title	Implement GET /api/orgs/:organizationId/ai-config
Description	Build the org AI config endpoint on the XXX.ai platform all 7 claims. T-JWT-5. Must return the AI provider configuration for the specified organization. Used: customer organizationId claim is correct. T-JWT-6: customer role claim is admin.
Deliverable	T by Modulance's resolveAiConfig function. Must-JWT-1 through T-JWT-6 results using real customer JWT. All require a valid service token 6 pass.
Estimated Effort	0.5 pd
**Required for authentication.	
Deliverable	GET /api/orgs/:organizationId/ai-config endpoint live; returns Capability**
Dependencies	WP7-S1-T1, org-specific AI provider config WP1-S3-T3
Verification Criteria	All 6 T
Estimated Effort	1 pd
Required Capability	XXX.ai Backend-JWT tests pass with real customer JWT.
WP7-S3 Engineering |
| Dependencies | None — parallel with T-1.1. — Audit Events

Objective: Wire1 and T-1.1.2 | | Verification Criteria | GET with 5 audit event types valid service token and existing org ID so customer actions are trac returns HTTP 200 with AI config payload; GETeable.

Expected Outcome: Customer actions produce audit log with unknown org ID returns HTTP 404; GET without service token returns HTTP 401 | entries attributed to the customer org.

WP7
T-1.1.4
Field	Value
Task ID	T-1.1-S3-T1
Field	Value
Task ID	WP7-S3-T1
Task Title	Wire 5 audit event types to audit.4
Task Title	Deploy all log
Description	Implement audit3 endpoints to Modulance-accessible URL
Description	Deploy the three implemented event emission for the 5 key endpoints to an environment whose customer actions: ( URL is accessible from the Modulance development and CI environment.1) project created, (2) PDF uploaded, (3) GPT extraction Provide the base URL to triggered, (4) annotation promoted, (5) snapshot exported. Each event the Modulance team.
Deliverable	All must include organizationId,3 endpoints reachable from Modulance dev environment; userId, eventType, `resourceId base URL communicated to Modulance team
Estimated Effort	0 pd ( be written to the `auditEventsops task)
Required Capability	XXX.ai Dev` table (already org-scoped fromOps
Dependencies	T-1.1.1, T-1.1.2, T WP2-S2-1.1.3
Verification Criteria	Modulance engineer).
Deliverable	5 audit event types em can reach all 3 endpoints from dev machine; noitted and stored in auditEvents table with firewall or CORS block correct organization_id.
Estimated Effort	1 on required routes
pd |
| Required Capability | Modulance Backend Engineering | | Dependencies | WP2 WP1-S2 — Org Provisioning —-S1-T3 Internal

Objective: Create Internal Org A and Test Org B(identity context for event in the xxx.ai system attribution) | | Verification Criteria | Each with valid users, memberships, and AI provider of the 5 customer actions produces an audit event row in auditEvents with correct organization_id, userId, and configurations.

Expected Outcome: Both orgs have valid JWTs. Both AI eventType. |

WP7-S3-T2
Field	Value
Task ID	WP7-S3-T2
Task Title	Verify configs exist. Modulance JWT middleware snapshot and recovery with accepts both tokens. customer org present
Depends On: T-1.1.4 (endpoints deployed | | Description | With the customer org provisioned and); T-2.1.5 ( at least one project created, exportModulance JWT middleware live — required a snapshot as the customer. for verification step T-1.2 Import the snapshot as the customer. Confirm all.5) Blocks: T-2.3 customer data is restored correctly.1 (Org A ID required with correct organization_id. Confirm for backfill value); Org A and Org B data are unaffected by WP6-S3 (both the customer snapshot import. | | **Deliverable org JWTs required)

T-1** | Customer snapshot export and import verified.2.1
Field	Value
Task ID	T-1.2.1. Cross-org data unaffected.
Estimated Effort	0.
Task Title	Create Internal Org A record + admin5 pd
Required Capability	Modulance QA
Dependencies	WP7-S1 user + membership
Description	Create the-T1, WP5-S3-T2
Verification Internal Org A organization record in the xxx.ai ` Criteria	Customer snapshot import restores all customer rowsorganizations` table. Create an admin user record. Org A and Org B row counts are. Create the membership record linking unchanged after customer snapshot import.
WP7-S4 the user to the org with ` — Customer Access Grant
Objective: Deliverrole: admin`. | | Deliverable | Internal Org A exists credentials to the customer and verify their in xxx.ai with admin first project creation.

Expected Outcome: Customer validation begins. Customer can create user and membership; Org A ID value known a project and use the platform end-to-end.

WP7-S4-T1
| Field | Value | and communicated to Modulance team |

Estimated Effort	0
Task ID	WP7-S4-T1
.25 pd	
Required Capability	XXX.ai Operations
Dependencies	T Task Title
Description	-1.1.4
Verification Criteria	POST /auth/login with Deliver the customer's login credentials and platform Org A admin credentials returns a URL. Observe or confirm JWT containing organizationId the customer's first authenticated login. Confirm the customer can create a project. Confirm the created project has matching Org A's ID androle: adminorganization_id = customer org UUID
T-1.2.2
Field	Value
Task ID	T-1.2.2
Task Title	Configure Internal Org A AI provider config
Description	Set the AI provider configuration for Internal Org A to the customer. Customer validation begins at this point.
** via `GET /api/orgs/:organizationDeliverable**	Customer logged in. First project created. Id/ai-config. Config must include provider type andorganization_id` on project = customer org UUID. No cross API key.
Deliverable	`GET /api/orgs/{-org data visible.
Estimated Effort	0.5 pd
Required Capability	Modulance Operations + QA
DependenciesOrgAId}/ai-config` returns a	WP7-S1-T1, WP7-S2-T1, WP7 valid AI config payload
Estimated Effort	0.1 pd
Required Capability	XXX.ai Operations
Dependencies	T-1.2-S3-T2
Verification Criteria	Customer can log.1
Verification Criteria	Endpoint returns HTTP 200 with non in with their credentials. Customer can create a project. Project row has correct-empty AI config for Org A ID
T-1. organization_id. Customer cannot see Org A or Org B2.3
Field	Value
Task ID	T-1.2.3
** projects.	
##Task Title** | Create Test Org B record + admin user + Dependency Summary

membership |
| Description | Create the Test Org B organization record in xxx.ai. Critical Path (sequential gates Create an admin user. Create the membership record with role: admin. Also create a second — no parallelism user with role: member for admin route possible)

WP1-S1-T4 guard testing. | | **Deliverable** | Test Org B exists in xxx.ai with admin user, member user, and memb (endpoints deployed) erships; Org B ID communicated to Modulance team | | **Estimated Effort** | 0.25 pd |→ WP2-S1-T4 (JWT | **Required Capability** | XXX.ai Operations | | **Dependencies** | T-1.1 middleware registered) → WP2-S3.4 | | **Verification Criteria** | `POST /auth/login` with Org B admin credentials returns JWT-T1 (backfill script — with `organizationId` matching Org B ID and `role: admin` requires Org A ID from; login with Org B member credentials returns JWT with `role: member` | --- #### WP1-S2-T1) → WP2-S3-T4 T-1.2.4 | Field | Value | |---|---| | **Task ID** | (snapshot week1-post T-1.2.4 | | **Task Title** | Configure Test Org B AI provider config | | **Description** | Set-backfill) → WP3-S1 the AI provider configuration for Test Org B. Config must be distinct-T5 + WP3-S1-T6 (line from Org A's config so that AI config le 181 patch + review) → WP3-S6akage can be detected-T1 → WP3-S6-T2 (singleton in Week 4 V replacement) → WP4-S1-T1 →-AI tests. | | **Deliverable WP4-S1-T2 → WP4-S1-T3 →** | `GET /api/orgs/{OrgBId}/ai-config` returns a valid AI config payload distinct from Org A's config | | **Estimated Effort** | 0.1 pd | WP4-S1-T4 → WP4-S2-T3 → WP4-S2-T4 → WP4-S2-T5 | **Required Capability** | XXX.ai Operations | | **Dependencies** | T-1.2.3 | | **Verification Criteria** | Endpoint returns → WP6-S1-T3 (STOP criteria HTTP 200 with non-empty AI config for Org B ID; config value differs from Org A config value S-10 through | --- #### T-1.2.5 | Field | Value | |---|---| | **Task ID** | T-1 S-14) → WP5-S3-T3 (week.2.5 | | **Task Title** | Verify both org4-baseline snapshot) → WP6-S3-T1 (baseline JWTs accepted by Modulance JWT middleware | | **Description** | Using restore) → WP6-S3-T2 through WP6-S3-T the live Modulance JWT middleware (T-28 (59 assertions) → WP6-S3-T9 (.1.5 must be completeremediation if needed), verify that JWTs issued by xxx.ai for both) → WP1-S3-T1 (customer Org A and Org B are accepted and correctly parsed org — gate opens) → WP7-S4-T1 (customer access grant) ```. This is a bidirectional verification step ### Parallel Execution Opportunities — both programs must be ready | Parallel Group | Tasks | Can simultaneously. | | **Deliverable** | Confirmation Start | |---|---|---| | Group 1 | WP2 that Org A JWT and Org B JWT are both accepted by Modulance `-S1 + WP2-S2 | WeekjwtAuthMiddleware`; `getIdent 1, Day 1 (ity(res)` returns correctno dependency between them `organizationId` and `role` for each) | | Group 2 | WP3-S1 + WP3-S2 + | | **Estimated Effort** | 0.25 pd | | **Required Capability** | WP3-S3 + WP3-S4 + WP3-S5 | After XXX.ai Operations + Modulance Backend Engineering | | **Dependencies** | T-1.2.1 WP2-S1-T4 + WP2-S3-T4, T-1.2.3, T-2.1.5 ( | | Group 3 | WP5-S1 + WP5-S2cross-program: Modulance JWT middleware must be live) | + WP5-S3 | After WP2-S1-T4 + | **Verification Criteria** | Authenticated request with WP2-S3-T4 (parallel with Org A JWT → `getIdentity(res).organizationId` all of WP- equals Org A ID; authenticated request with Org B JWT → `3 and WP-4) | |getIdentity(res).organizationId` equals Org B ID; both return Group 4 | WP7-S3-T1 ( HTTP 200 on a protectedaudit events) | After WP2-S1-T3 ( route | --- ### WP1-S3 — Org Provisioning — Customerdoes not need Week 4 **Objective:** Create the real customer organization, gate) | ### user, and AI config in xxx Cross-Program Dependencies (XX.ai after the Week 4 gate passes. **Expected Outcome:** Customer canX.ai → Modulance) | Task ID | XX authenticate via xxx.ai and receiveX.ai Deliverable | Blocks Modulance Task a valid JWT accepted by Modulance. ` | |---|---|---| | WP1-S1-T4 | All 3resolveAiConfig(customerOrgId) endpoints deployed | WP2-S1-T1 (` returns the customer's own AI keyintegration testing) | | WP1-S1. **Depends On:** T-6.3.8-T2 | JWKS URL (all 8 Week 4 exit criteria pass — governing live | WP2-S1-T1 (JWKS validation) | | WP1-S1-T3 | ai-config endpoint live gate condition) **Blocks:** WP7-S1, WP7-S2 --- #### T-1.3 | WP4-S1-T1 (resolveAiConfig) | |.1 | Field | Value | |---|---| | **Task ID** | T-1.3.1 | | **Task WP1-S2-T1 | Org A UUID known Title** | Create real customer org record | WP2-S3-T1 (backfill value + admin user + membership | | **Description** | Create the real customer organization record in xxx.ai. Create the) | | WP1-S2-T3 | Org B JWT + customer's admin user with their member JWT | WP5-S1-T2 actual email address. Create the membership record with `role: admin`. This, WP6-S3 all task must not begin V-tests | | WP1-S2-T4 | Org until T-6.3.8 confirms all 8 exit criteria pass. | B AI config exists | **Deliverable** | Real customer org exists in xxx.ai with admin user and | WP4-S1-T2, WP6-S3-T4 membership | | **Estimated Effort** | 0.25 pd | | | WP1-S3-T1 | Customer org | **Required Capability** | XXX.ai Operations | | **Dependencies** | T-6.3.8 ( created | WP7-S1-T1 | | WP1-S3cross-program gate: all 8 Week-T3 | Customer JWT issued | WP7-S2 4 exit criteria must pass before this task begins-T1 | ### Cross-Program) | | **Verification Criteria** | `POST /auth/login` with customer credentials Dependencies (Modulance → XXX.ai) | Task ID | Modulance Deliverable | returns HTTP 200 and a valid JWT containing Blocks XXX.ai Task | |---|---|---| | WP2-S1-T4 customer `organizationId` and `role: admin` | JWT middleware live | WP1-S2 | --- #### T-1.3.2 | Field | Value | |---|---| |-T5 (joint verification) | | WP6 **Task ID** | T-1.3.2 | | **Task Title** | Configure customer AI-S3-T9 | All 8 exit provider config with customer's own criteria pass | WP1-S3-T1 (customer key | | **Description** | Set the AI provider configuration for the real customer org org provisioning — governing using the customer's own API key. Must not use the internal gate) | Org A key or any shared key. | | **Deliverable** | `GET /api/orgs/{customerOrgId}/ai-config` returns the customer's own AI provider config | | **Estimated Effort** | 0.1 pd | | **Required Capability** | XXX.ai Operations | | **Dependencies** | T-1.3.1 | | **Verification Criteria** | Endpoint returns HTTP 200 with customer AI config; config key value is the customer's own key, not the internal org key | --- #### T-1.3.3 | Field | Value | |---|---| | **Task ID** | T-1.3.3 | | **Task Title** | Issue customer admin's
Completed
