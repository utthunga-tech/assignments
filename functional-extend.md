# Extending and Refactoring

This exercise is about extending functionality.
Often, while extending existing code, it becomes slightly more complex.
The 'cleanliness' of the code goes down.

The skill of refactoring keeps the code clean and fresh.

This assignment is a continuation of the [previous one](bms-statement.md).

## Extensions

Try at least **two** of these extensions on your code.
Mention the extensions you select in your `README.md` file.

### Extension 1: Early Warning
Customers need _early warnings_ to take action,
in addition to the alarm that you print after the limit is breached.
Introduce a 'warning' level with a tolerance of 5% of the upper-limit.

Example: If the SoC needs to be between 20 and 80, the warning-tolerance is `5% of 80` = `4`.
Warnings need to be displayed in these ranges:
- `20` to `20+4` Warning: Approaching discharge
- `80-4` to `80` Warning: Approaching charge-peak

Same for Temperature and Charge-rate.

### Extension 2: Support a language in addition to English

Our market has expanded to German-speaking countries!
Switch the language of the printed messages based on a global variable.

Use [Google translate](https://translate.google.com/?sl=en&tl=de&op=translate)
if you aren't familiar with German.

### Extension 3: Accept input in different units

Some sensors report the temperature in Fahrenheit.
Make provision to express the unit along with the measurement.
Avoid repeating the limits in different units.

## Recommended process

1. Try / imagine the changes on the existing assignment.
Experience the places where code gets more complex.
Think of refactoring opportunities.
1. Read the Recommended Approach below. 
1. Start over with a **fresh assignment**
(accept one of the assignments at the bottom of this page).
1. Re-use / copy code from previous assignment only if you feel good about it.
1. Commit in the Fresh assignment

## Recommended Approach

Treat the problem as a series of data-transformations.
A chain of transformations is suggested below.

- Translate to common units

- Mark the anomaly against the ranges. Keep the code common across parameters and vary the data.
    
    Example: Design a data-structure with a series of numbers representing the boundary of each condition.
    In the example above: 
    - `0 to 20`: `LOW_SOC_BREACH`
    - `21 to 24`: `LOW_SOC_WARNING`
    - `24 to 75`: `NORMAL`
    - `76 to 80`: `HIGH_SOC_WARNING`
    - `81 to 100`: `HIGH_SOC_BREACH`

- Translate the anomaly to a message in the appropriate language

- Output the resulting message

- Compute overall Battery status. Make logical assumptions in case of warning and error combinations.

Each transformation is one function (or more).
Do not mix different transformations in the same function.
Have one function to chain ('compose') these transformation-functions.

## Fresh Assignment - with "same old" starting-point

[C](https://classroom.github.com/a/oT3763ql)

[C++](https://classroom.github.com/a/DLdvNpl-)

[C#](https://classroom.github.com/a/bmUQtxVu)

[Java](https://classroom.github.com/a/yj7qNrEu)

[Python](https://classroom.github.com/a/aiLG__Yz)

## Alternative

You could also extend your old repository without joining a new assignment.
If you prefer that, please complete/merge the current Pull Request
and create a new one
