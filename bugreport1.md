# Lemon Clicker Bug Report

**Name:**
**Tickets solved:** <!-- e.g. 1, 2, 3, 5, 6 (at least five) -->

Copy the template below once for each ticket you solved. 

---

## Ticket <1>: <ticket Stats always say Stats unavailable>

### Actual cause

<!-- Which file and function was the bug in, and what was wrong with the code?
     Explain why that code produced the behavior described in the ticket. -->

**File / function:** MenuScreenController.ts, loadStatsFromServer()

**What was wrong:** Stats on Menu Screen shows "Stats Unavailable"

### Fix

the fetch("/api/stats") used the path /api/stat instead of stats

### How did you find it?

#### Backward tracing

1. **Symptom:** text was shown as unavailable even when inserting the leaderboard.json file in
2. **Traced back to:** MenuScreenView.ts, which displayed the text itself 
3. **Traced back to:** MenuScreenController.ts,
4. **Traced back to:** index.ts
4. **Buggy code:** MenuScreenController: found that the api fetch path had a typo 

<!-- It is okay to use your judgement here in limiting the number of traceback steps. We want to understand your 
    reasoning for how you discovered where the bug was -->

### Confirming the fix

Restarted the server and screens and noted the menu screen had the value expected (best:0) is addressed in the next bug report.
<!-- How did you confirm the problem is gone? -->