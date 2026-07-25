# Manage Login Details Documentation Design

**Date:** 2026-07-25

## Objective

Add one task-focused Mintlify page under **Account & Billing** that helps Terriqon users change their password, change their registered email address, or reset a forgotten password.

## Content design

Create `account/manage-login-details.mdx` with concise frontmatter, a short introduction, and three clearly separated procedures:

1. **Change your password** — open the profile page from the profile picture, select **Change Password**, enter the current and new passwords, save the change, and sign in again.
2. **Change your registered email address** — open the profile page, select **Change Email**, confirm the current password, request an OTP for the new email address, verify the OTP, and sign in again with the new email address and existing password.
3. **Reset a forgotten password** — select **Forgot password?** on the sign-in page, submit the registered email address, open the reset link from the email, set and save a new password, and sign in with it.

Use Mintlify `<Steps>` components for all procedures, bold interface labels, and notes that make sign-out and reauthentication outcomes explicit. Avoid unsupported claims about OTP or reset-link expiration times.

## Navigation

Add `account/manage-login-details` to the **Account & Billing** page list in `docs.json`, positioned before pricing and subscription content because account access is a foundational account task.

## Validation

- Confirm `docs.json` remains valid JSON.
- Confirm the new MDX page has valid frontmatter and balanced Mintlify component tags.
- Confirm every page referenced by the Account & Billing navigation exists.
- Review the branch diff to ensure only the approved page, navigation entry, and planning records changed.
