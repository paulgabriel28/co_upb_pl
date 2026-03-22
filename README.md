# Simplex PL

`simplex_PL.html` is a single-file interactive solver for Linear Programming problems using the Simplex method with Big-M handling for artificial variables.

The page is written in Romanian and is designed as a step-by-step teaching tool, not just a calculator. It guides the user from the original LP model to the standard form, initial basis, simplex iterations, and final verification in the original problem.

## What It Does

- defines a linear objective function for `max` or `min`
- accepts multiple linear constraints with `=`, `<=`, and `>=`
- automatically transforms the LP problem into `PLS` (standard form)
- adds slack/surplus and artificial variables using the Big-M method
- builds the initial basis (`ASP`)
- runs the simplex iterations and highlights:
  - entering variable
  - leaving variable
  - pivot element
  - `zj`, `Δj`, `θ`, and objective value at each iteration
- shows symbolic and numeric formulas when a simplex-table cell is double-clicked
- verifies the final solution back in the original LP
- exports the solved workflow to PDF
- saves and reloads exercises locally with IndexedDB
- exports/imports the local exercise database as JSON

## Workflow

The interface is split into 5 stages:

1. `PL Input`
   Enter the objective, constraints, and non-negativity condition.
2. `PL -> PLS`
   Transform the original LP into standard form.
3. `ASP`
   Build the initial basis and display the matrices/vectors used by the algorithm.
4. `Simplex Table`
   Inspect every iteration of the simplex method.
5. `Verification`
   Check the computed solution in the original model and export the result.

## Constraint Conversion Rules

The file applies the following conversion rules:

- `=` -> `+z_k`
- `<=` -> `+y_k`
- `>=` -> `-y_k + z_k`

where:

- `y_k` = slack/surplus variable
- `z_k` = artificial variable

Artificial variables receive coefficient `+M` in the objective function.

## How To Use

Open `simplex_PL.html` in a modern browser and follow the on-screen steps.

Recommended flow:

1. set the number of variables and constraints
2. choose `max` or `min`
3. fill in objective coefficients
4. fill in each constraint
5. click `Validare`
6. continue through `PLS`, `ASP`, `Tabel Simplex`, and `Verificare`
7. optionally save the exercise or export the solved result to PDF

## Files

- `simplex_PL.html` - the full application in one HTML file
- `README.md` - documentation for the page

## Technical Notes

- no build step is required
- the application is client-side only
- saved exercises are stored in the browser with IndexedDB
- PDF export depends on browser-side libraries loaded at runtime
- the page also loads Google Fonts from the web

## Best Used For

- Operations Research / Linear Programming coursework
- simplex demonstrations in class or seminar
- step-by-step verification of LP exercises
- learning how Big-M affects the initial simplex basis

## Limitations

- the page assumes a standard non-negativity condition
- it is intended for educational simplex workflows, not large-scale optimization
- persistence is local to the browser unless the database is exported manually
- the built-in “validation” confirms the expected LP structure in the UI; it is not a formal symbolic parser

## Quick Start

```text
Open proiect_final/simplex_PL.html in your browser.
```
