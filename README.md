# Nitin Mahale — Comprehensive Career & Technical Portfolio

---

## 1. Professional Overview & Positioning

* **Current Official Designation:** Senior Developer
* **Organization:** Ambibuzz Technologies LLP (Joined: January 2022 – Present | ~4 years, 8 months)
* **Career Path / Internal Milestones:** Junior Developer / Fresher → Shopify Developer → Frappe / ERPNext Developer → Team Lead (internal team-lead mandate) → Senior Developer
* **Target Roles:** Senior Software Developer, Technical Lead, Senior Integration Engineer, Shopify Plus Technical Lead
* **Work Model:** 100% Remote (India-based or global remote organizations)
* **Core Market Positioning:** **Enterprise Systems & Ecommerce Integration Specialist**. You bridge the gap between enterprise ecommerce platforms (**Shopify Plus B2B/B2C**) and modern ERP/business backends (**Frappe / ERPNext, NetSuite**). Your profile focuses on middleware data pipelines, schema translations, asynchronous queuing, rate-limit resilience, and operational observability rather than frontend-only or theme-only development.

---

## 2. Technical Skill Inventory

### Languages & Frameworks

* **Python:** Backend service development, data transformation, REST/GraphQL clients, scheduled batch jobs, system automation.
* **Frappe Framework (v14/v15):** Custom app development, custom DocTypes, Child Tables, Single DocTypes, NestedSet hierarchical models, Whitelisted Server APIs (`@frappe.whitelist`), hooks (`hooks.py`), background queues (`frappe.enqueue`), real-time pub/sub (`frappe.publish_realtime`), Frappe Query Builder.
* **ERPNext:** Custom business workflows, Sales Orders, Material Requests, custom pricing/discount schemes, distributor management logic.
* **Shopify Liquid & Frontend Scripting:** JavaScript, jQuery, Shopify Liquid customization, Frappe Client Scripts, Jinja templating.

### Ecommerce & API Engineering

* **Shopify Plus:** B2B and B2C architecture, multi-warehouse/location structures.
* **Shopify APIs:** Admin REST API, Admin GraphQL API, Webhook ingestion and HMAC-verified handling.
* **Shopify B2B Domain Constructs:** Companies, Company Locations, Catalogs, Publication Catalogs, Price Lists, Quantity Breaks, and Step Pricing.
* **NetSuite Integration:** SuiteQL query construction, RESTlets, Token-Based Authentication (TBA / OAuth 1.0a HMAC-SHA256).

### Systems Integration & Distributed Architecture

* **Synchronization Patterns:** Bidirectional synchronization, payload schema mapping, hierarchical field translations, diff calculations.
* **Resilience & Fault Tolerance:** Exponential backoff and jitter algorithms for upstream rate limits (HTTP 429), transaction-level deduplication (`transaction_id` tracking), non-blocking asynchronous job dispatching, scheduled cron orchestration.
* **Data Streaming & Queuing:** Google Cloud Pub/Sub, Firebase Realtime Database / Firebase Admin SDK, Frappe worker queues (default, short, long).

### Infrastructure, DevOps & Tooling

* **Cloud & Compute:** Google Cloud Platform (Cloud Functions, Cloud Run, Pub/Sub, IAM Service Accounts).
* **Environment & Containment:** Docker, Linux server navigation, remote virtual machines, Git/GitHub.
* **Advanced Code Intelligence & Graphs:** Neo4j (Graph databases, node/relationship traversal), Tree-sitter (Concrete Syntax Tree / Abstract Syntax Tree code parsing).

---

## 3. Experience Breakdown: What You Built, What You Coordinated & What You Own

### A. What You Personally Engineered & Built (Hands-On Code)

1. **Shopify Webhook Ingestion Pipelines:**
* Engineered asynchronous webhook endpoints (`on_shopify_order_create`) that immediately acknowledge Shopify to prevent timeouts and enqueue background workers via `frappe.enqueue` for order ingestion into ERP systems.


2. **GraphQL Bulk Inventory Synchronization:**
* Built differential inventory comparison logic (`adjust_inventory`) comparing live Shopify warehouse counts against enterprise dumps.
* Implemented Shopify GraphQL bulk inventory adjustment mutations (`adjust_bulk_inventory_graphql`), sending batched updates per warehouse location.


3. **B2B Tiered Pricing & Catalog Synchronization:**
* Programmed synchronization of tiered B2B pricing into Shopify Plus Catalogs and Price Lists.
* Handled volume breaks, minimum/maximum order limits, and incremental step pricing mapped from ERP price levels.


4. **B2B Companies & Locations Data Pipelines:**
* Wrote customer and address reconciliation logic (`sync_netship_addresses_to_shopify_company`, `create_company_location`), linking ERP internal IDs to Shopify Company and Location resources.
* Built specialized prefecture/address parsing and phone-number normalization algorithms for regional customer address data.


5. **Rate-Limit Resilience & File Batching:**
* Implemented exponential backoff decorators/handlers for NetSuite RESTlets and SuiteQL calls encountering HTTP 429 rate limits.
* Handled high-volume data dumps (thousands of items, catalogs, and price tiers) by streaming and staging them into private file structures before processing, avoiding server memory exhaustion.


6. **Custom ERP Sales & Discounting Engines (Sundaram Project):**
* Developed custom Frappe DocTypes, child tables, and Python business logic calculating multi-tier distributor discounts based on territory, customer classification, and item matrices.
* Automated real-time Sales Order recalculations and Material Request generation with live UI feedback using `frappe.publish_realtime`.


7. **Repository AST Ingestion & Graph Intelligence (Knowledge Base Project):**
* Built code parsing pipelines utilizing Tree-sitter to inspect Git repositories, extract functional symbols, and establish structural dependencies in a Neo4j graph database.



### B. What You Coordinated (Architecture & Systems Collaboration)

1. **Middleware Architecture Collaboration (NetShip):**
* Partnered alongside the core architect (Amit, who designed the generic `Adaptor` engine) to integrate the entire Shopify Plus ecosystem.
* Formulated the mapping contracts connecting Shopify REST/GraphQL data models with the middleware’s JSON-driven schema engine.


2. **Cross-System Product Delivery:**
* Collaborated with Product Managers (PMs) on new business requirements, scoping technical feasibility across Shopify API limits, Frappe framework capabilities, and ERP database schemas.
* Coordinated deployment rollouts and infrastructure requirements with dedicated DevOps and infrastructure teams.



### C. What You Managed (Team Leadership & Technical Helpdesk)

1. **Team Leadership (4–6 Engineers):**
* Served as team lead across senior and junior developers.
* Managed sprint task allocation, timeline and effort estimations, daily syncs, and weekly planning sessions.
* Unblocked developers on difficult integration bugs, API quirks, and architectural issues.
* Conducted code reviews, established coding patterns, interviewed technical candidates, and onboarded junior developers to live codebases.


2. **Technical Helpdesk & Incident Ownership:**
* Triaged production support tickets into structured categories: Queries, Definite Bugs, and Feature Enhancements.
* Took ownership of production bug resolution, managing root-cause analysis on dropped sync jobs, failed orders, or payload mismatches.
* Built operational Frappe UI dashboards, manual retry buttons, and health checks to empower support staff to re-trigger failed warehouse or order syncs without database intervention.



---

## 4. In-Depth Project Case Studies

### Flagship 1: NetShip — Enterprise Shopify Plus & ERP Integration Middleware

* **Domain:** Multi-Platform Enterprise Integration & B2B/B2C Ecommerce.
* **Stack:** Python, Frappe Framework, Shopify Plus (REST & GraphQL), NetSuite (SuiteQL, RESTlets, TBA), Google Pub/Sub.
* **Architectural Flow:**
```text
Shopify Plus (B2B/B2C)
      ↕ [Webhooks / GraphQL / REST Admin API]
NetShip Middleware (Custom Frappe Engine + Adaptors)
      ↕ [SuiteQL / RESTlets / TBA (OAuth 1.0a)]
NetSuite / Enterprise ERP

```


* **Key Modules & Ownership:**
* **Orders & Fulfillment:** Webhook-driven order ingestion into Frappe, asynchronous translation to NetSuite Sales Orders, and reverse status synchronization of fulfillment tracking numbers and carrier details back to Shopify.
* **B2B Entities:** Automated syncing of corporate customer hierarchies, creating Shopify Companies, assigning Company Locations, and routing location-specific orders.
* **Inventory Matrix:** Multi-location inventory reconciliation using SuiteQL dumps and batched GraphQL adjustments, complete with per-warehouse manual retry endpoints (`retry_inventory_sync`).
* **Pricing & Catalogs:** Syncing dynamic price levels to Shopify Catalogs with multi-tiered volume breaks.
* **Data Resilience:** Enforced unique `transaction_id` constraints across all adaptor logs to prevent double-processing of payloads. Implemented a 15-day automated hard-delete data retention policy to maintain MariaDB performance.



---

### Flagship 2: Sundaram Discounting — ERPNext Automated Sales & Pricing Engine

* **Domain:** Wholesale Distribution & Manufacturing Supply Chain.
* **Stack:** Python, Frappe Framework, ERPNext, MariaDB, Client Scripts.
* **Functionality & Architecture:**
* Automated complex commercial distributor discounting logic across wholesale sales orders.
* Replaced manual, error-prone calculations with rule engines evaluating customer class, geographical territory, and order line items.
* Leveraged `frappe.enqueue` for asynchronous calculation of large multi-line-item orders, maintaining UI responsiveness via `frappe.publish_realtime` websockets.
* Handled downstream generation of Material Requests, stock reserve validations, and carton/quantity conversions.



---

### Flagship 3: Code Intelligence & Knowledge Graph Platform

* **Domain:** Developer Productivity, AI Tooling & AST Code Search.
* **Stack:** Python, Frappe v15, Neo4j, Tree-sitter, GitHub Webhooks, LLM Orchestration.
* **Functionality & Architecture:**
* Ingestion engine that clones and monitors Git repositories via GitHub push webhooks.
* Leverages Tree-sitter parsers to analyze source files, producing Concrete Syntax Trees (CST) and Abstract Syntax Trees (AST).
* Extracts code symbols (classes, methods, variables, imports, calls) and persists relationships inside a Neo4j Graph database.
* Exposes graph-traversal APIs that serve as context retrieval backends for an AI agent, enabling code explanation, impact analysis, and automated system documentation.



---

## 5. Education & Early Career Background

* **Early Trainee Experience (March 2016 – September 2017):**
* **Organization:** Deepak Fertilisers & Petrochemicals Corporation Ltd.
* **Role:** Trainee Engineer
* *Context:* Early career foundation in industrial operations and precision workflows before transitioning into full-time software engineering and systems architecture.


* **Formal Education:**
* **Credential:** Diploma in Petrochemical Engineering
* **Completion Year:** 2016
