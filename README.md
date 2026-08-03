# WODRLE - My final project at Zenmonk
# Product Perspective
The Wordle web application is a client-side SPA. It operates entirely within the user's web browser, maintaining game state, word dictionaries, and user statistics locally without requiring a backend service.

# Product Functions
Word Guessing Engine: Validates inputs, checks against target word, and assigns letter statuses (correct, present, absent).
Interactive Keyboard: On-screen dynamic keyboard reflecting the status of guessed letters alongside native physical keyboard support. (optional)

# System Features & Functional Requirements

## Core Game Mechanics

### Word Grid Structure

The grid consists of 6 rows and 5 columns (30 tiles total).
Each row represents one 5-letter guess attempt.
Active tile highlights as the user types.

# Input Validation

### Letter Input: Only standard English alphabetical characters (A-Z) are accepted.
Length Validation: A row must contain exactly 5 letters before submission via the Enter key.
Dictionary Validation: Submitted words must exist in a valid 5-letter English word list.
Invalid Word Feedback: If an invalid word is submitted:
Trigger a "Not in word list" toast notification.
Execute a horizontal shake animation on the current row.
Do not consume a guess attempt.

### Letter Status Logic
Upon submitting a valid guess, each tile evaluation follows the standard Wordle evaluation algorithm:
Green (correct): Letter exists in target word and is in the exact correct position.
Yellow (present): Letter exists in target word but in a different position (accounting for letter frequencies).
Gray (absent): Letter does not exist in target word (or exceeds frequency count). 0, mark 'present' and decrement count; otherwise mark 'absent'." type="suggestion">
Note on Duplicates: Letters marked correct take priority over present. Remaining letter instances in target dictate yellow allocations.
### Game Win / Loss Conditions
Win: The user successfully guesses the target word within  attempts.
Trigger tile celebration bounce animation.
Display congratulatory message ("Genius", "Magnificent", "Impressive", etc.).
Open Statistics Modal after a 1.5-second delay.
Loss: The user exhausts 6 attempts without guessing the target word.
Reveal the correct word via a toast message.
Open Statistics Modal after a 1.5-second delay.

## Virtual & Physical Keyboard

### Virtual Keyboard Layout
Standard QWERTY layout divided into 3 rows:
Row 1: Q W E R T Y U I O P
Row 2: A S D F G H J K L
Row 3:
Z X C V B N M

### Key Status Synchronization
Keys on the virtual keyboard dynamically inherit color statuses based on guesses:
Green: Marked correct in at least one guess.
Yellow: Marked present and never correct.
Gray: Marked absent.
Default: Unused letter.

### Physical Keyboard Integration
Listen to global keydown events.
Map keypresses to match virtual key triggers (Enter, Backspace, KeyA - KeyZ).


