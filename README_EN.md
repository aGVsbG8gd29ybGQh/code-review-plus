# Code Review Plus

<div align="center">

**An IntelliJ IDE plugin designed to improve code review efficiency**

Manage review sessions, track states, perform incremental reviews, and use an integrated comment system to make branch reviews simple and efficient.

[![Version](https://img.shields.io/badge/version-2.0.1-blue.svg)](https://plugins.jetbrains.com/plugin/XXXXX)
[![IDEA Version](https://img.shields.io/badge/IDEA-2025.2+-orange.svg)](https://www.jetbrains.com/idea/)
[![License](https://img.shields.io/badge/license-Proprietary-red.svg)]()

</div>

---

## 📖 Table of Contents

- [Features](#-features)
- [Key Benefits](#-key-benefits)
- [Quick Start](#-quick-start)
- [User Guide](#-user-guide)
- [Use Cases](#-use-cases)
- [Architecture](#-architecture)
- [Feedback](#-feedback)

---

## ✨ Features

### 1 Session Management

Review progress is saved locally and supports:

- 💾 **Auto-save** - Persist state changes in real time
- 🔄 **Session restore** - Automatically restore the last active session after IDEA restarts
- 📁 **Multi-project support** - Manage multiple Git projects within the same IDEA instance
- 📊 **Multiple concurrent sessions** - Manage multiple review branches at the same time

---

### 2 State Tracking

Mark the review state for each diff block. Three states are supported:

- 🔲 **Unreviewed** - Changes pending review
- ✅ **Approved** - No issues found
- ⚠️ **Problem** - Requires attention or modification

---

### 3 Incremental Review Support

When the branch is updated, the plugin intelligently merges old and new diffs and preserves reviewed states so you only need to review newly added or changed code.

Smart matching strategies:
- ✅ **Exact match** - Same position and content; keep review state
- 🔄 **Fuzzy match** - Content changed but traceable; keep comments but reset state
- ➕ **New detection** - Automatically identify newly added blocks
- ➖ **Deletion handling** - Clean up deleted blocks

---

### 4 Diff View Enhancements

Mark review state directly in IDEA's native Diff view for seamless workflow integration:

- 🎨 **Gutter icons** - Show state icons beside line numbers
- 🖱️ **One-click toggle** - Click the icon to cycle states (Unreviewed → Approved → Problem)
- 🌈 **Background highlight** - Confirmed blocks are shown with a light green background
- 💬 **Tooltips** - Hover to see detailed information about a diff block

---

### 5 Visual Review Panel

A graphical interface to improve review efficiency:

- 🌲 **Tree file list** - Hierarchical view of changed files
- 🏷️ **State icons** - Visual display of review state and change type
- 🔍 **Smart filters** - Filter by state (Unreviewed/Approved/Problem) or by comment state (Pending/Resolved/Not applicable)
- 📈 **Progress stats** - Real-time review completion and comment handling stats
- ⚡ **Bulk actions** - Support file-level bulk state updates

---

### 6 Code Commenting System

A complete commenting capability for code reviews with issue tagging and tracking:

- 💬 **Add comments in the Diff window** - Right-click to add a comment on any line
- 🎨 **Visual comment icons** - Gutter area shows stateful icons (Pending/Not applicable/Resolved)
- 📝 **Smart comment panel** - View comments, change state, and show original code context
- 🔄 **Floating comment mechanism** - Comments persist after code changes and are shown semi-transparent
- 📋 **Comment list view** - Manage all comments grouped by file with filtering and bulk actions
- 🎯 **Precise navigation** - Double-click a comment to jump to its position in the Diff window

Comment states:
- 🔵 **Pending** - Issues or suggestions that need attention
- ✓ **Not applicable** - Confirmed that no change is required
- ● **Resolved** - Issue has been addressed

Smart features:
- Support single-line and multi-line range comments
- Comment text up to 500 characters with live character count
- Replay original code at comment creation time using Git history
- Bulk update comment states for efficient progress management

---

## 🎯 Key Benefits

### 🚀 Avoid Repeated Reviews

When the reviewed branch receives new commits, the plugin will intelligently identify:
- ✅ Which code has already been reviewed (state preserved)
- 🆕 Which code is new or modified (marked Unreviewed)

Avoid duplicate work and focus on the changes that truly need attention.

---

### 💾 Persistent State

Review progress is saved in a local database in real time:
- No more worry about losing progress if IDEA crashes
- No worry about accidentally closing the tool window
- Support cross-session restoration of review state

---

### 🎨 Native Experience

Fully integrated with IDEA's native Diff view:
- No context switching; keep familiar workflows
- Support all Diff view shortcuts
- Automatically follow IDEA themes (Dark/Light)

---

### 💬 Enhanced Comment Collaboration

A professional comment system for more efficient issue tracking:
- Add detailed comments to diff blocks to record issues and suggestions
- Three state management (Pending/Not applicable/Resolved) to track progress clearly
- Floating comments persist after code changes
- Comment list view centralizes comment management
- Original code replay allows viewing the context when the comment was made even if the code changed

---

## 🚀 Quick Start

### Step 1: Open the tool window

Open the tool window via any of the following:

- Menu: `View` → `Tool Windows` → `Code Review Plus`
- Sidebar: Click the `Code Review Plus` icon on the left toolbar

---

### Step 2: Create a review session

1. Open the "Start Review" dialog:
   - Menu: `Tools` → `Code Review Plus` → `Start Review...`
   - Project context menu: `Code Review Plus` → `Start Review...`
   - Tool window: Click the `+` button in the toolbar
2. In the dialog select:
   - **Review branch**: the feature branch to review (e.g. `feature/user-login`)
   - **Base branch**: the target branch to compare against (e.g. `master` or `develop`)
3. Click **OK** to create the session

Tips:
- Both review and base branches must be pushed to the remote
- The system will automatically check branch relationships and show warnings

---

### Step 3: Start reviewing

1. **Browse the file list**: view all changed files in the tool window
2. **Open Diff view**: double-click a file to open its diff
3. **Mark review state**: click the icon next to the line number to toggle state
   - 🔵 Unreviewed → ✅ Approved → ⚠️ Problem → 🔵 Unreviewed (cycle)
4. **Check progress**: the bottom status bar shows real-time review statistics

---

### Step 4: Add comments (optional)

Add comments to mark issues and suggestions:

1. **Right-click in the Diff view and select "Add Comment"**
2. **Enter the comment and save** (up to 500 characters)
3. **Click the comment icon to view and manage comments**
4. **Use the comment list view for centralized management** (toolbar "Toggle View")

Tip: See the [User Guide - Comment System](#code-commenting-system) for detailed instructions.

---

### Step 5: Incremental refresh

When the review branch receives new commits:

1. Click the **Refresh** button in the toolbar
2. The system will:
   - Recompute the diff
   - Preserve reviewed states and comments
   - Mark newly added/changed code as "Unreviewed"
3. Continue reviewing the new or changed code

---

## 📖 User Guide

### Toolbar actions

| Icon | Action | Shortcut | Description |
|------|--------|----------|-------------|
| ➕ | Start Review | - | Create a new review session |
| 🔄 | Refresh Session | - | Incrementally update the current session |
| 🗑️ | Delete Session | - | Delete the current session and all data |
| ❌ | Close Session | - | Close the session but keep its data |
| 🔀 | Toggle View 🆕 | - | Switch between Diff Block list and Comment list |
| 🔍 | Filter | - | Filter files by state or change type |
| 📂 | Expand All | - | Expand all folders |
| 📁 | Collapse All | - | Collapse all folders |

---

### File tree icons

#### Change type icons

- 🆕 **Green plus** - New file
- 📝 **Blue edit** - Modified file
- 🗑️ **Red trash** - Deleted file
- 🔄 **Purple arrow** - Renamed file

#### Review state icons

- 🔵 **Blue dot** - Unreviewed
- ✅ **Green check** - Approved
- ⚠️ **Orange warning** - Problem

#### Comment state icons 🆕

Diff Gutter area:
- 💬 **Speech bubble** - Pending comment
- ✓ **Check** - Not applicable comment
- ● **Dot** - Resolved comment
- 🌫️ **Semi-transparent** - Floating comment (associated code no longer exists)

Comment list view:
- 🔵 **Blue todo** - Pending
- 🟠 **Orange warning** - Not applicable
- 🟢 **Green check** - Resolved
- 🌫️ **Gray text** - Floating comment

---

### State filters

Use the toolbar filter dropdown to quickly locate files and comments:

Diff Block list view:
- **All** - Show all files
- **Unreviewed** - Show only unreviewed files
- **Approved** - Show only approved files
- **Problem** - Show only files with issues

Comment list view:
- **Filter by comment state**: Pending, Not applicable, Resolved
- **Filter by change type**: New, Modified, Deleted, Renamed
- **Filter rule**: A file is shown if it contains any comment matching the selected criteria

---

### Stats panel

The bottom stats panel shows real-time information like:

```
Review progress: 45/120 blocks (37.5%)
  ✅ Approved: 40
  ⚠️ Problems: 5
  🔵 Unreviewed: 75
```

- **Total blocks** - Number of diff blocks in the current session
- **Approved** - Number of blocks marked Approved
- **Problems** - Number of blocks marked Problem
- **Unreviewed** - Number of blocks not yet reviewed

---

## 🎯 Use Cases

### ✅ Recommended scenarios

1. **Feature branch reviews**
   - Review code before merging into the main branch
   - Ensure code quality meets team standards

2. **Large branch reviews**
   - Many files changed and reviews can be split into smaller batches
   - Avoid missing issues from a single bulk review

3. **Continuously updated branches**
   - Branches that receive new commits during the review process
   - Use incremental review to avoid repeating work

4. **Internal team reviews**
   - Individual reviewers mark states for later team discussion and traceability

---

## 🏗️ Architecture

### Core stack

- **Language**: Kotlin 1.9+
- **Build tool**: Gradle 8.5+ (Kotlin DSL)
- **Platform SDK**: IntelliJ Platform SDK 2025.2

**Privacy**: All data is stored locally and is not uploaded to any server.

---

## 🐛 Feedback

### Found an issue?

If you encounter any problems while using the plugin, please provide feedback via:

1. **Email**: zero_feedback@163.com
2. **Plugin reviews**: Leave a comment on the JetBrains Marketplace plugin page

---

### What to include in feedback

To help resolve issues faster, please include:

- **IDEA version**: the version from `Help` → `About`
- **Plugin version**: the version from `Settings` → `Plugins`
- **OS**: Windows / macOS / Linux and the version
- **Description**: detailed steps to reproduce the issue
- **Error logs**: `Help` → `Show Log in Finder/Explorer`

---

## 📄 License

**Code Review Plus** © 2026 Zero. All Rights Reserved.

This plugin is proprietary. See the [LISENSE](https://github.com/aGVsbG8gd29ybGQh/code-review-plus/blob/main/LISENSE) file for full license terms.

### Restrictions

Unauthorized actions are prohibited:
- Reverse engineering or decompilation
- Modification or redistribution
- Removal of copyright notices

### Third-party components

This software uses some open-source components, including:
- Carbon Icons (Apache 2.0) - plugin icons
- IntelliJ Platform SDK (Apache 2.0) - development framework
- SQLite JDBC (Apache 2.0) - database driver

---

## 🙏 Acknowledgements

Thanks to the following projects and technologies:

- [IntelliJ Platform SDK](https://plugins.jetbrains.com/docs/intellij/welcome.html)
- [Kotlin](https://kotlinlang.org/)
- [SQLite](https://www.sqlite.org/)
- [Git](https://git-scm.com/)

---

<div align="center">

**If you find this plugin useful, please consider leaving a positive review on the Marketplace! ⭐**

Made with ❤️ by Zero

</div>
