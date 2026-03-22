[🎉🎉 Get Discount Code 🎉🎉](https://github.com/aGVsbG8gd29ybGQh/code-review-plus/issues/1)

# Code Review Plus - Intelligent Code Review Assistant

<div align="center">

![Plugin Icon](images/pluginIcon.svg)

**Dedicated to making code reviews easier**

An IntelliJ IDEA plugin that helps you review code efficiently with session management, incremental review, automated rules, and a comment system

[![Version](https://img.shields.io/badge/version-3.5.0-blue.svg)](https://plugins.jetbrains.com/plugin/29361-code-review-plus)
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
- [Report Export & Import](#report-export--import)
- [Plugin Settings](#plugin-settings)
- [Best Practices](#best-practices)
- [FAQ](#faq)
- [License & Feedback](#license--feedback)

---

## Why Code Review Plus

Common pain points during code reviews:

- **Interrupted mid-review** — you come back and can't remember what you've already reviewed
- **New commits on the branch** — unsure if your previous review is still valid, so you start over
- **Too many changed files** — you want to review in batches but have no way to track progress
- **Want to flag issues** — but don't want to clutter the PR with scattered comments
- **Noise from trivial changes** — import reordering, code formatting, blank line adjustments... these mix in with real business logic, forcing you to manually verify each one is "fine", wasting review time on noise

Code Review Plus solves these problems simply: **track review progress directly in IDEA, and use automated rules to filter out noise**.

Every code block you've reviewed, every status you've marked, every comment you've written is automatically saved locally. When the branch updates, the system intelligently identifies what changed and what didn't — you only need to focus on new and modified code. For trivial changes like import adjustments and formatting, as well as obvious issues like hardcoded secrets and leftover debug code, auto review rules handle them in one click, letting you spend your time on code that actually requires thought.

### Who Should Use This

**Developers**: Use it for self-review before submitting code to testers or reviewers. Create a review session, check your own changes one by one — you can even review as you develop, marking off sections as you complete them to avoid missing details in a final bulk review.

**Reviewers**: When facing a large number of changed files, use auto review to filter out noise first, then review in batches with progress saved at all times. Write comments directly on issues you find. After review, export a report and send it to the developer, who can view and fix issues one by one in their own IDEA — no back-and-forth communication needed.

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

### Report Export & Import

Export review results as an HTML report containing review progress, code diffs, and all comments. The report can be sent to the branch developer, who can import it directly into their own IDEA to view the reviewer's comments and fix issues one by one.

Recommended collaboration workflow: **Reviewer flags issues → Exports report → Developer imports report → Reviews comments and fixes → Notifies reviewer to confirm**, forming a closed-loop review process.

---

## Free & Paid

Code Review Plus uses a Freemium model: **only the Auto Review feature requires a license**. All other features (session management, status tracking, incremental review, comment system, report export & import, etc.) are free to use.

Our commitment: **existing free features will always remain free, with no license restrictions added in the future**. You can use them with confidence.

The Auto Review feature comes with a 30-day trial period automatically activated upon installation from JetBrains Marketplace. After the trial expires, you can purchase a license on the Marketplace to continue using it. If you'd like an extended trial period, please contact us by email with your reason, and we'll consider providing a free license.

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
| <img src="images/run.svg" width="16" height="16"> | Auto Review | Run auto review rules on the current session |
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

Recursively analyzes the call chain of `@Transactional` methods (up to 5 levels deep) for network I/O operations that hold the database connection longer than necessary:

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

---

## Best Practices

### Daily Review Workflow

**Recommended workflow**:

1. **Create session** → Select the feature branch and master/develop branch
2. **Run auto review** → Let rules automatically handle whitespace, import, and other trivial changes
3. **Review file by file** → Start with unreviewed files, double-click to open the Diff view
4. **Mark status + write comments** → Mark passing code as Passed, flag issues as Issues with comments
5. **Refresh periodically** → Refresh when the branch has new commits, focus only on changes
6. **Export report** → After review, export for archiving or send to the developer for import

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
