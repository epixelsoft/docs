# Manage Login Details Documentation Implementation Plan

> **For Antigravity:** REQUIRED WORKFLOW: Use `.agent/workflows/execute-plan.md` to execute this plan in single-flow mode.

**Goal:** Publish one Mintlify page that explains how Terriqon users can change their password, change their registered email address, and reset a forgotten password.

**Architecture:** Add a standalone task-focused MDX page beneath the existing Account & Billing content. Register that page in `docs.json` so Mintlify includes it in navigation, then validate the JSON, frontmatter, navigation target, and component structure before opening a draft pull request.

**Tech Stack:** Mintlify, MDX, JSON, GitHub

---

### Task 1: Create the login-details page

**Files:**
- Create: `account/manage-login-details.mdx`

**Step 1: Add frontmatter**

Use the title `Manage Your Terriqon Login Details`, sidebar title `Login Details`, and a concise description covering password changes, registered-email changes, and password resets.

**Step 2: Add the three procedures**

Use separate level-two headings and Mintlify `<Steps>`/`<Step>` components for:

- Change your password
- Change your registered email address
- Reset a forgotten password

Use bold interface labels, identify which credentials remain unchanged, and explicitly state when Terriqon redirects the user to the sign-in page.

**Step 3: Review the copy**

Check that each instruction begins with an action, uses consistent terms (`sign-in page`, `registered email address`, and `one-time password (OTP)`), and makes no unsupported claims about expiry times.

**Step 4: Commit**

Commit message: `docs: add login details guide`

### Task 2: Register the page in Mintlify navigation

**Files:**
- Modify: `docs.json`

**Step 1: Add the navigation path**

Insert `account/manage-login-details` as the first page in the `Account & Billing` group.

**Step 2: Validate JSON**

Parse the updated file as JSON and confirm the Account & Billing pages array contains the new path exactly once.

**Step 3: Commit**

Commit message: `docs: add login guide to navigation`

### Task 3: Validate the documentation change

**Files:**
- Verify: `account/manage-login-details.mdx`
- Verify: `docs.json`

**Step 1: Validate page structure**

Confirm the MDX file begins and ends its frontmatter with `---`, includes all required frontmatter keys, and has three opening and closing `<Steps>` tags with balanced `<Step>` tags.

**Step 2: Validate navigation**

Confirm `docs.json` parses and every Account & Billing navigation path resolves to an existing `.mdx` file.

**Step 3: Inspect the branch diff**

Compare `codex/manage-login-details` with `main` and confirm the product change is limited to the new page and its navigation entry, with planning records stored only under `docs/plans/`.

### Task 4: Publish for review

**Files:**
- Update: `docs/plans/task.md`

**Step 1: Mark the tracker complete**

Update the task tracker only after all validation checks pass.

**Step 2: Open a draft pull request**

Target `main` from `codex/manage-login-details`. Summarize the new guide, explain its user benefit, and include the validation evidence.
