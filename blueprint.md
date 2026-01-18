# Minesweeper Game Enhancement Blueprint

## 1. Project Overview

This document outlines the plan to enhance a web-based Minesweeper game. The goal is to add features that improve user experience and replayability, specifically by introducing difficulty levels, a game timer, and a player assistance mechanism.

## 2. Implemented Features and Design

### **Current Version**
*   **Core Gameplay:** A functional Minesweeper game with three difficulty levels (Easy, Medium, Hard).
*   **Dynamic Layout:** The game grid automatically adjusts its size based on the selected difficulty using CSS variables.
*   **Game Timer:** A timer starts on the first click and stops when the game ends.
*   **Controls:**
    *   UI buttons to switch between "Dig" and "Flag" modes for mobile-friendly play.
    *   Click to perform the selected action (dig or flag).
    *   Right-click always flags a cell on desktop.

### **Re-implementing the Green Light Bonus**

*   **Green Light Bonus:** A system to reward correct flagging.
    *   When a player correctly flags a mine, a green light turns on.
    *   After collecting 3 correct flags, the game automatically marks one un-flagged mine with a special pin (📍).
    *   The lights reset after the bonus is awarded.
*   **Game Instructions:** A clear explanation of the game rules, controls, and the bonus feature is displayed on the page.

## 3. Current Enhancement Plan: Re-add Green Light Feature

This plan details the steps to re-integrate the green light bonus system and add game instructions.

### **Step 1: UI Enhancements**

*   **HTML Structure:**
    *   Add a `<div>` with the ID `#energy-slot` to contain three individual `<div>` elements, each representing a light.
    *   Add a `<div>` with the ID `#computer-assistant` to display messages when the bonus is triggered.
    *   Add a `<div>` with the ID `#instructions` to hold the game rules.
*   **CSS Styling:**
    *   Add styles for the `#energy-slot` and the `.light` elements, including an `.on` state for when a light is active.
    *   Style the `#computer-assistant` and `#instructions` sections for readability.

### **Step 2: JavaScript Logic for Green Light Bonus**

*   **State Management:**
    *   Introduce a `correctFlagsForBonus` variable to track the number of correct flags placed.
    *   Add an `isComputerFlagged` property to each cell object in the `grid` data structure.
*   **Game Flow Integration:**
    *   In `initGame()`: Reset `correctFlagsForBonus` and clear any bonus-related messages.
    *   In `handleCellRightClick()` (or the flagging logic):
        *   When a flag is placed on a mine, increment `correctFlagsForBonus` and update the lights.
        *   If `correctFlagsForBonus` reaches 3, trigger the `computerRevealMine()` function, reset the counter, and update the lights.
        *   When a correct flag is removed, decrement the counter.
*   **Bonus Functions:**
    *   `updateLights()`: Visually syncs the number of lit lights with the `correctFlagsForBonus` counter.
    *   `computerRevealMine()`: Finds an un-flagged mine, marks it as `isComputerFlagged`, and displays a message.
*   **Rendering:**
    *   Update `renderGrid()` to display a different icon (📍) for mines flagged by the computer.
    *   Update `handleCellClick()` to prevent digging on computer-flagged cells.
