# CS 490 – Individual Project 1: Quantum Tic-Tac-Toe

## Overview

This assignment simulates a starter task you might be given as a junior software engineer joining a team. A senior engineer began implementing a new feature — Quantum Tic-Tac-Toe — but got sick before finishing.

Your job is to:

- Understand the existing Covey.Town codebase
- Complete the unfinished parts of the project
- Write tests to verify your implementation

You are given 2 weeks to complete this assignment. It is estimated to take about 8 hours of focused work. Start early to avoid rushing and producing low-quality code.

---

## Objectives

By completing this assignment, you will:

- Become familiar with TypeScript, VSCode, and the Covey.Town codebase
- Practice reading and writing TypeScript code
- Learn how to translate high-level requirements into working code
- Gain experience writing unit tests using Jest

---

## Scenario

- Covey.Town has a built-in Tic-Tac-Toe game, but engagement is low.
- A webcomic has popularized a variant called Quantum Tic-Tac-Toe.
- Management wants this variant implemented in Covey.Town to attract users.
- A senior engineer started this project but is unavailable to finish.
- You will complete the feature and its tests.

---

## Getting Started

### Branch Setup

The starter code is in the `fall2025-ip1` branch of the course staff’s Covey.Town repository.

**If you forked the repo in IP0:**

```bash
git remote add course-staff https://github.com/kelloggm/covey.town.git
git fetch course-staff
git checkout fall2025-ip1
```

**If you cloned(what i did) the repo in IP0:**

```bash
git fetch origin
git checkout fall2025-ip1
```

## Code Modification Limits

- You may modify any code as needed.

- You must not change existing tests for non-Quantum-Tic-Tac-Toe components.

- Only modify or add tests specifically for Quantum Tic-Tac-Toe.

- All modified files must be listed under "files" in package.json before submitting

# Implementation Tasks

## Task 1 – Implement `QuantumTicTacToeGame` (58 points)

**Files:**

- `QuantumTicTacToeGame.ts`
- `QuantumTicTacToeGame.test.ts`
- `shared/types/CoveyTownSocket.d.ts`

This class extends the existing `Game` class.

### a) Constructor (1 point)

- Initialize all fields properly.

### b) Joining and Leaving (8 points)

- Implement `_join()` and `_leave()` methods.
- Manage players and subgames (A, B, C).
- Reference `TicTacToeGame.ts` and `Game.ts` for patterns.

**Grading:**

- `_join()` passes tests: 4 points
- `_leave()` passes tests: 4 points

### c) Applying a Move (22 points)

- Implement `applyMove()` to apply moves to the correct subgame.
- Implement helper methods:
  - `_validateMove`
  - `_checkForWins`
  - `_checkForGameEnding`
- Expand on the existing `makeMove` test infrastructure.

### d) Testing (27 points)

- Write extensive tests for `_join()`, `_leave()`, and `applyMove()`.
- Autograder will inject 180 bugs; you must catch ≥167 for full credit.

**Scoring Table:**

| Mutants Detected | Points |
| ---------------- | ------ |
| ≥167             | 27     |
| 166              | 24     |
| ≥164             | 21     |
| ≥161             | 18     |
| ≥156             | 15     |
| ≥148             | 12     |
| ≥135             | 9      |
| ≥124             | 6      |
| ≥90              | 3      |
| <90              | 0      |

---

## Task 2 – Wire Up `QuantumTicTacToeGameArea` (12 points)

**File:** `QuantumTicTacToeGameArea.ts`

- Implement the `handleCommand()` method.
- This method receives commands from clients and routes them to `QuantumTicTacToeGame`.
- There are 3 types of commands, mapping to the 3 main methods of your game.
- A complete test suite is already provided — no need to write new tests.

**Grading:**

- Passing all existing tests: 12 points

---

## Task 3 – Finish Frontend in `QuantumTicTacToeAreaController` (20 points)

**File:** `QuantumTicTacToeAreaController.ts`

- Implement the `_updateFrom()` method to synchronize frontend state with backend.

**Responsibilities:**

- Call `super._updateFrom(newModel)`
- Rebuild the state of the 3 boards (A, B, C) based on `newModel`
- Emit:
  - `"boardChanged"` event when the board updates
  - `"turnChanged"` event when the turn changes

This method acts as the bridge between backend game state and UI.

**Grading:**

- Passing all existing tests: 20 points

---

## Grading Breakdown

| Component                               | Points  |
| --------------------------------------- | ------- |
| Task 1 – QuantumTicTacToeGame           | 58      |
| Task 2 – QuantumTicTacToeGameArea       | 12      |
| Task 3 – QuantumTicTacToeAreaController | 20      |
| **Total (Autograder)**                  | **90**  |
| Style & Manual Review                   | 10      |
| **Grand Total**                         | **100** |

---

## Style Requirements (10 points)

- Follow naming conventions from the course style guide
- No unused variables
- All public methods/properties documented with JSDoc
- No duplicated logic (refactor into shared methods if needed)
- Each violation deducts 2 points (up to 10)

---

## Linting

- Run `npm run lint` before submitting.
- Any linter errors = automatic grade of 0.

---

## Submission Instructions

1. Ensure all modified files are listed in `"files"` in `package.json`.
2. Run:
   ```bash
   npm run zip
   ```
