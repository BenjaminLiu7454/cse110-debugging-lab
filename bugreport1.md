# Lemon Clicker Bug Report

**Name: Benjamin Liu**
**Tickets solved:** 1, 3 -->

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

## Ticket <3>: <ticket The lemon only lands in four spots>

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

Restarted the server and screens and noted the lemon positions were not consistently in the far corner.


## Ticket <2>: <ticket Best score always shows 0>

### Actual cause

<!-- Which file and function was the bug in, and what was wrong with the code?
     Explain why that code produced the behavior described in the ticket. -->

**File / function:** index.ts

**What was wrong:** Best score on menu always shows as 0 regardless of score

### Fix

changed inequality of the check for best, as it only updated score if the score being checked was less than best

### How did you find it?
### Hypothesis testing
    after fixing ticket 1, I kept in mind that the logic for calculating best and average were stored in index.ts, so I assumed the bug was there
#### Backward tracing

1. **Symptom:** Best score on menu always shows as 0 regardless of score
2. **Traced back to:** index.ts 
4. **Buggy code:** for loop calculating best score had the inequality flipped

<!-- It is okay to use your judgement here in limiting the number of traceback steps. We want to understand your 
    reasoning for how you discovered where the bug was -->

### Confirming the fix
Best 0 was now 19 as set by the leaderboard earlier, played a round to check it updates with higher scores and doesn't update with lower
<!-- How did you confirm the problem is gone? -->