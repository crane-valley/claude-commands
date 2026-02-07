---
argument-hint: <bug-description>
description: Debug with competing hypotheses using agent team
---

Create an agent team to investigate: $ARGUMENTS

Use the competing hypotheses approach - teammates actively challenge each other's theories.

1. **Gather initial context**:
   - Read relevant error logs, stack traces, or reproduction steps
   - Identify the affected code areas
   - List 3-5 plausible hypotheses for the root cause

2. **Spawn hypothesis investigators** (one per hypothesis, use Sonnet, max 5 teammates):
   - Give each teammate a specific hypothesis to investigate
   - Include relevant file paths and context in their spawn prompt
   - Tell each: "Investigate whether [hypothesis] is the root cause. Gather evidence for AND against. When done, share your findings with all teammates and challenge other hypotheses."

3. **Enable debate**:
   - After initial investigation, have teammates share findings
   - Each teammate should try to disprove others' theories with evidence
   - The surviving theory with strongest evidence wins

4. **Converge on root cause**:
   - Wait for teammates to finish their debate
   - Synthesize: which hypothesis has the strongest evidence?
   - Identify the confirmed root cause
   - If no clear winner, narrow to top 2 and spawn focused investigators

5. **Propose fix**:
   - Based on the confirmed root cause, propose a specific fix
   - Identify affected files and the minimal change needed
   - Note any regression risks

6. **Clean up the team** and present:
   - Root cause (with evidence)
   - Proposed fix
   - Hypotheses that were ruled out (and why)
