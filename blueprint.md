# Minesweeper Game Blueprint

## 1. Overview

A modern, web-based Minesweeper game built with HTML, CSS, and vanilla JavaScript. The game offers a classic Minesweeper experience with several enhancements, including a customizable mine count, a computer-assisted hint system, and a clean, responsive, and performant user interface designed for both desktop and mobile. The entire application is contained within a single `index.html` file.

## 2. Project Outline & Features

This section documents the design, style, and features of the application from the initial version to the current one.

### 2.1. Initial Version (Core Game)
*   **Framework:** None. Built with plain HTML, CSS, and JavaScript.
*   **Structure:** A single `index.html` file.
*   **Game Board:** A 20x20 grid.
*   **Core Logic:** Left-click to reveal, right-click to flag, win/loss conditions, and chain reaction for empty cells.
*   **Customization:** Input field for mine count.

### 2.2. Visual & Layout Upgrade (Flexbox Centering)
*   **Layout:** The main game container is centered using CSS Flexbox.
*   **Styling:** Added backgrounds, rounded corners, box-shadows, and colored numbers for revealed cells to enhance visual hierarchy and readability.

### 2.3. "The 5-Light Indicator" Feature (Computer Assistance)
*   **UI Element:** A visual "energy slot" with 5 lights.
*   **Logic:** Correctly flagging 5 mines rewards the player by having the computer automatically mark one un-flagged mine. The lights reset after the reward.

### 2.4. Icon & Style Differentiation
*   **Objective:** To create clear visual distinctions between game actions.
*   **Iconography:** Player Flag (`🚩`), Computer-Assisted Flag (`📍`), Revealed Mine (`💣`), Incorrectly Flagged Mine (`❌`).

### 2.5. Mobile & Responsive Optimization
*   **Objective:** To make the game fully functional and enjoyable on mobile devices.
*   **Toggle Mode:** Added "Dig" (`⛏️`) and "Flag" (`🚩`) buttons for single-tap operation on touchscreens.
*   **Responsive Layout:** Implemented horizontal scrolling for the grid on small screens and made controls larger and easier to tap.
*   **Interaction Polish:** Added CSS to prevent pull-to-refresh and accidental text selection on mobile.

### 2.6. Performance & Rendering Optimization (Current Version)
*   **Objective:** To eliminate layout shifts, reduce rendering lag, and create a smoother user experience.
*   **Layout Stability:**
    *   CSS `overflow-y: scroll;` was applied to the `body` to permanently reserve space for the scrollbar, preventing the entire layout from shifting when the content height changes.
    *   CSS `overscroll-behavior-y: contain;` was also added to prevent the pull-to-refresh action on mobile browsers.
*   **Efficient DOM Updates:**
    *   The core rendering logic was refactored. The `initGame()` function now creates the 400 grid cell DOM elements only once.
    *   The `renderGrid()` function was optimized to no longer clear and rebuild the entire grid on every click. Instead, it now intelligently iterates through the existing cell elements and only updates their CSS classes and `innerHTML` to reflect the current game state. This dramatically reduces the amount of DOM manipulation, resulting in a significantly faster and flicker-free rendering process.

## 3. Current Implementation Plan

The last user request was to optimize performance and rendering. This has been completed. The current state of the application reflects all the features listed in this blueprint. No further implementation is planned until the next user request.
