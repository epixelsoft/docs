# Install the App Documentation Design

**Date:** 2026-07-31

## Objective

Add one task-focused Mintlify page to **Get Started** that explains how Managers and Field Officers can install the Terriqon Progressive Web App on iPhone, iPad, and Android devices.

## Content design

Create `install-the-app.mdx` with concise frontmatter, a short explanation of the PWA experience, and a preparation callout covering the initial internet requirement, supported roles, and sign-in details.

Structure the page into four sections:

1. **Install on iPhone or iPad** — use Safari, open the Terriqon app URL, use the Share menu, add the app to the Home Screen, enable **Open as Web App** when shown, and launch Terriqon from its icon.
2. **Install on Android** — use Chrome or another Chromium-based browser, follow the installation prompt or browser menu, confirm installation, and launch Terriqon from the Home screen or app drawer.
3. **Updates** — explain that updates load automatically when the installed app is opened online and provide a restart tip.
4. **Troubleshooting** — provide concise resolutions for missing iOS or Android installation controls and startup problems.

Use Mintlify `<Steps>` components for both installation procedures, `<Note>` for prerequisites, and `<Tip>` for update recovery. Use active voice, second person, sentence-case headings, and bold interface labels. Use `Organization Admin` to match existing terminology. Link directly to `https://app.terriqon.com`.

## Navigation

Add `install-the-app` to the **Get Started** pages array in `docs.json`, positioned immediately after `quickstart` and before `how-it-works`.

## Validation

- Confirm `docs.json` remains valid JSON.
- Confirm the Get Started navigation order is exact.
- Confirm the new page has valid frontmatter and balanced Mintlify component tags.
- Confirm the Terriqon app URL is a valid HTTPS link.
- Confirm every Get Started navigation target resolves to an MDX file.
- Review the branch diff to ensure only the approved page, navigation entry, and planning records changed.
