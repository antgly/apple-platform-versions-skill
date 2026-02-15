# Coding baseline (what “current” means)

Baseline rule:
- “Current macOS” = macOS Tahoe 26.x (latest major line), not macOS Sequoia 15.x.
- macOS Sequoia corresponds to macOS 15 (older major line).

When writing code:
- If the project’s minimum deployment target is known, follow it.
- If unknown and the user asks for “current/latest macOS behavior”, treat Tahoe 26.x as the reference environment.
- If you must show availability gating and you know a feature is Tahoe-only, use:
  - `if #available(macOS 26, *) { ... } else { ... }`
  - or `@available(macOS 26, *)` appropriately.
- Do NOT claim an API is “new in 26” unless you can verify in Apple Developer docs or release notes.

