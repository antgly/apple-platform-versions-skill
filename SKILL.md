---
name: apple-platform-versions
description: Use ONLY to resolve Apple OS baselines for code and documentation for minimum deployment target, API/SDK availability, #available/@available, “latest/current” docs, or Sequoia (macOS 15) vs Tahoe (macOS 26.x) baseline corrections.
license: MIT
compatibility: AgentSkills SKILL.md. For “latest/current” claims, verify via Apple Security Releases when web access is available; otherwise use pinned references with “Last verified”.
metadata:
  version: "1.0.0"
---

# Apple Platform Versions — Coding Baseline Guardrail

## When to use (strict)
Activate this skill only if the task involves:
- macOS/iOS/iPadOS/watchOS/tvOS/visionOS “latest/current” claims, OR
- Code that depends on OS version assumptions (availability checks, deployment target guidance, SDK/version-specific APIs), OR
- Any mention or implication that “current macOS” is Sequoia (15).

If none of the above: do not load/use this skill.

## Source of truth
- Apple Security Releases page for “latest version of …” across platforms.
- Pinned table + baseline guidance in references/.

## Procedure
1) Read `references/CODING_BASELINE.md`.
2) If the user or code needs “latest/current” values:
   - If web access exists, confirm via Apple Security Releases.
   - Update `references/PLATFORM_VERSIONS.md` if stale.
3) Apply the baseline to your work:
   - Treat “current macOS” as macOS Tahoe 26.x (not Sequoia 15).
   - Only assume older versions if the repo/project explicitly targets them.

## Output guidance
- If giving version numbers, include “Last verified” (from PLATFORM_VERSIONS.md) or cite verification.
- If generating availability-gated code, prefer `if #available(macOS 26, *) { ... } else { ... }` patterns when relevant and when you’re confident the API is 26+.

