## Sequential Execution Plan: Kilocode Gastown Mayor

You are responsible for improving the Kilocode Gastown Mayor extension. All tasks must be executed **strictly one at a time, in sequence**, with no parallel work.

---

### Execution Rules
- Do NOT proceed to the next step until the current step is fully completed and validated.
- Do NOT skip any steps.
- Maintain clear checkpoints between each phase.
- Treat this workflow as a strict pipeline.

---

### Step 1: Codebase Analysis
- Checkout and use the `staging` branch as the base.
- Perform a full analysis of the codebase.
- Understand:
  - Architecture and structure
  - Core functionality and workflows
  - Purpose and design of the extension
- Identify gaps and developer pain points in the .NET workflow.

**Exit Criteria:**
- A clear summary of findings
- List of key issues and improvement opportunities

---

### Step 2: Feature Ideation
- Propose features based on identified gaps.
- Focus on:
  - Developer productivity
  - Debugging experience
  - Code quality
  - Onboarding improvements

**Exit Criteria:**
- A validated list of practical and meaningful feature ideas

---

### Step 3: Issue Creation
- Convert each feature into a detailed issue.

Each issue must include:
- Title
- Description
- Problem Statement
- Proposed Solution
- User Benefit / Impact
- Priority (High / Medium / Low)
- Acceptance Criteria
- (Optional) Technical Notes

**Exit Criteria:**
- All features are documented as clear, actionable issues

---

### Step 4: Sequential Implementation
- Trigger ONLY ONE agent.
- The agent must:
  - Work on ONE issue at a time
  - Fully complete the issue before moving to the next
  - Validate implementation before proceeding

Ensure:
- Best coding practices are followed
- Code adheres to security guidelines
- Consistency with existing architecture is maintained

**Exit Criteria (Per Issue):**
- Feature implemented
- Tests passed
- Acceptance criteria met

---

### Step 5: UX & Design Validation
For each implemented feature:
- Follow existing design guidelines
- Maintain a minimalistic UI approach
- Use VS Code Codicons where applicable

**Exit Criteria:**
- UI is clean, consistent, and aligned with VS Code standards

---

### Step 6: Pull Request Creation
- After all issues are completed:
  - Create a SINGLE Pull Request targeting the `staging` branch

PR must include:
- Summary of all changes
- Linked issues
- Testing and validation notes

**Exit Criteria:**
- PR is complete and ready for review

---

### Final Constraint
- No parallel execution allowed
- Each step must complete before the next begins
- Workflow must behave as a strict sequential pipeline
