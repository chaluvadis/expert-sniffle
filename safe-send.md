You are a senior VS Code extension engineer.

You are extending an existing VS Code extension:

# **Safe Send (V1)**

---

# 🎯 V2 OBJECTIVE

Extend Safe Send V1 into:

# **Safe Send Pro (V2)**

V2 MUST:

* preserve ALL V1 behavior exactly
* add new event-driven safety layer
* introduce risk scoring system
* remain deterministic and minimal

V2 MUST NOT:

* change V1 command behavior
* remove or modify V1 UX flows
* introduce breaking architectural changes

---

# 🧱 BASE SYSTEM (INHERITED FROM V1)

V1 already includes:

### Command:

> Safe Send: Scan & Copy for AI

### Behavior:

* scan selected text or full file
* detect sensitive data via regex
* if clean → copy automatically
* if risky → show UI with:

  * Sanitize & Copy
  * Copy Anyway
  * Cancel

👉 THIS MUST REMAIN EXACTLY THE SAME.

---

# 🚀 V2 EXTENSION: SAFE SEND PRO

V2 adds **NON-BREAKING enhancements only**.

---

# ⚙️ NEW FEATURE 1: EVENT-DRIVEN SAFETY LAYER

## Monitored events:

* copy events (primary)
* selection change events (pre-analysis only)

---

## Copy Event Behavior (NEW LOGIC)

When a copy event occurs:

### Step 1: Capture copied text

### Step 2: Run Risk Engine (see below)

### Step 3: Decision logic:

* If risk = LOW:
  → DO NOTHING (silent pass-through)

* If risk = MEDIUM or HIGH:
  → Show warning (non-blocking UI)

---

## WARNING UI (V2 ONLY)

```plaintext id="v2warn1"
⚠️ Safe Send Pro Alert

Risk Score: 72/100 (HIGH)

Detected:
• API Key
• Internal IP

Actions:
[Sanitize Clipboard]
[Allow Copy]
[Ignore for this file]
```

---

## IMPORTANT RULES

* MUST NOT block copy action
* MUST NOT interfere with V1 command behavior
* MUST remain async and fast (<50ms target)
* MUST be silent for LOW risk

---

# 🧠 NEW FEATURE 2: RISK SCORING ENGINE (DETERMINISTIC)

V2 introduces a scoring system used ONLY in event layer and V1 UI decision layer.

---

## Output format:

```ts id="v2risk1"
{
  score: number,
  level: "LOW" | "MEDIUM" | "HIGH",
  findings: string[]
}
```

---

## Base scoring rules:

| Pattern                | Score |
| ---------------------- | ----- |
| OpenAI API key         | +40   |
| AWS key                | +40   |
| JWT token              | +25   |
| IP address             | +15   |
| Email                  | +10   |
| password/secret inline | +35   |

---

## Context modifiers:

| Context               | Adjustment |
| --------------------- | ---------- |
| `.env` file           | -10        |
| `README.md`           | +10        |
| `/test/` path         | -15        |
| multiple secret types | +20        |
| >3 findings           | +15        |

---

## Classification thresholds:

* 0–29 → LOW
* 30–59 → MEDIUM
* 60–100 → HIGH

---

## RULE:

Scoring MUST be deterministic (no randomness, no ML).

---

# 🧼 NEW FEATURE 3: SANITIZATION ENGINE (SHARED WITH V1)

Same rules as V1, reused here:

Replace:

* API key → `<API_KEY>`
* AWS key → `<AWS_KEY>`
* JWT → `<JWT_TOKEN>`
* IP → `<IP_ADDRESS>`
* Email → `<EMAIL>`
* secret/password → `<SECRET>`

Rules:

* Preserve code structure
* Only replace matched values
* No formatting changes

---

# 🧱 ARCHITECTURE (V1 + V2 COMBINED)

V2 MUST extend V1 structure, NOT replace it.

---

## Required modules:

### 1. extension.ts

* registers V1 command
* registers V2 event layer
* acts as glue only

---

### 2. riskEngine.ts (NEW)

* regex detection
* scoring logic
* classification output

---

### 3. eventManager.ts (NEW)

* copy event handler
* selection pre-scan
* calls risk engine

---

### 4. sanitizer.ts (SHARED)

* used by both V1 and V2 flows

---

## FLOW MODEL

### V1 flow (UNCHANGED):

```text id="v1flow"
Command → Scan → Decision → Copy/Sanitize
```

---

### V2 flow (NEW):

```text id="v2flow"
Copy Event → Risk Engine → Decision → Warning UI (if needed)
```

---

# 🧾 UX RULES (GLOBAL)

* V1 UX MUST remain unchanged
* V2 UX must be non-blocking
* No settings UI
* No configuration system
* No background noise for LOW risk
* Minimal notifications only

---

# 🧱 TECH STACK (STRICT)

* TypeScript only
* VS Code Extension API
* pnpm package manager
* Node 24 development environment assumption
* Biome.js for linting + formatting
* No ESLint or Prettier
* No external dependencies
* No AI/ML models

---

# 🚫 NON-GOALS (CRITICAL)

Do NOT:

* modify V1 command behavior
* introduce breaking architectural changes
* add AI integrations
* add telemetry or analytics
* build enterprise DLP system
* block clipboard operations
* over-engineer module structure

---

# 🎯 SUCCESS CRITERIA

V2 is successful if:

* V1 works exactly as before
* Copy events trigger risk evaluation
* LOW risk = zero friction
* MEDIUM/HIGH risk = warning UI only
* Risk scoring is deterministic and explainable
* System remains simple and readable (<15 min understanding)

---

# 🔁 POST-GENERATION SELF-REVIEW (MANDATORY)

After generating code:

1. Verify V1 behavior is unchanged
2. Ensure V2 is additive only
3. Confirm no blocking copy behavior
4. Simplify event system if over-engineered
5. Ensure risk engine is deterministic
6. Inline logic where possible

Output a simplified final version.
