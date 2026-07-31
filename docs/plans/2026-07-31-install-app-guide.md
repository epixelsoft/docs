# Install the App Guide Implementation Plan

> **For Antigravity:** REQUIRED WORKFLOW: Use `.agent/workflows/execute-plan.md` to execute this plan in single-flow mode.

**Goal:** Publish a Mintlify guide that helps Terriqon Managers and Field Officers install and maintain the Progressive Web App on iOS, iPadOS, and Android devices.

**Architecture:** Add one standalone root-level MDX page using Mintlify steps and callouts. Register the page in the existing Get Started navigation, then validate the JSON, MDX structure, links, page targets, and branch scope before opening a draft pull request.

**Tech Stack:** Mintlify, MDX, JSON, Node.js, Git, GitHub

---

### Task 1: Create the installation guide

**Files:**
- Create: `install-the-app.mdx`

**Step 1: Verify the page does not exist**

Run: `test ! -e install-the-app.mdx`

Expected: exit code 0.

**Step 2: Add page frontmatter and introduction**

Use:

```mdx
---
title: "Install the Terriqon App"
sidebarTitle: "Install the App"
description: "Install the Terriqon Progressive Web App on iPhone, iPad, or Android, keep it updated, and resolve common installation issues."
---
```

Explain that Terriqon is a PWA installed from a browser, launches from its own icon, opens without the browser interface, and supports offline fieldwork after initial setup.

**Step 3: Add prerequisites**

Use a `<Note>` component to state that the first installation requires internet access, the app is intended for Managers and Field Officers, Organization Admins use the web dashboard, and users should have their sign-in details ready.

**Step 4: Add iOS and iPadOS steps**

Use one `<Steps>` component that instructs the user to open Safari, visit [app.terriqon.com](https://app.terriqon.com), open the Share menu, select **Add to Home Screen**, enable **Open as Web App** when shown, select **Add**, and launch Terriqon from the Home Screen.

**Step 5: Add Android steps**

Use one `<Steps>` component that instructs the user to open Chrome or another Chromium-based browser, visit the app URL, use the install prompt or **⋮ → Install app** / **Add to Home screen**, confirm with **Install**, and launch Terriqon from the Home screen or app drawer.

**Step 6: Add updates and troubleshooting**

Explain automatic updates without promising a specific delivery interval. Add a `<Tip>` advising users to close and reopen the app while online. Add concise troubleshooting bullets for missing iOS or Android installation controls and blank startup screens.

**Step 7: Commit**

Run:

```bash
git add install-the-app.mdx
git commit -m "docs: add Terriqon app installation guide"
```

### Task 2: Register the page in Get Started

**Files:**
- Modify: `docs.json`

**Step 1: Confirm the navigation path is absent**

Run: `node -e 'const c=require("./docs.json");const g=c.navigation.tabs.flatMap(t=>t.groups).find(x=>x.group==="Get Started");if(g.pages.includes("install-the-app"))process.exit(1)'`

Expected: exit code 0.

**Step 2: Add the page in the exact position**

The Get Started pages array must be:

```json
[
  "introduction",
  "quickstart",
  "install-the-app",
  "how-it-works"
]
```

**Step 3: Validate JSON**

Run: `node -e 'JSON.parse(require("fs").readFileSync("docs.json","utf8"));console.log("docs.json valid")'`

Expected: `docs.json valid`.

**Step 4: Commit**

Run:

```bash
git add docs.json
git commit -m "docs: add install guide to navigation"
```

### Task 3: Validate and publish

**Files:**
- Verify: `install-the-app.mdx`
- Verify: `docs.json`
- Modify: `docs/plans/task.md`

**Step 1: Validate MDX and navigation structure**

Run a Node.js validation that confirms:

- frontmatter includes `title`, `sidebarTitle`, and `description`
- iOS, Android, Updates, and Troubleshooting headings exist
- two `<Steps>` wrappers and all `<Step>` tags are balanced
- `<Note>` and `<Tip>` tags are balanced
- `https://app.terriqon.com` appears as a link
- Get Started contains the exact four-page order
- every Get Started page resolves to an `.mdx` file

Expected: all checks pass with exit code 0.

**Step 2: Check formatting and scope**

Run:

```bash
git diff --check origin/main...HEAD
git diff --stat origin/main...HEAD
```

Expected: no whitespace errors; changes are limited to the new guide, one navigation entry, and planning records.

**Step 3: Complete the tracker**

Mark all install-app guide rows in `docs/plans/task.md` as `Completed` after validation passes.

**Step 4: Push and open a draft pull request**

Push `codex/install-app-guide` to `origin` and open a draft PR targeting `main`. The PR body must summarize the content, user impact, and fresh validation evidence.
