# Circuit Logic Explanation

## System Overview

This 3-User Buzzer System implements a **priority encoder** using digital logic components. It demonstrates:
- Sequential logic (flip-flops)
- Combinatorial logic (AND, OR, NOT gates)
- State machines
- Priority selection

---

## Boolean Equations

### Complete System Logic

```
// Input signals
Buzzer1, Buzzer2, Buzzer3, Reset ∈ {0, 1}

// LOCK signal generation
LOCK = Q1 ∨ Q2 ∨ Q3  (OR operation)

// NOT_LOCK signal
NOT_LOCK = ¬LOCK  (NOT operation)

// Set signals (AND operations)
SET1 = Buzzer1 ∧ NOT_LOCK
SET2 = Buzzer2 ∧ NOT_LOCK
SET3 = Buzzer3 ∧ NOT_LOCK

// Flip-flop outputs
Q1 = SET1 → FF1_Q (on clock pulse)
Q2 = SET2 → FF2_Q (on clock pulse)
Q3 = SET3 → FF3_Q (on clock pulse)

// Clear operations
Reset → Q1 = 0
Reset → Q2 = 0
Reset → Q3 = 0

// Output signals
Winner1_LED = Q1
Winner2_LED = Q2
Winner3_LED = Q3

// Counter increments
Count1 += SET1
Count2 += SET2
Count3 += SET3
```

---

## Operation Flow

### Initial State
```
Q1 = 0, Q2 = 0, Q3 = 0
LOCK = 0 OR 0 OR 0 = 0
NOT_LOCK = NOT(0) = 1
All LEDs = OFF
All Counters = 0
```

### User 1 Presses Buzzer1
```
SET1 = Buzzer1 AND NOT_LOCK
SET1 = 1 AND 1 = 1 ✓

FF1 Clock Pulse:
  Q1 = 1
  Winner1 LED = ON
  Counter1 Increments
```

### System Locks
```
LOCK = Q1 OR Q2 OR Q3
LOCK = 1 OR 0 OR 0 = 1
NOT_LOCK = NOT(1) = 0
```

### Users 2 & 3 Try to Press (BLOCKED)
```
SET2 = Buzzer2 AND NOT_LOCK
SET2 = 1 AND 0 = 0 ✗

SET3 = Buzzer3 AND NOT_LOCK
SET3 = 1 AND 0 = 0 ✗

No clock pulse to FF2 or FF3
Winner2 and Winner3 LEDs stay OFF
Counter2 and Counter3 don't increment
```

### Reset Button Pressed
```
Clear Signals Activate:
  Q1 = 0
  Q2 = 0
  Q3 = 0

LOCK = 0 OR 0 OR 0 = 0
NOT_LOCK = NOT(0) = 1
All LEDs = OFF

New Round Ready!
```

---

## Truth Table: AND Gate Behavior

### SET1 = Buzzer1 AND NOT_LOCK

| Buzzer1 | NOT_LOCK | SET1 | FF1 Clock | Result |
|---------|----------|------|-----------|--------|
| 0       | 1        | 0    | No        | ✓ Blocked (not pressed) |
| 1       | 1        | 1    | Yes       | ✓ Activated (wins!) |
| 1       | 0        | 0    | No        | ✓ Blocked (locked out) |
| 0       | 0        | 0    | No        | ✓ Blocked |

---

## Truth Table: OR Gate Behavior

### LOCK = Q1 OR Q2 OR Q3

| Q1 | Q2 | Q3 | LOCK | NOT_LOCK | Status |
|----|----|----|------|----------|--------|
| 0  | 0  | 0  | 0    | 1        | System unlocked, buttons active |
| 1  | 0  | 0  | 1    | 0        | Winner found (User1), others blocked |
| 0  | 1  | 0  | 1    | 0        | Winner found (User2), others blocked |
| 0  | 0  | 1  | 1    | 0        | Winner found (User3), others blocked |

---

## Key Features

✅ **Priority Encoding** - Only first valid input accepted
✅ **Automatic Locking** - No software needed
✅ **State Memory** - D Flip-Flops retain state
✅ **Independent Scoring** - Each counter increments independently
✅ **Simple Reset** - Single button clears all states

---

For detailed build instructions, see BUILD-GUIDE.txt