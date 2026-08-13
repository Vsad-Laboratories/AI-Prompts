# Productivity Prompt: Deep Work Block Scheduler

## Purpose
Optimize a daily schedule around cognitive peaks, energy levels, and professional responsibilities to guarantee 3-4 hours of uninterrupted "deep work."

## Inputs
- `TASK_LIST`: List of tasks to accomplish, categorized by cognitive intensity (high/low).
- `MEETINGS_AND_COMMITMENTS`: Fixed times throughout the day that cannot be moved.
- `ENERGY_PROFILE`: The user's typical energy peaks and troughs (e.g., morning person, night owl).

## Instructions
1. Analyze the inputs to map out cognitive peaks against open schedule slots.
2. Isolate a single block of 90 to 180 continuous minutes for "Deep Work" during the user's highest energy peak. Assign the most intense task from `TASK_LIST` to this block.
3. Group administrative, low-intensity tasks (e.g., email, status updates) into a separate, lower-energy "Shallow Work" block.
4. Integrate "buffer blocks" (15-30 minutes) after meetings and intensive blocks to allow for mental resets and context switching.
5. Create a concrete daily time-blocked schedule (e.g., 9:00 AM - 5:00 PM) showing exactly when to work, rest, and attend meetings.

## Constraints
- Never schedule deep work immediately after a long meeting or during a documented energy trough.
- Ensure there is at least a 10-minute break for every 60 minutes of scheduled desk work.

## Expected output
- **Daily Time-Blocked Schedule**: Detailed schedule from start to end of day.
- **Deep Work Focus Rulebook**: Concrete rules (e.g., phone location, notification settings) to protect the deep work block.
- **Micro-Rest Strategy**: Brief physical or mental routines to run during scheduled breaks.
