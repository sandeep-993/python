# Interview Practice Projects

Projects turn isolated concepts into practical problem-solving. Keep the first version small, write down requirements, and explain design choices as you build. For each project, include tests and a short README describing how to run it.

## Project 1: Number guessing game

**Practice:** input conversion, loops, conditions, random numbers, and validation.

**Requirements:** generate a secret number, accept guesses, report higher/lower, and stop on a correct guess or a defined attempt limit. Handle invalid input without losing an attempt unless the requirements say otherwise.

**Interview extensions:** isolate the game logic in functions, inject the secret number for deterministic tests, and track attempts.

## Project 2: Calculator

**Practice:** functions, branching, exceptions, and input validation.

**Requirements:** support a small set of arithmetic operations and reject invalid operators and division by zero clearly.

**Extensions:** separate parsing from calculation and add unit tests for every operation and error case.

## Project 3: To-do list

**Practice:** lists or dictionaries, CRUD operations, functions, and JSON persistence.

**Requirements:** add, list, complete, and remove tasks; save and load them from a file.

**Extensions:** assign unique IDs, validate file data, and avoid losing data if a write fails.

## Project 4: Contact book

**Practice:** dictionaries, searching, input normalization, and file handling.

**Requirements:** add, search, update, and remove contacts. Decide whether names, email addresses, or generated IDs are unique keys.

**Extensions:** support CSV or JSON import/export and test duplicate handling.

## Project 5: Expense tracker

**Practice:** data modeling, dates, decimal values, aggregation, and tests.

**Requirements:** record an amount, category, and date; list expenses and calculate totals by category or month.

**Extensions:** use `decimal.Decimal` when exact decimal currency arithmetic is required, validate dates, and test boundary dates.

## Project 6: Student records

**Practice:** classes or dataclasses, collections, sorting, validation, and exceptions.

**Requirements:** add students, record marks, compute summaries, and find a student by ID.

**Extensions:** separate domain logic from input/output and add tests for missing IDs and invalid marks.

## How to approach a project in an interview

1. Clarify users, inputs, outputs, constraints, and error behavior.
2. Identify the main entities and operations.
3. Select data structures based on access and update patterns.
4. Sketch a small API or pseudocode before implementation.
5. Implement a minimal working version.
6. Test normal, boundary, and invalid cases.
7. Discuss time/space complexity and tradeoffs.
8. Refactor only after the behavior is correct.

## Review checklist

- Are responsibilities separated and names clear?
- Are assumptions and edge cases documented?
- Is input validated at the boundary?
- Are file resources and errors handled safely?
- Can core logic be tested without interactive input?
- Are secrets and personal data kept out of the repository?
