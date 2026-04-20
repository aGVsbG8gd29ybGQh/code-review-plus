[🎉🎉 Get Discount Code 🎉🎉](https://github.com/aGVsbG8gd29ybGQh/code-review-plus/issues/1)

# Code Review Plus - Intelligent Code Review Assistant

<div align="center">

![Plugin Icon](images/pluginIcon.svg)

**Dedicated to making code reviews easier**

An IntelliJ IDEA plugin that helps you review code efficiently with session management, incremental review, AI-powered review, automated rules, and a comment system

[![Version](https://img.shields.io/badge/version-4.1.0-blue.svg)](https://plugins.jetbrains.com/plugin/29361-code-review-plus)
[![IDEA Version](https://img.shields.io/badge/IDEA-2025.2+-orange.svg)](https://www.jetbrains.com/idea/)

</div>

---

## Table of Contents

- [Why Code Review Plus](#why-code-review-plus)
- [Core Features](#core-features)
- [Free & Paid](#free--paid)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [User Guide](#user-guide)
- [Auto Review Rules [Premium]](#auto-review-rules-premium)
- [AI Review [Premium]](#ai-review-premium)
- [AI Auto-Fix [Premium]](#ai-auto-fix-premium)
- [Report Export & Import](#report-export--import)
- [Plugin Settings](#plugin-settings)
- [Best Practices](#best-practices)
- [FAQ](#faq)
- [License & Feedback](#license--feedback)

---

## Why Code Review Plus

Common pain points during code reviews:

- **Interrupted mid-review** — you come back and can't remember what you've already checked
- **New commits on the branch** — unsure if your previous review still holds, so you start over
- **Issues found but lost in follow-up** — tracked in scattered notes, fixed or not remains unclear
- **Noise from trivial changes** — import reordering, formatting, blank lines mixed with real logic, forcing you to verify each one manually

Code Review Plus addresses these from four directions:

**Automated review — filter noise, surface deep issues**: Auto review rules skip import adjustments, whitespace changes, and other noise in one click. AI Review runs three expert agents in parallel to automatically detect coding defects, security vulnerabilities, and database risks — issues that would otherwise take hours to find manually.

**Persistent progress — no interruptions, no omissions**: Every code block's review status is saved locally and restored instantly after IDEA restarts. Whether you review in batches or step away mid-session, you always know exactly where you left off.

**Incremental updates — pinpoint what actually changed**: When new commits land on the branch, click refresh. The system identifies which code truly changed — already-reviewed blocks keep their status, only new and modified code needs another look. No starting over.

**Trackable comments — no issue slips through**: Each comment carries a Pending / No Action Needed / Resolved status and persists through branch updates. Export a report and the developer works through every comment one by one, closing the review loop completely.

### Who Should Use This

**Developers**: Self-review before submitting. Use auto review to strip format noise and AI Review to catch security risks and coding issues before delivery — fix problems before reviewers even see them, eliminating unnecessary back-and-forth.

**Reviewers**: Let AI and auto rules do the first pass — common issues are flagged automatically. You focus only on the code that truly requires judgment. Review time drops significantly. Progress is always saved, comments are trackable, and a one-click report export completes the collaboration loop.

---

## Core Features

### Session Management

Select a review branch and a base branch to create a review session. The plugin calculates all differences between the two branches, listing changed files and code blocks.

- Session data is automatically saved locally and restored after IDEA restarts
- Multiple review sessions can be managed simultaneously within the same project
- Review data is isolated between different projects

### Status Tracking

Mark a review status for each code change block (Diff Block):


| Icon | Status | Meaning | Use Case |
|:----:|--------|---------|----------|
| <img src="images/gutterCheckBoxSelected_gray_1.svg" width="16" height="16"> | Unreviewed | Not yet processed | Default status, awaiting review |
| <img src="images/gutterCheckBoxSelected_green.svg" width="16" height="16"> | Passed | Code looks good | Confirmed as expected |
| <img src="images/warning.svg" width="16" height="16"> | Issues | Needs attention | Found issues or needs discussion |
| <img src="images/lightning_green.svg" width="16" height="16"> | Auto Passed | Code looks good | Confirmed by auto review rules |
| <img src="images/lightning_orange.svg" width="16" height="16"> | Auto Issues | Needs attention | Flagged by auto review rules |

The first three statuses are set manually: click the icon next to the line number in the Diff view to cycle through them (Unreviewed → Passed → Issues → Unreviewed). The last two are set by auto review rules and cannot be changed manually. Block-level statuses are automatically aggregated to the file level, giving you an at-a-glance view of each file's overall review status.

### Incremental Review

After new commits on the branch, click the refresh button. The system recalculates differences and intelligently matches them against the previous review state:


| Scenario | Behavior |
|----------|----------|
| Code unchanged | Preserves previous review status and comments |
| Code modified | Resets to Unreviewed, comments become floating |
| New code | Marked as Unreviewed |
| Deleted code | Automatically cleaned up |

This means you don't have to start over — just continue reviewing the changed parts.

### Comment System

Add text comments to code in the Diff view to record issues and improvement suggestions.

**Comment numbering**: Each comment is automatically assigned a unique sequential number (e.g., C1, C2, C3) within a session. Comment numbers are displayed in the Comment List, gutter icon tooltips, and exported reports for easy reference and communication.

**Comment priority**: Each comment can be assigned a priority level, helping developers distinguish must-fix critical issues from optional suggestions.

| Icon | Priority | Meaning |
|:----:|----------|---------|
| <img src="images/comment_mandatory.svg" width="16" height="16"> | Mandatory | Affects service stability or data integrity — must be fixed before release |
| <img src="images/comment_recommended.svg" width="16" height="16"> | Recommended | May affect service in edge cases — recommended to fix before release |
| <img src="images/comment_advisory.svg" width="16" height="16"> | Advisory | Code style or best-practice suggestion — no stability impact, address at your discretion |

Priority can be set when adding a comment and changed afterward. Issues submitted by AI Review are automatically assigned a priority based on their severity.

**Comment statuses**:


| Icon | Status | Meaning |
|:----:|--------|---------|
| <img src="images/comment_orange.svg" width="16" height="16"> | Pending | Issue that needs the developer's attention |
| <img src="images/comment_light_green.svg" width="16" height="16"> | No Action Needed | Confirmed no changes required |
| <img src="images/comment_green.svg" width="16" height="16"> | Resolved | Issue has been fixed |

**Floating comments**: When a comment's associated code block changes after a branch update, the comment is preserved but marked as "floating". You can still view the original code as it was when the comment was created.

### Auto Review [Premium]

Automatically mark code block statuses based on predefined rules. For example:

- A code block with only whitespace changes → automatically marked as "Passed"
- A new `import *` statement added → automatically marked as "Issues"
- Hardcoded secrets detected → automatically marked as "Issues"

Auto review helps you skip trivial changes and focus on code that truly needs attention. Rules can be freely enabled and disabled in settings.

### AI Review [Premium] ✨ New in v4.0 / Extended in v4.1

Powered by **AI CLI + MCP Server** architecture, AI Review lets AI autonomously perform code review. The plugin launches a local MCP HTTP Server, and AI CLI subprocesses connect via tool calls to retrieve diff content, read source files, and submit findings — no human intervention required.

Three expert agents run in parallel, covering different dimensions:

- **Code Quality Review Expert**: Detects null pointer risks, resource leaks, swallowed exceptions, concurrency hazards, missing enum fallbacks, serialization compatibility, logging anti-patterns, and more
- **Security & Stability Review Expert**: Detects missing XSS/CSRF protection, SQL/command/path traversal/XXE/SSRF injection, auth bypass, privilege escalation, hardcoded secrets, sensitive data exposure, and more
- **Database Review Expert**: Detects N+1 queries, large table queries without pagination, leading-wildcard LIKE, function calls on indexed columns, unconditional full-table updates/deletes, oversized IN lists, and more

AI Review supports **full session review** (all unreviewed blocks) and **partial review** (right-click selected files). Progress is streamed in real time to an output dialog with one tab per expert.

Advantages of using AI Review within the plugin:
1. Building on auto review — a large portion of diffs have already been marked as auto-passed. When the AI retrieves content via the MCP server, these blocks are excluded, reducing the volume of code the AI needs to process.
2. Comments created before AI Review starts are passed to the AI via the MCP server. The AI uses this information to avoid re-flagging already-discovered issues while helping surface additional problems.
3. After review, the AI submits its findings via the MCP server. This makes review artifact management straightforward and provides data support for future re-reviews.

**v4.1: Codex CLI support added**

In addition to Claude Code CLI, v4.1 introduces support for **Codex CLI** (OpenAI). AI Review and AI Auto-Fix can each independently use either CLI — you can even mix them (e.g., review with Codex, fix with Claude Code).

> **Prerequisites**: Install and configure the CLI tool of your choice. See the [AI Review](#ai-review-premium) section for details.

### Report Export & Import

Export review results as an HTML report containing review progress, code diffs, and all comments. The report can be sent to the branch developer, who can import it directly into their own IDEA to view the reviewer's comments and fix issues one by one.

Recommended collaboration workflow: **Reviewer flags issues → Exports report → Developer imports report → Reviews comments and fixes → Notifies reviewer to confirm**, forming a closed-loop review process.

---

## Free & Paid

Code Review Plus uses a Freemium model: **Auto Review and AI Review require a license**. All other features (session management, status tracking, incremental review, comment system, report export & import, etc.) are free to use.

Our commitment: **existing free features will always remain free, with no license restrictions added in the future**. You can use them with confidence.

Premium features come with a 30-day trial period automatically activated upon installation from JetBrains Marketplace. After the trial expires, you can purchase a license on the Marketplace to continue using them. If you'd like an extended trial period, please contact us by email with your reason, and we'll consider providing a free license.

---

## Installation

### System Requirements

- IntelliJ IDEA 2025.2 or later (Community and Ultimate editions supported)
- Git plugin (built into IDEA, no separate installation needed)
- OS: Windows / macOS / Linux

### Install from JetBrains Marketplace (Recommended)

1. Open IDEA, go to `Settings` → `Plugins`
2. Select the `Marketplace` tab
3. Search for **Code Review Plus**
4. Click `Install`, then restart IDEA

We recommend always installing through the Marketplace and keeping the plugin up to date. The Marketplace will automatically notify you of updates, ensuring you're using the most stable version.

### Manual Installation

1. Download the plugin `.zip` file
2. Open IDEA, go to `Settings` → `Plugins`
3. Click the gear icon → `Install Plugin from Disk...`
4. Select the downloaded `.zip` file, then restart IDEA

### About Version Downgrading

**Do not downgrade to an older version.** The plugin's database schema evolves with each version upgrade. Downgrading may cause the plugin to fail to start and result in unrecoverable data corruption and loss of review data. If you encounter issues with the current version, please contact us through the feedback channels instead of downgrading.

---

## Quick Start

### 1. Open the Tool Window

After installation, find the **Code Review Plus** icon in IDEA's left sidebar and click it.

You can also open it via the menu: `View` → `Tool Windows` → `Code Review Plus`.

### 2. Create a Review Session

Open the session creation dialog using any of the following methods:

1. **Tool Window**: Click the **+** button in the toolbar → `New Session...`
2. **Menu Bar**: `Tools` → `Code Review Plus` → `Start Review...` (shortcut `Ctrl+Shift+R` / macOS `Cmd+Shift+R`)
3. **Project Context Menu**: `Code Review Plus` → `Start Review...`

In the dialog, select:

- **Review Branch**: The feature branch you want to review
- **Base Branch**: The comparison baseline, typically `master`

Click OK, and the plugin will calculate all differences between the two branches.

**Note**:

- The review branch must contain all commits from the base branch
- If there are uncommitted or unpushed local changes, a warning will be shown but it won't prevent session creation

### 3. Review Code Blocks

Double-click a file in the file list to open the Diff view. Click the status icon next to the line number to mark each code block:

- Click once: Unreviewed → Passed
- Click again: Passed → Issues
- Click again: Issues → Unreviewed

### 4. Add Comments (Optional)

Right-click in the Diff view and select `Add Comment` to write a comment on the code. Comments are linked to the corresponding code block for easy tracking.

### 5. Refresh Session

When there are new commits on the review branch, click the refresh button in the toolbar. Previously reviewed code blocks will retain their status — you only need to focus on new or modified parts.

### 6. Export Report (Optional)

After completing the review, click the export button in the toolbar to save the review results as an HTML report.

---

## User Guide

### Toolbar


| Button | Function | Description |
|--------|----------|-------------|
| <img src="images/add.svg" width="16" height="16"> | New Session | Create a new review session or import from a report |
| <img src="images/refresh.svg" width="16" height="16"> | Refresh | Incrementally update the current session's diff data |
| <img src="images/delete.svg" width="16" height="16"> | Delete Session | Delete the current session and all associated data |
| <img src="images/run.svg" width="16" height="16"> | Auto Review | Run predefined auto review rules on the current session (fast, rule-based) |
| <img src="images/run.svg" width="16" height="16"> | AI Review | Start AI review — Claude Code CLI reviews all unreviewed blocks autonomously [Premium] |
| <img src="images/show.svg" width="16" height="16"> | Switch View | Toggle between Diff Block List and Comment List |
| <img src="images/filter.svg" width="16" height="16"> | Filter | Filter files by review status or change type |
| <img src="images/export.svg" width="16" height="16"> | Export Report | Export review results as an HTML report |
| <img src="images/close.svg" width="16" height="16"> | Close Session | Close the current session but preserve data for later |

### Filtering

In **Diff Block List** view, filter by review status: All / Unreviewed / Passed / Issues.

In **Comment List** view, filter by comment status: Pending / No Action Needed / Resolved, or by change type.

### Statistics Panel

The bottom of the tool window displays real-time review progress:

```
Review Progress: 45/120 blocks (37.5%)
  Passed: 40    Issues: 5    Unreviewed: 75
```

Completion formula: (Passed + Issues) / Total × 100%

### Comment Management

**Add a comment**: Right-click in the Diff view → `Add Comment`. Supports selecting multiple lines as the comment range. Maximum 500 characters per comment. Each comment is automatically assigned a number.

**View comments**: Click the comment icon in the Diff view's gutter area to view a single comment's details, or switch to the Comment List view for a consolidated view.

**Search comments**: In the Comment List view's search box, three search modes are supported: enter a comment number (e.g., C1) for exact match, search by file name or path, or search by comment content keywords. Results are a union of all matching modes.

**Status transitions**: Pending → No Action Needed / Resolved. Change status in the comment panel or comment list.

**Batch operations**: In the Comment List view, select multiple comments and right-click to update statuses or delete in bulk.

**Navigate to code**: Double-click a comment in the Comment List to jump to the corresponding location in the Diff view.

---

## Auto Review Rules [Premium]

Auto review uses predefined rules to batch-mark code block statuses, reducing manual effort. You can click the "Auto Review" button in the toolbar to run on all files, or right-click selected files in the file list to run a partial auto review on specific files only.

### Built-in Rules

Rules are organized into seven categories, displayed as a categorized tree in the settings panel.

---

#### Security

##### Hardcoded Secret Detection

Detects sensitive credential strings embedded directly in code, preventing secrets from leaking through commits. Covered scenarios:

- Password assignments: `password = "abc123"`, `passwd = "P@ssw0rd"`
- API Key / Token: `apiKey = "sk-xxxx"`, `token = "eyJxxx"`
- JWT / signing keys: `secretKey = "jwt-secret"`, `signingKey = "..."`
- Private key PEM strings: literals containing `-----BEGIN PRIVATE KEY-----`
- Common credential keywords: `credential`, `authorization`, `access_key`, `secret`, `auth_token`, etc.

Excluded scenarios (to reduce false positives):

- Comment lines (starting with `//`, `/*`, or `*`)
- Swagger / OpenAPI annotation `example` attribute values, e.g. `@ApiModelProperty(example = "token_abc123")`
- Constants whose variable name contains `PATTERN`, `REGEX`, `EXAMPLE`, or `PLACEHOLDER` (regex patterns or placeholder values)

##### Prohibit Wildcard Imports (import \*)

Detects new wildcard `import` statements such as `import java.util.*`. Wildcard imports pull in all classes from a package, increasing the risk of naming conflicts and reducing code readability.

---

#### Code Defect

Leverages IDEA's PSI (Program Structure Interface) for Java semantic-level analysis, detecting code defects that may cause unintended behavior and are easily missed in manual review.

> All rules in this category depend on the Java PSI API and require a Java-capable IDE (IntelliJ IDEA).

##### Concurrency Bug Detection

Detects `static` non-`final` mutable fields inside Spring Bean classes (singletons). Because Spring Beans are singletons shared across all requests, using thread-unsafe types as `static` fields causes concurrent data corruption.

Applies to classes annotated with: `@Service`, `@Component`, `@Repository`, `@Controller`, `@Configuration`.

Covered scenarios:

- **Critical risk**: `static SimpleDateFormat`, `static Calendar` — thread-unsafe; concurrent formatting causes date corruption
- **High risk**: `static HashMap`, `static ArrayList`, `static HashSet` — non-thread-safe collections used as shared global state, leading to data loss or exceptions under concurrency

##### Conditional Null Dereference Detection

Detects chained method calls where an intermediate method is annotated `@Nullable` and its return value is used directly without a null guard:

```java
// ❌ getUser() is @Nullable — direct chaining may throw NPE
service.getUser(id).getName()

// ✅ Safe alternatives
User user = service.getUser(id);
if (user != null) { user.getName(); }
```

The following safe patterns are excluded (no false positives):

- `if (a.b() != null) { a.b().c(); }` — explicit if guard
- `a.b() != null ? a.b().c() : null` — ternary guard
- `if (x != null && a.b() != null) { a.b().c(); }` — compound condition guard

##### Precision Trap Detection

Detects five BigDecimal misuse patterns and three additional numeric precision issues:

**BigDecimal misuse:**

- `new BigDecimal(0.1)` — double constructor causes precision loss; actual value is `0.1000000000000000055511...`; use `BigDecimal.valueOf(0.1)` or `new BigDecimal("0.1")` instead
- `a == b` (both `BigDecimal`) — reference equality, almost always `false`; use `a.compareTo(b) == 0`
- `a.equals(b)` for `BigDecimal` — compares both value and scale; `new BigDecimal("1.0").equals(new BigDecimal("1.00"))` returns `false`; use `compareTo`
- `a.divide(b)` (single argument) — throws `ArithmeticException` on non-terminating decimals (e.g., 1/3); use `a.divide(b, 2, RoundingMode.HALF_UP)`
- `bigDecimal.intValue()` / `longValue()` — truncates the fractional part without rounding; `new BigDecimal("3.99").intValue()` returns `3`

**Floating-point comparison:**

- `if (a == 0.3)` where `a` is `double` — IEEE 754 precision errors make this condition never true; use `Math.abs(a - 0.3) < 1e-9`

**Integer overflow assigned to long:**

- `long total = count * 1024 * 1024` where `count` is `int` — the multiplication overflows in `int` space before widening to `long`; use `(long) count * 1024 * 1024`

**Long field frontend serialization:**

- `Long` fields in VO/DTO classes (e.g., snowflake IDs) returned to the frontend without `@JsonSerialize(using = ToStringSerializer.class)` — JavaScript's `Number` type cannot safely represent values beyond 2^53-1, causing ID precision loss in the browser

##### Loop Database Query Detection (N+1)

Detects database queries issued inside loop boundaries — a leading cause of performance incidents that other static tools cannot detect because they cannot simultaneously understand loop scope and DB call semantics.

Recognized loop forms:

- `for` / `while` / `do-while` / `for-each` — standard Java loops
- `.forEach(lambda)` / `.stream().map(lambda)` and other Stream API pipeline operations

DB call identification (structural evidence only, no method name guessing):

- Class implements `JpaRepository` / `CrudRepository` (Spring Data JPA)
- Class name ends with `Mapper`, `Repository`, or `Dao`
- Method is annotated with `@Select`, `@Update`, `@Insert`, or `@Delete` (MyBatis)

> This rule is disabled by default. Enable it as needed.

---

#### Code Quality

##### Debug Code Leftover

Detects the following debug output statements that should not appear in production code:

- `System.out.println(...)`
- `System.err.println(...)`
- `e.printStackTrace()`

##### TODO / FIXME Comments

Detects new `TODO`, `FIXME`, `HACK`, `XXX`, and similar marker comments. During review, these flag unresolved items that should be confirmed: can they be merged now, or must they be addressed before the PR is accepted?

---

#### Spring Framework

Deep analysis rules designed for Spring/Spring Boot projects, using PSI semantic analysis to catch framework usage issues easily missed in manual review.

> All rules in this category depend on the Java PSI API. In IDEs without Java support, they are automatically skipped without affecting other plugin features.

##### Spring Circular Dependency Detection

Detects circular dependencies between Spring Beans, with severity graded by injection type:

- **Constructor injection cycle (Critical)**: throws `BeanCurrentlyInCreationException` at startup — cannot be bypassed, must be refactored
- **`@Bean` method parameter cycle (Critical)**: `@Bean` methods in a `@Configuration` class depend on each other cyclically — also causes startup failure
- **Field / Setter injection cycle (Warning)**: application starts but initialization order is non-deterministic; refactoring is recommended
- **`@Lazy`-mitigated cycle (Info)**: at least one side uses `@Lazy` to break the cycle at runtime; flags the underlying design concern

##### Spring Injection Issue Detection

Detects six categories of common Spring injection problems:

- **Scope mismatch**: a Prototype-scoped Bean is injected into a Singleton Bean, caching the Prototype instance and breaking per-request semantics
- **Layer violation (Controller → Repository)**: Controller directly depends on Repository, bypassing the Service layer's business encapsulation
- **Reverse layer dependency**: Repository's call chain reaches Service or Controller; Service's call chain reaches Controller — lower layers calling upper layers violates the layered architecture principle (traced up to 3 hops via call graph)
- **Ambiguous injection**: an interface has multiple implementations without `@Primary` or `@Qualifier` — throws `NoUniqueBeanDefinitionException` at runtime
- **Nullable injection without null check**: an `@Autowired(required=false)` field is accessed without a null check — throws NPE when the Bean is absent
- **Unused injected field**: an injected Bean is never referenced anywhere in the class — dead dependency that adds unnecessary maintenance burden

##### `@Transactional` Misuse Detection

Detects two categories of `@Transactional` misuse:

**Annotation ineffectiveness (transaction silently not applied):**

- **Non-public method**: Spring AOP proxies cannot intercept non-public methods; the annotation has no effect
- **`static` / `final` method**: CGLIB proxies cannot override `static` methods or methods of `final` classes
- **Self-invocation**: calling a transactional method via `this.method()` bypasses the proxy entirely
- **Checked exception without `rollbackFor`**: checked exceptions do not trigger rollback by default; must configure `rollbackFor = Exception.class`
- **Swallowed exception in catch block**: the exception is caught and suppressed inside the method, so Spring never sees it and does not roll back
- **`@Async` conflict**: `@Async` and `@Transactional` on the same method causes the async thread to run outside the original transaction context

**Long transaction (network I/O inside transaction):**

Recursively analyzes the call chain of `@Transactional` methods for network I/O operations that hold the database connection longer than necessary:

- **HTTP calls**: `RestTemplate`, `FeignClient`, and similar HTTP clients
- **RPC calls**: Dubbo `@DubboReference` remote calls
- **MQ message sends**: `KafkaTemplate.send()`, `RocketMQTemplate.send()`, etc. (both sync and async sends are detected)
- **Redis operations**: `RedisTemplate` and chained operations (e.g., `opsForValue().set()`, `opsForHash().put()`)

Async boundaries are automatically excluded: calls inside lambdas passed to `Thread`/`ExecutorService`/`CompletableFuture`, and calls to `@Async`-annotated methods.

**Propagation semantic misuse:**

- **`REQUIRES_NEW` called inside a transaction**: the outer transaction is suspended; the inner transaction commits independently — if the outer later rolls back, the inner commit cannot be undone, causing data inconsistency
- **`NOT_SUPPORTED` called inside a transaction**: the outer transaction is suspended and the method runs without a transaction — operations inside cannot be rolled back

---

#### Redis

Designed for Redis usage issues, supporting Java (Spring Data Redis / Jedis), Kotlin, and Go (go-redis).

##### Redis Cache Breakdown Detection

Detects cache breakdown risk in the "cache read → reload → write" pattern. The rule tracks three key elements via PSI: the cache read call (`query1`), the first assignment after the cache miss (`p1`), and the cache write call (`set2`, traced across method boundaries). The reload block from `p1` to `set2` must satisfy both conditions below, otherwise an alert is raised:

- **Reload block unprotected by a lock**: under high concurrency, multiple threads simultaneously miss the cache, causing a stampede to the database
- **Locked but no double-check**: after acquiring the lock, the cache is not re-read to confirm whether another thread has already rebuilt it, causing redundant writes

##### Redis Missing TTL Detection

Detects Redis write operations that do not set an expiration time, preventing keys from permanently consuming memory:

- `ValueOperations.set(key, value)` — 2-arg form (no TTL); 3/4-arg forms include TTL and are not flagged
- `ValueOperations.setIfAbsent(key, value)` — 2-arg form; commonly misused as a distributed lock without a timeout
- `BoundValueOperations.set(value)` / `BoundValueOperations.setIfAbsent(value)` — 1-arg forms (no TTL)
- `setnx(key, value)` — 2-arg form; if the third argument is present and not the literal `0`, it is treated as a timeout and not flagged
- `persist(key)` / `pPersist(key)` — explicitly removes the expiration time, making the key permanent
- Go-redis: `client.Set(ctx, key, value, 0)` / `client.SetNX(ctx, key, value, 0)` — `duration=0` means never expire

##### Redis Dangerous Command Detection

Detects three categories of dangerous Redis commands, in both method call and raw command string forms:

- **Data destruction commands** (must never appear in business code): `FLUSHDB` (wipes the current database), `FLUSHALL` (wipes the entire Redis instance), `SHUTDOWN` (shuts down the Redis server)
- **Full-scan commands** (block the server under large datasets):
  - `KEYS pattern` — O(N) keyspace scan; use `SCAN` cursor iteration instead
  - `HGETALL key` — returns all fields of a Hash in one response; prohibitively large when the Hash has many fields
  - `SMEMBERS key` — returns all members of a Set in one response; same concern as `HGETALL`

---

#### IDE Inspections

Invokes all inspection tools already loaded in IDEA (including third-party plugins such as SonarLint) and runs them against newly added code blocks:

- **IDE Error Inspection**: reports error-level findings from IDEA's built-in inspections
- **IDE Warning Inspection**: reports warning-level findings from IDEA's built-in inspections
- **IDE Weak Warning Inspection**: reports weak-warning-level findings from IDEA's built-in inspections

---

#### Auto Pass

Automatically marks code blocks as "Passed" when conditions are met, helping you skip trivial changes:

- **Import Statement Changes**: code block contains only `import` statement additions or removals
- **Blank Line / Whitespace Changes**: code block contains only whitespace, indentation, or blank line adjustments
- **Comment Changes**: code block contains only comment additions, removals, or edits
- **API Doc Annotation Changes**: code block contains only Swagger 2.x / OpenAPI 3.0 annotation changes (`@Api`, `@ApiModelProperty`, `@Schema`, etc.)
- **Spring Injection Field Changes**: code block contains only `@Autowired` / `@Resource` / `@Inject` field additions/modifications/removals, with no compile errors
- **Rename Only**: file was renamed or moved with no content changes
- **Document and Test Files**: document files (`.md`, `.txt`, `.docx`, `.pdf`, etc.) and code under test directories (`src/test/`, `src/androidTest/`, `__tests__/`, etc.) are automatically marked as passed — no manual review needed

**Combined matching**: When a code block contains multiple safe change types simultaneously (e.g., import adjustments + comment edits + doc annotation changes) and no single rule can match independently, multiple rules collaborate to "strip" their respective safe content. If the remaining old and new code are identical, the block is also automatically marked as passed — extending auto-pass coverage to more real-world scenarios.

### Rule Configuration

Go to `Settings` → `Tools` → `Code Review Plus`, in the Auto Review Settings panel:

- **Global toggle**: Enable/disable the entire auto review feature
- **Categorized tree view**: Rules are grouped by Security / Code Defect / Code Quality / Spring Framework / Redis / IDE Inspections / Auto Pass — toggle each rule with a checkbox
- **Search and filter**: Search by rule name, filter by programming language, or enable/disable all rules at once

### Execution Logic

- Issue rules are executed before pass rules
- Manually marked code blocks are not overridden by auto rules

---

## AI Review [Premium]

AI Review uses AI CLI combined with the plugin's embedded **MCP Server** to perform fully autonomous code review. Three expert agents run in parallel across the code quality, security, and database dimensions, automatically surfacing deep issues that are easy to miss manually.

Since v4.1, both **Claude Code CLI** (Anthropic) and **Codex CLI** (OpenAI) are supported as AI engines — configure the one that matches your setup.

### Prerequisites

Install and configure the CLI tool of your choice:

**Using Claude Code CLI (default)**

Follow the [official Claude Code documentation](https://docs.anthropic.com/en/docs/claude-code/getting-started) to install and log in, then verify in a terminal:
```bash
claude --version   # confirms the command is found
claude -p "hi"     # confirms login is valid; should return a normal response
```

**Using Codex CLI**

Follow the [Codex CLI documentation](https://github.com/openai/codex) to install, and ensure `OPENAI_API_KEY` is set in your environment:
```bash
codex --version    # confirms the command is found
```

**Verify connectivity from plugin settings**

Go to `Settings → Tools → Code Review Plus → AI Review`, then click the **Validate** button next to the relevant "Start Command" field. The plugin will run a version check to confirm the binary is reachable.

If the command works in terminal but validation fails, IDEA's `PATH` likely differs from your shell's. Set the "Start Command" to the full binary path (e.g., `/usr/local/bin/claude`).

**Valid Premium license**

AI Review is a premium feature and requires a valid Code Review Plus Premium license.

**⚠️ Data Security Notice**

AI Review sends your code's diff content to the Claude API for analysis. **Before using this feature, ensure it complies with your organization's data security policies**, including but not limited to: code confidentiality agreements and data transfer restrictions. If in doubt, consult your internal security team or legal department first.

### How It Works

```
IDEA Plugin
  │
  ├─ Starts MCP HTTP Server (localhost:random port)
  │    └─ Provides 3 tools: start_review / get_review_blocks / submit_problem
  │
  └─ Starts 3 Claude Code CLI subprocesses in parallel
       ├─ Code Quality Review Expert Agent
       ├─ Security & Stability Review Expert Agent
       └─ Database Review Expert Agent
            │
            └─ Each agent makes MCP tool calls:
                 1. start_review → get the file manifest
                 2. get_review_blocks → get diff content & semantic summaries
                 3. Read/Grep source files → verify findings
                 4. submit_problem → submit confirmed issues
```

Issues found by each agent are automatically committed to the plugin database and trigger a UI refresh. Problem blocks are marked with "Auto Issues" status.

### Usage

#### Full AI Review

Click the **AI Review** button in the toolbar to review all unreviewed code blocks in the current session.

#### Partial AI Review

Right-click one or more file nodes in the file tree and select **AI Review Selected Files** to review only those files.

#### Real-Time Output

Once review starts, a live output dialog appears with three tabs (Code Quality, Security & Stability, Database), each streaming the corresponding agent's log. Tool calls are shown in a compact format (`● start_review()`, `● submit_problem()`). A completion summary with duration and cost is displayed when each agent finishes.

If the dialog is minimized, a notification with a "View Output" action lets you reopen it at any time.

### What Gets Reviewed

AI Review only processes **UNREVIEWED** blocks. Blocks already marked as Passed or Issues are skipped. Use the status filter before starting to confirm which blocks are unreviewed.

### Configuration

Go to `Settings → Tools → Code Review Plus → AI Review`:

**AI Engine Selection**

| Setting | Description | Default |
|---------|-------------|---------|
| Review Engine | CLI tool for AI Review: Claude Code CLI or Codex CLI | Claude Code CLI |
| Fix Engine | CLI tool for AI Auto-Fix: can be set independently from the review engine | Claude Code CLI |

**Claude Code CLI Settings**

| Setting | Description | Default |
|---------|-------------|---------|
| Start Command | Path to the `claude` binary; use full path if it isn't in PATH | `claude` |
| Model | Claude model to use (e.g. `claude-opus-4-5`); leave blank for CLI default | Blank (CLI default) |

**Codex CLI Settings**

| Setting | Description | Default |
|---------|-------------|---------|
| Start Command | Path to the `codex` binary; use full path if it isn't in PATH | `codex` |
| Model | Model to use (e.g. `o4-mini`); leave blank for CLI default | Blank (CLI default) |

**Shared Settings**

| Setting | Description | Default |
|---------|-------------|---------|
| Enable AI Review | Global on/off switch | Enabled |
| Prompt Language | Output language for review findings: `zh` for Chinese, `en` for English | Follows IDE locale |
| Timeout (minutes) | Maximum wait time per session; leave blank for adaptive timeout (5 min per 50 files, min 5 min) | Adaptive |

**Project-Level Settings**

| Setting | Description | Default |
|---------|-------------|---------|
| Enable Code Quality Review Expert | Enable/disable the code quality review agent; recommended for all projects — covers logic issues, boundary cases, exception handling, and more | Enabled |
| Enable Security & Stability Review Expert | Enable/disable the security & stability review agent; recommended for all projects — covers injection vulnerabilities, memory leaks, infinite loops, sensitive data exposure, and more | Enabled |
| Enable Database Review Expert | Enable/disable the database review agent; recommended for projects using a database — covers slow queries, large result sets, large/long transactions, and more | Enabled |
| Custom Rules | Project-specific coding conventions injected into expert system prompts | Empty |

### Custom Rules

Custom rules are project-level and let teams add extra review requirements for the AI experts. For example:

```
1. All public API endpoint parameters must be validated with @Valid
2. Never use HttpServletRequest/Response directly in the Service layer — pass context instead
3. Database query method names must start with query/get/find/count
```

These notes are injected into all three experts' system prompts simultaneously. Each expert processes the rules accordingly.

### What Each Expert Reviews

> **Note:** Although each expert's system prompt specifies a primary focus area, the AI is not strictly limited to that category. Because AI behavior is not fully predictable, the boundaries between experts are not perfectly distinct — overlap is possible. For example, multiple experts may independently flag the same issue, and this cannot be completely eliminated.

#### Code Quality Review Expert

Focused on coding standards and code quality, for example:

- **Input validation**: Public method boundary checks, null checks on external service responses, null guards on chained calls, Optional.get() protection
- **Resource management**: Correct closure of locks, connections, and IO streams on all execution paths
- **Exception handling**: No silent swallowing, correct propagation in async contexts, log level matches severity
- **Concurrency**: Non-thread-safe object access, thread usage patterns, idempotency checks
- **Enum/state handling**: Missing default/else branch in switch/if-else blocks
- **Serialization compatibility**: New/old version compatibility when adding/removing fields in RPC or MQ message types

#### Security & Stability Review Expert

Focused on security vulnerabilities and stability risks, for example:

- **Injection prevention**: SQL injection (MyBatis `${}`), command injection, path traversal, XXE, SSRF
- **Auth & access control**: Horizontal privilege escalation (missing ownership validation), auth bypass
- **Data security**: Sensitive data in plaintext logs, sensitive fields exposed in responses
- **Interface protection**: Missing XSS/CSRF defense, insecure deserialization
- **Cryptography**: Weak algorithms (MD5/SHA-1 for password storage), hardcoded secrets

#### Database Review Expert

Focused on database operation issues, for example:

- **N+1 queries**: Database calls inside loops
- **Large table risks**: Unconditional full-table queries/updates/deletes, large table queries without pagination
- **Index invalidation**: Leading-wildcard LIKE (`LIKE '%xxx'`), functions on indexed columns
- **Oversized result sets**: Very large IN lists (typically > 1000 elements)
- **High-frequency interfaces**: `SELECT *` in frequently called endpoints

---

## AI Auto-Fix [Premium]

✨ **New in v4.1**

Once AI Review surfaces issues, you can let AI fix the code directly — no manual search, no line-by-line editing. AI Auto-Fix reads the problem description and line numbers from each comment, then edits the source files on your behalf.

The same AI engines supported by AI Review are available for Auto-Fix: **Claude Code CLI** or **Codex CLI**, configured independently in settings.

### How to Use

**Fix all pending issues in the current session**

Click the **AI Fix** button in the toolbar. AI will batch-process all comments in "Pending" status from the current session.

**Fix specific comments only**

Right-click one or more comments in the Comment List and select **AI Fix Selected** to target only those issues.

### How It Works

- Runs concurrently by file — up to 5 files are processed at a time; within each file, issues are addressed in line-number order
- Progress streams in real time to an output panel; you can monitor the AI's actions as they happen
- After completion, the file list refreshes automatically — inspect the diff to confirm the changes
- Only local source files are modified; nothing is committed or pushed automatically

### Things to Keep in Mind

- Fix quality depends on comment clarity — **the more specific the description, the better the result**
- Always build and test after AI Fix to confirm the code behaves as expected
- For complex business logic changes, let AI make the first attempt, then review the output carefully before committing

---

## Report Export & Import

The export and import features are designed to bridge the collaboration gap between reviewers and developers. After completing a review, the reviewer exports a report. The developer imports the report into their own IDEA to see all comments and fix issues one by one. Once fixes are committed, the reviewer pulls the latest code and refreshes the review session to confirm whether issues have been resolved.

Of course, you can also simply use reports for archiving or sharing.

### Export Report

1. Open a review session, click the export button in the toolbar
2. In the dialog, select the export scope and location
3. An HTML report is generated

Report contents include:

- Review progress statistics (Passed / Issues / Unreviewed counts and percentages)
- Changed file list and code diffs
- Comment content and statuses

**Export language**: Supports Chinese and English. Configure in `Settings` → `Tools` → `Code Review Plus`.

**Export directory**: Two modes available:

- Relative path mode: Relative to the project root directory (default)
- Fixed path mode: Uses a fixed absolute directory

### Import Report

1. The developer opens the same project in their own IDEA
2. Click the **+** button in the toolbar, select **Import from Report**, then choose the reviewer's exported HTML report file
3. The system automatically parses the report and creates a review session, restoring the reviewer's comments
4. The developer views comments in the Diff view, locating and fixing issues

Importing creates a new session and does not affect locally created sessions.

---

## Plugin Settings

Go to `Settings` → `Tools` → `Code Review Plus` to configure:


| Setting | Description | Default |
|---------|-------------|---------|
| Export Report Language | Language used for exported reports | English |
| Mark as Issues on Comment | Automatically mark the associated diff block as "Issues" when adding a comment | Off |
| Show Diff Block Toolbar | Display a quick action toolbar on the left side of each diff block in the Diff view for fast diff block navigation | Off |
| Branch Update Check | Automatically detect new remote branch commits and show a reminder | On |
| Default Export Directory | Choose between relative path or fixed path | Relative |
| Auto Review Rule Settings | Configure auto review rule toggles and global options | See above |
| AI Review Settings | Configure AI engine (Claude Code CLI / Codex CLI), model, expert toggles, and custom rules | See above |
| AI Auto-Fix Settings | Configure the fix engine (can differ from the review engine); the toolbar and comment context menu show the Fix button only when this is enabled | Off |

---

## Best Practices

### Daily Review Workflow

**Recommended reviewer workflow**:

1. **Create session** → Select the feature branch and master/develop branch
2. **Run auto review** → Let rules automatically handle whitespace, import, and other trivial changes (fast, seconds)
3. **Run AI review** → Let AI automatically surface code quality, security, and SQL issues (requires AI CLI)
4. **Review file by file** → Start with unreviewed files, double-click to open the Diff view; focus on what AI didn't flag
5. **Mark status + write comments** → Mark passing code as Passed, flag issues as Issues with comments; set priority on important issues
6. **Refresh periodically** → Refresh when the branch has new commits, focus only on changes
7. **Export report** → After review, export for archiving or send to the developer for import

**Developer self-review workflow (recommended before submitting)**:

1. **Create session** → Select your own feature branch
2. **Run auto review + AI review** → Quickly scan for potential issues
3. **Run AI Auto-Fix** → Let AI fix discovered issues automatically (requires AI Auto-Fix enabled in settings)
4. **Check the results** → Review AI-modified code and confirm the logic is correct
5. **Handle remaining issues** → Manually fix complex issues that AI couldn't resolve automatically

### Large Branch Review Strategy

When there are many changed files:

1. **Run auto review first** to filter out formatting, import adjustments, and other noise
2. **Use the filter** to show only "Unreviewed" files
3. **Review in batches** — review some files at a time, progress is automatically saved
4. **Focus on flagged files** — filter for "Issues" files to handle them as a group

### Collaborating with Developers (Recommended Workflow)

1. After review, **export the report** and send it to the branch developer
2. The developer **imports the report** and views review comments in their own IDEA
3. The developer reviews each comment, fixes issues, and commits new code
4. The developer notifies the reviewer to confirm fixes
5. The reviewer **refreshes the session**, and the system automatically detects code changes
6. Check whether previously flagged code blocks have been fixed, then update statuses

### Efficiency Tips

- **Enable "Mark as Issues on Comment"**: Automatically marks the code block as "Issues" when you write a comment, saving one click
- **Use the Comment List view**: View all comments in one place, quickly locate unresolved issues
- **Clean up floating comments regularly**: Delete floating comments that are no longer needed after code updates
- **Configure auto review rules**: Enable rules that match your team's coding standards to reduce repetitive work

---

## FAQ

### How does the plugin identify whether code changes have been reviewed?

The plugin computes a content signature (MD5 based on code position and content) for each code block. During session refresh, it matches signatures to identify:

- Signature matches → Preserves review status
- Signature changed → Resets to Unreviewed
- New signature → Marked as new

### Will review statuses and comments be lost after refreshing?

No. Unchanged code fully retains its status and comments. For modified code, the review status resets to Unreviewed, but comments are preserved as floating comments — you can still view the comment content and the original code as it was when the comment was created.

### Does it support multi-user collaboration?

Review data is stored locally and cannot be shared across machines. For team collaboration, we recommend using GitHub/GitLab PR features. Code Review Plus is best suited for personal pre-review, local code self-checks, or exporting reports to share with your team after completing a local review.

### Does deleting a session affect my code?

No. Deleting a session only removes review data (database records). Git repository code, branch history, and local files are completely unaffected.

### Where is data stored?

Review data is stored in `.idea/code-review-plus.db` (SQLite database) under the project directory. This file is typically in `.gitignore` and won't be committed to version control. All data is stored locally only — the plugin does not depend on any server-side API, and no data is uploaded to any server.

### Why does it say "branch not pushed" when creating a session?

The plugin uses `git diff` to calculate differences, so both the review branch and base branch must exist on the remote repository. Please `git push` the relevant branches first.

### What's the difference between review status and comments?

Review status is marked at the code block level (Unreviewed / Passed / Issues) and reflects overall review progress. Comments are textual notes (Pending / No Action Needed / Resolved) that record specific issues and suggestions. A typical usage pattern: mark a code block as "Issues", then add a comment explaining the specific reason.

### What are floating comments?

When a comment's associated code block changes or is deleted after a branch update, the comment becomes a "floating comment". Floating comments are displayed with a semi-transparent style in the UI. You can still view the comment content and the original code at the time of creation. Floating comments that are no longer needed can be manually deleted.

### What are IDE Inspection Rules (Platform Error/Warning)?

These three rules leverage IDEA's built-in code inspection capabilities to analyze newly added code. They invoke all inspection tools loaded in IDEA (including inspections registered by third-party plugins such as SonarLint), running them on new code blocks and reporting issues. If you have code inspection plugins like SonarLint installed, their findings may also be captured by auto review.

### Do Spring rules require additional configuration?

No. Spring rules work out of the box in IntelliJ IDEA. The plugin analyzes Spring annotations and Bean definitions in your project to build the dependency graph — no Spring Boot plugin or runtime environment is needed.

### Does the plugin affect performance?

The impact is minimal. Diff computation uses the Git command line, database operations are based on lightweight SQLite, and the UI only loads when the tool window is open. The analysis caches used by PSI semantic analysis rules (Spring, Code Defect, Redis, etc.) exist only during auto review execution and are automatically cleared afterward. Batch database operations and asynchronous loading ensure the plugin won't slow down IDEA.

### Does AI Review require an internet connection?

Yes. AI Review invokes the configured AI CLI, which connects to the corresponding API server (Anthropic for Claude Code, OpenAI for Codex). The plugin itself (MCP Server and database) runs entirely locally — only the CLI subprocess makes outbound API requests.

### Does AI Review incur API costs?

Yes. AI Review consumes API tokens from the provider you choose (Anthropic for Claude Code, OpenAI for Codex), which incur charges. Actual costs depend on code volume and the model selected — typically $0.01–$0.50 per review session. The output dialog shows the total cost for each completed session.

### How long does AI Review take?

It depends on code volume and the number of enabled experts. A session with 20–50 files typically takes 5–15 minutes with all three experts running in parallel. The plugin provides adaptive timeout (5 minutes per 50 files) and you can also set a manual timeout in settings.

### What's the difference between AI Review and Auto Review?

| Dimension | Auto Review | AI Review |
|-----------|-------------|-----------|
| Implementation | Predefined rules, static analysis | AI large model inference |
| Speed | Seconds | Minutes |
| Understanding | Pattern matching, no context | Understands semantics and business logic |
| Coverage | Fixed rule set | Flexible, discovers novel issues |
| Cost | Free | Incurs API charges |
| Recommended order | Run first, quickly filter noise | Run second, deep-dive into standards and security |

### What's the difference between AI Auto-Fix and AI Review?

AI Review **finds** issues; AI Auto-Fix **resolves** them. The two are triggered independently. A typical flow: AI Review scans and flags problems → you confirm which ones are safe to auto-fix → AI Auto-Fix applies the changes → you verify the result before committing.

### Will AI Auto-Fix modify my files directly?

Yes, AI Auto-Fix writes changes directly to local source files. We recommend ensuring your working tree is clean (or stashed) before running it so you have a rollback point. Always review and verify the AI's changes before committing.

### Which is better — Codex CLI or Claude Code CLI?

Both are capable. Claude Code generally has stronger autonomous tool-use and code reasoning; Codex is a natural fit if you already have an OpenAI API key. Choose based on your team's existing API access, and feel free to mix them (e.g., Claude for review, Codex for auto-fix).

### AI Review says "branch mismatch" — what do I do?

AI Review validates that the current Git branch matches the review session's branch. If they don't match, switch to the session's branch with `git checkout <review-branch>` or via IDEA's Git toolbar, then trigger AI Review again.

### AI Review says the CLI is not found — what do I do?

1. Run `claude --version` (or `codex --version`) in a terminal to verify the command is available. If it fails, the CLI is not yet set up — follow the respective installation guide
2. If the terminal works but the plugin validation fails, IDEA's `PATH` likely differs from your shell's. Set the "Start Command" in settings to the full binary path (e.g., `/usr/local/bin/claude` or `/usr/local/bin/codex`)

---

## License & Feedback

**Code Review Plus** &copy; 2026 Zero. All Rights Reserved.

This plugin is proprietary software. See the LICENSE file for detailed terms.

### Feedback

If you encounter issues or have suggestions, feel free to reach out:

- Email: zero_feedback@163.com

When reporting issues, please include your IDEA version, plugin version, OS information, and steps to reproduce the problem. Error logs can be obtained via `Help` → `Show Log in Finder/Explorer`.

### Third-Party Components

This software uses the following open-source components:

- [Carbon Icons](https://github.com/carbon-design-system/carbon) (Apache 2.0) - UI icons
- [IntelliJ Platform SDK](https://plugins.jetbrains.com/docs/intellij/welcome.html) (Apache 2.0) - Plugin development framework
- [SQLite JDBC](https://github.com/xerial/sqlite-jdbc) (Apache 2.0) - Database driver

---

<div align="center">

**If you find this plugin helpful, please leave a rating on the Marketplace**

Made with care by Zero

</div>
