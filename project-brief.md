# Project Brief: COBOL AI Assistant Test Harness

**Document Version:** 1.0
**Date:** 2026-01-07
**Project Lead:** Kamal Singh
**Status:** Initial Draft

---

## Executive Summary

XYZ Bank has been running legacy mainframe applications for over 30 years with minimal modernization. The effort required to update these systems has always been prohibitive—until now. Recent advancements in AI technologies present a real opportunity to modernize with significantly lower effort and cost.

However, there's a critical limitation: testing AI agents on production code isn't feasible. Infrastructure logistics create barriers—deploying AI tools in our mainframe environment requires extensive approvals, not all AI features are available in on-premise setups, and security policies prohibit sending proprietary code to external sandboxes or cloud-based testing environments. We can't objectively evaluate AI assistants before committing to them.

The solution is ABC123—a purpose-built dummy COBOL application that mirrors the complexity, structure, and messiness of our real-world banking systems without containing any actual business logic or proprietary code from XYZ Bank. It's intentionally designed to be difficult: 40 modules with authentic legacy anti-patterns, GOTO spaghetti, nested logic, inconsistent error handling, and all the technical debt accumulated over decades. ABC123 covers cash account management—deposits, withdrawals, interest calculations, end-of-day processing—using VSAM files, DB2 tables, JCL batch jobs, and copybooks exactly as they exist in production environments.

Because ABC123 contains no real bank code or business logic, it's safe to send to external AI testing platforms, cloud-based sandboxes, and vendor evaluation environments. This lets us rigorously test various AI assistants—such as IBM watsonx Code Assistant for Z (WCA4Z), GitLab Duo, GitHub Copilot, and others—evaluating their ability to understand legacy code, extract business logic, identify modernization opportunities, suggest refactoring strategies, and validate changes, all before making any investment or deployment decisions.

**Deliverable:** ABC123 COBOL application (~40 modules, 400K-500K LOC) with complete mainframe infrastructure, designed for secure external AI assistant evaluation.

---

## Problem Statement

**The Evaluation Dilemma**

AI assistants promise to revolutionize mainframe modernization, but evaluating them at XYZ Bank is caught in an impossible catch-22. Security policies strictly prohibit sending production code outside the bank's infrastructure—our COBOL applications contain proprietary business logic, customer data structures, and competitive banking algorithms that cannot be shared with external AI platforms, cloud-based testing environments, or vendor sandboxes.

**The Deployment Bottleneck**

The alternative—deploying AI assistants on-premise for evaluation—presents its own challenge. Installing and configuring enterprise AI tools on mainframe infrastructure is a months-long process involving security reviews, infrastructure provisioning, network configuration, and compliance approvals. By the time an AI assistant is deployed for pilot testing, the technology landscape has often shifted, and the opportunity cost of delayed modernization mounts.

**The Testing Gap**

This creates a critical gap: we need AI assistants that can understand complex, decades-old COBOL codebases with poor documentation, extract business logic from spaghetti code, identify modernization opportunities, suggest refactoring strategies, and navigate cross-module dependencies—but we have no practical way to evaluate whether tools like WCA4Z, GitLab Duo, or GitHub Copilot can actually deliver on these promises before committing significant time and budget.

**The Transformation Risk**

Beyond evaluation, we need to validate that AI assistants can actually help transform legacy applications to modern architectures—not just understand them. Can they guide migrations from batch COBOL to newr cobol? Can they assist in refactoring monolithic modules into event-driven components? Testing these transformation capabilities on production applications is impossible within a reasonable timeframe—the risks are too high. A failed experiment on a live banking system could impact customers, create data integrity issues, or violate compliance requirements. ABC123 eliminates this risk by providing a safe sandbox for testing architectural transformations without jeopardizing production systems.

**What's Missing**

- A realistic COBOL test application with authentic legacy complexity that contains no proprietary code
- Objective benchmarks for comparing AI assistant capabilities across multiple dimensions (code comprehension, documentation extraction, refactoring suggestions, testing support)
- Representative mainframe structures (VSAM, DB2, JCL, copybooks) that mirror production environments
- A safe, shareable codebase that can be sent to external platforms for rapid pilot evaluation

**The Cost of Inaction**

Without a proper test harness, we cannot objectively evaluate AI capabilities before adoption, compare different tools to find the best fit, identify specific strengths and weaknesses, or make informed investment decisions. We're forced to choose between slow on-premise pilots or blind vendor commitments—neither is acceptable for a modernization effort of this scale.

---


## Project Goals

**Break the Evaluation Deadlock**

ABC123's primary goal is simple: enable rapid, secure evaluation of AI assistants without waiting months for on-premise deployment or violating security policies. Within weeks, we can test WCA4Z, GitLab Duo, GitHub Copilot, and other tools on realistic COBOL complexity—sending ABC123 to vendor sandboxes, cloud platforms, or evaluation environments with zero security risk.

**Test What Matters**

ABC123 focuses on five critical capabilities that determine whether an AI assistant can actually help with modernization:

1. **End-to-End Application Understanding** - Can it trace a transaction flow through 10+ modules and explain what happens?
2. **Business Logic Extraction** - Can it document interest calculation rules buried in 30,000 lines of procedural code?
3. **Improvement Identification** - Can it spot duplicate logic, dead code, and modernization opportunities?
4. **Refactoring Guidance** - Can it suggest how to break a monolithic module into maintainable components?
5. **Testing Support** - Can it generate test scenarios and identify edge cases?

**Drive Informed Decisions**

The outcome is objective comparison data. When we ask three AI assistants to explain TXNROUTE's logic and get three different answers, we'll know which tool actually understands COBOL. When we test documentation extraction and one tool produces accurate business rules while another hallucinates, we'll know which to trust. ABC123 turns subjective vendor demos into measurable, comparable results that justify investment decisions.

**Success Metrics**

ABC123 succeeds when it:
- **Mirrors production complexity**: 40 modules (400K-500K LOC) with authentic legacy anti-patterns, DB2/JCL infrastructure, and cross-module dependencies
- **Contains zero proprietary code**: Safe to send anywhere without security approval delays
- **Differentiates AI capabilities**: Produces measurably different results across tools, revealing strengths and weaknesses
- **Enables rapid pilots**: Completes AI evaluations in weeks instead of months
- **Supports data-driven decisions**: Provides objective evidence for tool selection and budget justification

---

## Scope

### In Scope

**ABC123 Business Domain: Cash Account Management System**

ABC123 simulates a complete cash account management system for a banking institution, covering the full lifecycle of customer checking and savings accounts. The application handles everything from opening new accounts to processing daily transactions, calculating interest and fees, generating statements, and maintaining regulatory compliance—all the business functions found in real-world banking systems.

**Business Functions:**

**1. Daily Transaction Processing (12 modules)**
The heart of ABC123—processes all daily banking transactions including customer deposits, cash withdrawals, and account-to-account transfers. This function validates transaction formats, applies business rules (overdraft limits, hold policies, duplicate detection), routes transactions to specialized processors, posts updates to account master files, creates audit trails, and reconciles control totals. Simulates the nightly batch processing that updates millions of customer accounts with the day's activity.

**2. Interest & Fee Calculation (11 modules)**
Handles the financial calculations that generate bank revenue and customer benefits. Monthly interest accrual for savings accounts (simple and compound interest), tiered rate structures based on balance levels, promotional interest campaigns, maintenance fee assessments, overdraft fee calculations, and transaction-based charges. Includes complex fee waiver logic based on relationship balances and account status. Simulates month-end processing that determines bank profitability and customer account performance.

**3. End-of-Day Processing (10 modules)**
Critical reconciliation and reporting workflows that close the business day. Updates all account balances from the day's transactions, performs master file reconciliation against control totals, generates monthly customer statements, identifies dormant and inactive accounts, produces regulatory ledgers and position reports, archives transaction history to generation data groups (GDG), and prepares the system for the next business day. Includes checkpoint/restart logic for recovery from failures.

**4. Account Maintenance (7 modules)**
Manages the customer account lifecycle from creation to closure. New account opening with customer validation and initial deposit processing, account information updates (address changes, beneficiary modifications, contact details), account status changes (freeze, suspend, reactivate), account closure with balance settlement, and account type conversions. Includes the business logic that enforces banking regulations and customer relationship rules.

**Technical Architecture & Components**

ABC123 replicates a complete mainframe technology stack exactly as it exists in production banking environments. The application uses **40 COBOL modules** totaling 400,000-500,000 lines of code, with module sizes ranging from 5,000 to 30,000 lines—three massive orchestrator modules (TXNROUTE, INTMAST, EODMAIN) each exceeding 28,000 lines. The code intentionally mixes **COBOL-74 and COBOL-85 standards**, simulating decades of development by different teams with varying coding conventions.

**Key Technical Components:**

- **Batch Orchestration**: 4 JCL job streams coordinate execution—DAILYTRX.JCL for transaction processing, MONTHINT.JCL for interest/fee calculations, EODPROC.JCL for end-of-day workflows, and ACCTMNT.JCL for account maintenance. JCL kept deliberately simple (straightforward sequential execution) so complexity remains in the COBOL where AI assistants need to focus.

- **Data Persistence**: VSAM files (KSDS for account master, ESDS for transaction input, RRDS for audit records), sequential files for batch processing, and Generation Data Groups (GDG) for transaction archival and backups. Complex copybooks with REDEFINES structures, COMP-3 packed decimals for financial amounts, nested group levels, and inconsistently-used level 88 condition names.

- **Database Integration**: DB2 tables for account data, transaction history, interest rate tables, fee schedules, and audit logs. Embedded SQL (EXEC SQL...END-EXEC blocks) scattered throughout modules with inconsistent SQLCODE checking, cursor processing for large result sets, and business logic occasionally buried in SQL statements—authentic to legacy mainframe patterns.

- **Cross-Module Architecture**: Deep call chains (4-5 levels), mixed parameter passing (BY REFERENCE and BY CONTENT), shared utility modules via middleware layer, common copybooks for working storage, and intentional circular dependencies that create the tangled webs found in real legacy systems.

- **Middleware Utilities**: Standard library modules for error handling (ERRHAND), database access wrappers (DBUTIL), file I/O operations (FILEIO), logging and audit trails (LOGGER), date/time calculations (DATEUTIL), and common validation routines (VALIDAT). These represent the reusable components typical of mainframe development shops.

**Common Middleware Libraries**

ABC123 incorporates the most common middleware libraries and utility patterns found across mainframe banking environments. Rather than inventing custom approaches, the application uses industry-standard middleware components that COBOL developers recognize immediately—the same error handling frameworks, database access layers, and logging utilities they encounter in production systems every day.

These libraries include:
-


By using these familiar middleware patterns, ABC123 tests whether AI assistants can navigate the layered architecture typical of enterprise mainframe applications—understanding not just the business logic modules but also how they interact with shared utility layers. This mirrors real-world scenarios where developers must trace logic through multiple abstraction layers to understand what a program actually does.

### Intentional Complexity & Anti-Patterns

ABC123's value lies in its authentic messiness. The application deliberately includes the anti-patterns, technical debt, and legacy characteristics that make real mainframe modernization challenging. This isn't clean, well-structured code—it's the kind that makes developers wince when they encounter it.

**Code Quality Issues (By Design):**

- **Control Flow Chaos**: GOTO statements creating spaghetti logic jumps, PERFORM...THRU abuse spanning hundreds of lines, deeply nested IF statements (8-12 levels), fallthrough logic bugs from missing ELSE clauses, and paragraph-level logic that should be broken into smaller procedures.

- **Copy-Paste Engineering**: Duplicate calculation logic across modules (INTCALC1 vs INTCALC2), repeated validation code in multiple programs, inconsistent error handling patterns copied with slight variations, and maintenance nightmares when one copy gets updated but not others.

- **Hard-Coded Nightmares**: Magic numbers throughout the code (interest rates like 0.0325, fee amounts like 15.00, transaction limits like 10000), hard-coded dataset names and file paths, hard-coded account type codes and status flags—all the things that should be in configuration tables.

- **Documentation Disasters**: Comments that contradict the actual code behavior, obsolete comments from requirements that changed years ago, complex logic sections with no comments at all, and misleading variable names that confuse rather than clarify.

- **Error Handling Roulette**: SQLCODE checking scattered inconsistently (some modules check every statement, others ignore errors), missing error handling in critical sections, silent failures where errors aren't logged, and generic error messages like "ERROR IN PROCESSING" without context.

- **Design Debt**: Business logic buried in SQL WHERE clauses, circular module dependencies creating tight coupling, monolithic programs exceeding 28,000 lines doing too many things, God modules that orchestrate entire workflows, and tight coupling between modules that should be independent.

- **Legacy Accumulation**: Dead code from features removed years ago but never cleaned up, half-implemented features started and abandoned, workarounds for "temporary" issues that became permanent, multiple layers of patches simulating 30+ years of maintenance, and mixed COBOL standards as the language evolved.

### Out of Scope

- CICS transaction processing
- IMS database integration
- Complex JCL conditionals (keeping JCL simple)
- Real-time online processing
- Web services or API integration
- Modern COBOL features (COBOL 2014+)
- Production deployment infrastructure
- Performance optimization

---

## Target Users & Use Cases

### Primary Users

**1. COBOL Developers**
- **Need:** Understand unfamiliar code quickly, identify bugs, make safe changes
- **Use Case:** Use AI assistant to explain what module TXNROUTE does, identify why overdraft logic is failing
- **Test Scenario:** Can AI trace transaction flow from TXNLOAD through posting?

**2. Application Owners**
- **Need:** Extract business rules, understand what the application does
- **Use Case:** Generate business logic documentation for regulatory audit
- **Test Scenario:** Can AI document interest calculation rules from INTMAST module?

**3. Tech Architects**
- **Need:** Assess modernization opportunities, identify refactoring candidates
- **Use Case:** Identify modules with highest technical debt, find duplicate logic
- **Test Scenario:** Can AI identify the duplicate interest calculation logic in INTCALC1 vs INTCALC2?

**4. Business Analysts**
- **Need:** Map code to business requirements, verify business rule implementation
- **Use Case:** Validate that fee waiver rules match business policy
- **Test Scenario:** Can AI extract complete business rules from FEEWAIVE module?

### User Journeys

**Journey 1: Code Comprehension**
1. Developer encounters unfamiliar module (e.g., EODMAIN - 28K LOC)
2. Asks AI: "What does this module do?"
3. AI should identify: EOD orchestrator with checkpoint/restart, multi-pass processing
4. Developer asks: "What happens when checkpoint fails?"
5. AI should trace error handling logic (or lack thereof)

**Journey 2: Business Logic Extraction**
1. Business analyst needs to document interest calculation
2. Asks AI to extract business rules from INTMAST
3. AI should identify: account types, tiered rates, daily accrual, promotional logic
4. Analyst asks for flowchart or decision tree
5. AI generates visual documentation

**Journey 3: Refactoring Opportunities**
1. Architect reviews codebase for modernization
2. Asks AI: "What are the top 10 code smells?"
3. AI identifies: duplicate logic, deep nesting, magic numbers, dead code
4. Architect asks: "How would you refactor TXNROUTE?"
5. AI suggests decomposition strategy with smaller, focused modules

---

## Technical Specifications

### Application Architecture

**Module Distribution:**
- **Total Modules:** 40 COBOL programs
- **3 Huge Modules (28-30K LOC):**
  - TXNROUTE (30K) - Transaction routing orchestrator
  - INTMAST (30K) - Interest calculation engine
  - EODMAIN (28K) - End-of-day orchestrator
- **37 Standard Modules (5-15K LOC):** Supporting business logic and utilities

**Technology Stack:**
- COBOL (mixed COBOL-74 and COBOL-85 standards)
- DB2 with embedded SQL (EXEC SQL...END-EXEC)
- VSAM files (KSDS, ESDS, RRDS)
- Sequential files with GDG management
- JCL for batch orchestration
- Middleware utility library

### Business Function Breakdown

#### Function 1: Daily Transaction Processing (12 Modules)

**Purpose:** Process daily banking transactions (deposits, withdrawals, transfers)

**Modules:**
1. TXNLOAD (8K) - Load transaction input file
2. TXNVAL01 (12K) - Format validation
3. TXNVAL02 (15K) - Business rule validation
4. TXNROUTE (30K) - **HUGE** - Transaction routing and orchestration
5. DEPOPROC (10K) - Deposit processing
6. WDRLPROC (11K) - Withdrawal processing with overdraft
7. XFERPROC (9K) - Transfer processing
8. TXNPOST (14K) - Post to account master VSAM
9. TXNAUDIT (7K) - Audit trail creation
10. TXNERROR (6K) - Error handling and logging
11. TXNRECON (10K) - Control total reconciliation
12. TXNREPT (8K) - Daily transaction reports

**JCL:** DAILYTRX.JCL

**Key Complexity:**
- 4-5 level deep CALL chains
- Transaction routing with embedded business rules
- Inconsistent error handling
- Duplicate validation logic across modules

#### Function 2: Interest & Fee Calculation (11 Modules)

**Purpose:** Calculate and post interest and fees monthly

**Modules:**
1. INTREAD (8K) - Read eligible accounts
2. INTRATE (12K) - Rate table lookup
3. INTMAST (30K) - **HUGE** - Master interest calculation engine
4. INTCALC1 (10K) - Simple interest for checking
5. INTCALC2 (14K) - Compound interest for savings (duplicate logic)
6. INTPOST (9K) - Post interest to accounts
7. FEEMAST (15K) - Fee assessment
8. FEEWAIVE (11K) - Fee waiver logic
9. FEEPOST (8K) - Post fees
10. INTREPT (7K) - Interest reports
11. FEERECON (6K) - Fee reconciliation

**JCL:** MONTHINT.JCL

**Key Complexity:**
- Tiered interest rate logic
- Promotional rate calculations
- Duplicate calculation logic (INTCALC1 vs INTCALC2)
- Complex fee waiver business rules

#### Function 3: End-of-Day Processing (10 Modules)

**Purpose:** Daily balance updates, reconciliation, archiving

**Modules:**
1. EODMAIN (28K) - **HUGE** - EOD orchestrator with checkpoint/restart
2. BALUPD (14K) - Balance updates
3. RECONMST (12K) - Master reconciliation
4. STMTGEN (15K) - Statement generation
5. DORMCHK (9K) - Dormant account identification
6. REGLDGR (13K) - Regulatory ledger
7. ARCHTRX (10K) - Archive transactions to GDG
8. ARCHSTMT (8K) - Archive statements
9. EODREPT (11K) - EOD reports
10. EODCLEAN (7K) - Cleanup work files

**JCL:** EODPROC.JCL

**Key Complexity:**
- Checkpoint/restart logic (some broken)
- Multi-pass processing
- Control break reporting
- GDG management

#### Function 4: Account Maintenance (7 Modules)

**Purpose:** Account lifecycle management (create, update, close)

**Modules:**
1. ACCTVAL (6K) - Common validation
2. ACCTMNT (15K) - Maintenance dispatcher
3. ACCTNEW (12K) - New account creation
4. ACCTUPD (10K) - Account updates
5. ACCTCLS (14K) - Account closure
6. ACCTSTAT (9K) - Status changes
7. ACCTREPT (8K) - Account reports

**JCL:** ACCTMNT.JCL

**Key Complexity:**
- Conditional processing based on transaction type
- Inconsistent validation patterns
- Half-implemented account type conversion

### Data Structures

**Copybooks:**
- Complex REDEFINES structures
- COMP-3 packed decimal for amounts
- Nested group structures (01/05/10 levels)
- Level 88 condition names (used inconsistently)
- Inconsistent naming conventions across copybooks

**VSAM Files:**
- Account Master (KSDS) - Main account records
- Transaction File (ESDS) - Daily transaction input
- Audit Trail (RRDS) - Audit records

**Sequential Files:**
- Transaction input (daily batch)
- Report output files
- Extract files for downstream systems

**DB2 Tables:**
- Account table (master data)
- Transaction history
- Interest rate tables
- Fee schedule tables
- Audit log table

**GDG (Generation Data Groups):**
- Transaction archive (generations: 0, -1, -2, etc.)
- Statement archive
- Daily backup files

### Middleware Layer

**Location:** `/middleware` folder

**Planned Utilities:**
- ERRHAND - Error handling and logging
- DBUTIL - Database access wrappers
- FILEIO - File I/O utilities
- LOGGER - Audit trail and logging
- DATEUTIL - Date/time calculations
- VALIDAT - Common validation routines
- Standard copybooks for error codes, return codes

**Status:** To be defined and implemented

---

## Intentional Complexity & Anti-Patterns

### Code Quality Issues (By Design)

**Control Flow Anti-Patterns:**
- GOTO spaghetti creating unmaintainable logic jumps
- PERFORM...THRU abuse spanning large code sections
- Deeply nested IF statements (8-12 levels)
- Fallthrough logic bugs (missing conditions)
- Missing ELSE clauses causing unexpected behavior

**Code Duplication:**
- Copy-paste logic across modules (e.g., INTCALC1 vs INTCALC2)
- Duplicate validation in multiple modules
- Similar error handling repeated inconsistently

**Hard-Coded Values:**
- Magic numbers throughout (interest rates, fee amounts, limits)
- Hard-coded file names and dataset names
- Hard-coded account types and status codes

**Documentation Issues:**
- Comments contradicting actual code behavior
- Missing comments in complex logic sections
- Obsolete comments from old requirements
- Misleading variable names

**Error Handling:**
- Inconsistent SQLCODE checking
- Missing error handling in critical sections
- Silent failures (errors not logged)
- Generic error messages without context

**Data Management:**
- Inconsistent naming conventions
- REDEFINES creating ambiguous data structures
- Level 88 condition names used poorly
- Mixed data types for similar fields

**Design Issues:**
- Business logic buried in SQL
- Circular module dependencies
- Monolithic modules (28-30K LOC)
- Tight coupling between modules
- God objects/modules doing too much

**Legacy Accumulation:**
- Dead code from old requirements
- Half-implemented features
- Workarounds for "temporary" issues (now permanent)
- Multiple patches simulating 20+ years of changes
- Mixed COBOL standards (COBOL-74 and COBOL-85)

---

## AI Assistant Testing Framework

ABC123 enables comprehensive evaluation of AI assistants across five core capabilities plus stress testing scenarios that push tools to their limits. Each capability includes multiple test prompts ranging from basic comprehension to advanced analysis.

### Five Core Capabilities to Test

#### 1. End-to-End Application Understanding

**Test Scenarios:**
- "Explain the complete flow of a deposit transaction from input to posting"
- "What happens during end-of-day processing?"
- "How do modules interact in the interest calculation workflow?"
- "Map the dependencies between all 40 modules"
- "Trace a withdrawal request through the entire system—which modules are called and in what order?"
- "What files and database tables are touched during transaction posting?"
- "If TXNLOAD fails, what happens to downstream modules?"
- "Explain the relationship between JCL jobs and COBOL programs"
- "What's the difference between how deposits and transfers are processed?"
- "How does the checkpoint/restart logic work in EODMAIN?"

**Expected AI Capabilities:**
- Trace transaction flow across multiple modules
- Identify CALL hierarchies and dependencies
- Understand JCL orchestration
- Recognize data flow through files and databases
- Map error propagation paths
- Comprehend batch workflow sequences

#### 2. Business Logic Extraction

**Test Scenarios:**
- "Document the business rules for overdraft processing"
- "What are the interest calculation rules for different account types?"
- "Extract the fee waiver eligibility criteria"
- "Generate a decision tree for transaction validation"
- "What conditions trigger a maintenance fee?"
- "Explain the tiered interest rate structure in plain English"
- "When is an account marked as dormant?"
- "What are the rules for compound vs simple interest?"
- "Extract all validation rules for new account creation"
- "Document the complete fee schedule and waiver policies"
- "What business rules are enforced during account closure?"
- "Create a requirements document from the interest calculation code"

**Expected AI Capabilities:**
- Identify business rules embedded in code
- Extract conditional logic and decision points
- Generate human-readable documentation
- Create visual representations (flowcharts, decision trees)
- Translate COBOL logic to business language
- Identify implicit vs explicit business rules

#### 3. Improvement Opportunity Identification

**Test Scenarios:**
- "What are the top 10 code smells in this application?"
- "Identify duplicate logic across modules"
- "Find performance bottlenecks"
- "Which modules have the highest technical debt?"
- "Where is error handling inconsistent or missing?"
- "Identify all hard-coded values that should be configurable"
- "Find all instances of GOTO and suggest alternatives"
- "What dead code exists in the application?"
- "Which modules are candidates for refactoring first?"
- "Identify security vulnerabilities in the code"
- "Find SQL injection risks in embedded SQL"
- "What business logic is duplicated between INTCALC1 and INTCALC2?"
- "Identify circular dependencies between modules"
- "Where are magic numbers used instead of named constants?"

**Expected AI Capabilities:**
- Recognize anti-patterns (GOTO spaghetti, deep nesting)
- Identify code duplication
- Detect dead code and unused variables
- Find inconsistent error handling
- Spot magic numbers and hard-coded values
- Prioritize refactoring opportunities
- Identify security and compliance risks

#### 4. Module/Application Rewrites & Modernization

**Test Scenarios:**
- "How would you refactor the TXNROUTE module?"
- "Suggest a modernization strategy for interest calculation"
- "Propose breaking EODMAIN into smaller modules"
- "How can we eliminate the duplicate logic in INTCALC1 and INTCALC2?"
- "Recommend a migration path from batch COBOL to microservices"
- "How would you modernize the file I/O to use APIs?"
- "Suggest refactoring the nested IF statements in TXNVAL02"
- "Propose a strategy to extract business rules from SQL"
- "How could we replace GOTO logic with structured programming?"
- "Design a service-oriented architecture for transaction processing"
- "Recommend patterns to eliminate circular dependencies"
- "How would you introduce unit testing to this codebase?"
- "Suggest a phased approach to modernize ABC123"

**Expected AI Capabilities:**
- Suggest decomposition strategies
- Propose design patterns for refactoring
- Identify reusable components
- Recommend modern COBOL features
- Provide migration paths to modern architectures
- Balance risk with modernization benefits
- Generate refactored code samples

#### 5. Testing & Validation

**Test Scenarios:**
- "Generate test cases for withdrawal processing"
- "Create unit tests for interest calculation"
- "What edge cases should we test in fee waiver logic?"
- "Validate that account closure handles all scenarios"
- "Generate integration tests for the daily transaction batch"
- "What test data is needed to cover all overdraft scenarios?"
- "Identify boundary conditions in balance calculations"
- "Create negative test cases for invalid transactions"
- "What regression tests are needed if we refactor TXNROUTE?"
- "Generate test scenarios for end-of-month processing"
- "What happens if a DB2 connection fails during posting?"
- "Design tests to validate checkpoint/restart logic"

**Expected AI Capabilities:**
- Identify test scenarios from code
- Generate test data
- Recognize edge cases and boundary conditions
- Suggest integration test scenarios
- Validate business rule coverage
- Create both positive and negative test cases
- Identify testability issues in current code

### Stress Testing & Boundary Conditions

Beyond basic capabilities, ABC123 challenges AI assistants with extreme scenarios that reveal performance limits and context handling abilities.

**Depth & Scale Testing:**
- "Trace a transaction through all 5 levels of nested CALL statements"
- "Analyze the complete 28,000-line EODMAIN module end-to-end"
- "Map every dependency in the entire 40-module application"
- "Document every business rule across all four business functions"
- "Find all instances where magic number 0.0325 is used across the codebase"

**Cross-Module Complexity:**
- "Explain how data flows from TXNLOAD → TXNVAL01 → TXNVAL02 → TXNROUTE → DEPOPROC → TXNPOST → TXNAUDIT"
- "What's the impact if we change the ACCTMAST copybook structure?"
- "Trace how middleware utilities are called across all 40 modules"
- "Identify all modules that update the account balance field"

**Ambiguity & Contradictions:**
- "Find all comments that contradict the actual code behavior"
- "Identify logic that seems to implement one rule but actually does something else"
- "What happens when error handling is missing in critical sections?"
- "Explain the workaround logic in [specific module]—what was it trying to fix?"

**Large Context Analysis:**
- "Compare and contrast all four business functions"
- "Analyze the complete middleware layer and its usage patterns"
- "Review the entire application for COBOL-74 vs COBOL-85 patterns"
- "Generate a complete data dictionary from all copybooks"

**Transformation Challenges:**
- "Convert TXNROUTE to microservices architecture"
- "Migrate batch processing to event-driven streaming"
- "Redesign the entire application using modern design patterns"
- "Propose replacing VSAM files with cloud-native storage"

**Accuracy Under Complexity:**
- "Calculate cyclomatic complexity for all modules and rank them"
- "Count exact lines of code with GOTO statements"
- "Identify every DB2 table access across all modules"
- "List all possible error codes returned by the application"

---

## Success Metrics

### Quantitative Metrics

**Application Completeness:**
- ✅ 40 COBOL modules implemented
- ✅ 400K-500K total lines of code
- ✅ 4 JCL job streams functional
- ✅ 100% of modules contain intentional anti-patterns
- ✅ 100% business functions executable end-to-end

**Complexity Targets:**
- ✅ 3 modules exceed 25K LOC
- ✅ 37 modules between 5K-15K LOC
- ✅ Average cyclomatic complexity > 20 per module
- ✅ Call depth reaches 4-5 levels
- ✅ 50+ copybooks with complex structures

**AI Testing Coverage:**
- ✅ Test scenarios defined for all 5 AI capabilities
- ✅ Benchmark questions created for each business function
- ✅ Expected answers documented for validation

### Qualitative Metrics

**Realism:**
- Code mimics authentic legacy COBOL characteristics
- Anti-patterns reflect real-world technical debt
- Business logic matches actual banking workflows
- Data structures typical of mainframe applications

**Usability:**
- Clear documentation of intentional complexity
- Test scenarios easy to execute
- Results easy to compare across AI assistants
- Extensible for future test cases

**Differentiation:**
- AI assistants produce measurably different results
- Test challenges reveal capability gaps
- Performance varies across the 5 core capabilities

---

## Assumptions & Constraints

### Assumptions

1. **Target Environment:** Mainframe z/OS with COBOL, DB2, VSAM (or equivalent emulation)
2. **AI Assistants:** Have COBOL language support and can process large context windows
3. **Evaluation Approach:** Manual or semi-automated comparison of AI assistant outputs
4. **Business Logic:** Banking domain knowledge is sufficient for realistic workflows
5. **Middleware:** Standard utility patterns represent typical mainframe shops

### Constraints

**Technical Constraints:**
- COBOL only (no CICS, IMS, or web services)
- DB2 only (no other database systems)
- Batch processing only (no online/real-time)
- JCL kept simple (complexity in COBOL, not JCL)

**Resource Constraints:**
- Single developer (Kamal) initially
- Limited mainframe environment access
- Budget constraints for tooling

**Scope Constraints:**
- Banking domain only (no insurance, healthcare, etc.)
- Cash account management only (no loans, investments, etc.)
- Test harness only (not production application)

---

## Risks & Mitigation

### Technical Risks

**Risk 1: Insufficient Complexity**
- **Impact:** AI assistants handle test cases too easily, no differentiation
- **Mitigation:** Include diverse anti-patterns, verify with pilot testing, iterate complexity
- **Contingency:** Add more challenging scenarios based on pilot results

**Risk 2: Unrealistic Anti-Patterns**
- **Impact:** Test doesn't reflect real legacy code challenges
- **Mitigation:** Consult COBOL experts, reference actual legacy codebases, validate patterns
- **Contingency:** Revise anti-patterns based on expert feedback

**Risk 3: Tool Compatibility Issues**
- **Impact:** AI assistants can't process file formats or code structure
- **Mitigation:** Test with multiple AI tools early, use standard formats
- **Contingency:** Adjust file structure or provide alternative formats

### Scope Risks

**Risk 4: Scope Creep**
- **Impact:** Project expands beyond 40 modules, delays completion
- **Mitigation:** Strict scope definition, phased approach, module limit enforced
- **Contingency:** Defer additional features to future versions

**Risk 5: Incomplete Testing Framework**
- **Impact:** Can't effectively compare AI assistant performance
- **Mitigation:** Define test scenarios upfront, create evaluation rubric
- **Contingency:** Iterate testing framework based on initial results

---

## Timeline & Phases

### Phase 1: Foundation (Weeks 1-2)
- Define middleware utilities
- Create copybook structures
- Design VSAM file layouts
- Define DB2 table schemas
- Document anti-pattern guidelines

### Phase 2: Core Development (Weeks 3-8)
- Implement Function 1: Daily Transaction Processing (12 modules)
- Implement Function 2: Interest & Fee Calculation (11 modules)
- Implement Function 3: End-of-Day Processing (10 modules)
- Implement Function 4: Account Maintenance (7 modules)
- Create JCL job streams

### Phase 3: Complexity Injection (Weeks 9-10)
- Add intentional anti-patterns
- Inject dead code and duplicate logic
- Create inconsistent error handling
- Mix COBOL standards
- Add misleading comments

### Phase 4: Testing Framework (Weeks 11-12)
- Define test scenarios for 5 AI capabilities
- Create benchmark questions
- Document expected answers
- Develop evaluation rubric
- Pilot test with AI assistants

### Phase 5: Validation & Refinement (Weeks 13-14)
- Run pilot tests with multiple AI assistants
- Analyze results and differentiation
- Refine complexity and test scenarios
- Finalize documentation
- Prepare release

**Total Duration:** 14 weeks (3.5 months)

---

## Dependencies

### External Dependencies
- Mainframe environment or emulator for testing
- DB2 database or compatible system
- JCL execution environment
- AI code assistant tools for validation

### Internal Dependencies
- Middleware utility definitions (to be created)
- Copybook library completion
- DB2 schema definitions
- Test data generation

### Knowledge Dependencies
- COBOL expertise (COBOL-74 and COBOL-85)
- Banking domain knowledge
- Mainframe file system understanding (VSAM, GDG)
- DB2 and embedded SQL knowledge

---

## Stakeholders

### Primary Stakeholder
**Kamal** - Project Lead
- Responsible for: Overall project direction, development, testing

### Secondary Stakeholders
**COBOL Developer Community**
- Interest: Realistic test harness for AI assistant evaluation
- Input needed: Validation of anti-patterns and complexity

**AI Code Assistant Vendors**
- Interest: Benchmark for capability demonstration
- Input needed: Compatibility requirements, test scenario feedback

**Modernization Consultants**
- Interest: Standardized evaluation framework
- Input needed: Real-world scenarios and use cases

---

## Next Steps

### Immediate Actions (This Week)

1. ✅ **Complete brainstorming session** - DONE
2. ✅ **Create project brief** - DONE
3. **Define middleware utilities** - Create utility specifications in `/middleware` folder
4. **Create copybook templates** - Design standard copybook structures
5. **Design DB2 schema** - Define table structures for banking data

### Short-Term Actions (Next 2 Weeks)

1. **Create Product Requirements Document (PRD)** - Detailed functional requirements
2. **Design Architecture Document** - Technical architecture and design decisions
3. **Create development environment setup guide**
4. **Begin Phase 1 implementation** - Foundation components

### Long-Term Actions (Next 3 Months)

1. Complete all 40 COBOL modules
2. Inject intentional complexity
3. Develop testing framework
4. Pilot test with AI assistants
5. Refine and release v1.0

---

## Appendix

### Glossary

- **COBOL** - Common Business-Oriented Language
- **VSAM** - Virtual Storage Access Method
- **KSDS** - Key-Sequenced Data Set
- **ESDS** - Entry-Sequenced Data Set
- **RRDS** - Relative Record Data Set
- **GDG** - Generation Data Group
- **JCL** - Job Control Language
- **DB2** - IBM's relational database management system
- **LOC** - Lines of Code
- **EOD** - End of Day
- **COMP-3** - Packed Decimal (computational-3)

### References

- Brainstorming Session: `/core/analysis/brainstorming-session-2026-01-07.md`
- Middleware Folder: `/middleware`
- Project Root: `/home/kamal/Documents/Garage/cobolapp`

### Document Control

- **Version:** 1.0
- **Last Updated:** 2026-01-07
- **Next Review:** After Phase 1 completion
- **Owner:** Kamal
