# Lemon Clicker Bug Report

**Name: Benjamin Liu**
**Tickets solved:** 1 -->

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

## Ticket <2>: <ticket The lemon only lands in four spots>

### Actual cause

<!-- Which file and function was the bug in, and what was wrong with the code?
     Explain why that code produced the behavior described in the ticket. -->

**File / function:** GameScreenView.ts, randomizeLemonPosition

**What was wrong:** Calculations for using Math.random() were rounded up so only 0 & 1 values were used, and only extreme values were outputted"

### Fix

removed Math.round on the outside of the randomX and randomY variables

### How did you find it?
### Hypothesis Testing
    I assumed that the calculation for random was rounded or floored so that only values 0/1 are used and multiplied by screen dimensions
#### Backward tracing

1. **Symptom:** lemon was only appearing in the far corners of the screen
2. **Traced back to:** GameScreenView.ts, which displayed the lemon and had the randomize logic in file
4. **Buggy code:** RandomizeLemonPosition(), where randomX and randomY calculations were rounding

<!-- It is okay to use your judgement here in limiting the number of traceback steps. We want to understand your 
    reasoning for how you discovered where the bug was -->

### Confirming the fix

Restarted the server and screens and noted the menu screen had the value expected (best:0) is addressed in the next bug report.
<!-- How did you confirm the problem is gone? -->