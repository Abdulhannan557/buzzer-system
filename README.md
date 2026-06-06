# 3-User Buzzer System with Scoring

## Overview

A complete digital logic circuit built in **Logisim Evolution 4.1.0** that implements a 3-user buzzer system with automatic locking and scoring counters.

### Features

✅ **3 Independent Buttons** - Buzzer1, Buzzer2, Buzzer3
✅ **Priority Logic** - First press wins, others are locked out
✅ **Visual Winner Indicator** - LED lights up for the winner
✅ **Automatic Counters** - Tracks wins for each user
✅ **Reset Button** - Start new rounds with one click
✅ **Digital Logic Design** - Perfect for learning sequential circuits

---

## How It Works

### Logic Flow

1. **Initial State**: All outputs are 0, system ready
2. **Button Press**: User presses Buzzer button
3. **Lock Activation**: First valid press sets a D Flip-Flop
4. **Signal Locking**: OR gate generates LOCK signal
5. **Block Others**: NOT gate creates NOT_LOCK, disabling other buttons
6. **LED Indication**: Winner's LED lights up green
7. **Score Increment**: Counter for that user increments
8. **Reset**: Pressing Reset clears lock and prepares for new round

---

## Quick Start

### 1. Prerequisites
- **Logisim Evolution 4.1.0** - Download from [GitHub](https://github.com/logisim-evolution/emu/releases)

### 2. Opening the Circuit
1. Open Logisim Evolution
2. File → Open → Select `3-User-Buzzer-System.circ`

### 3. Running Simulation
1. Click **Simulate → Start** (or press `Ctrl+K`)
2. Click the Buzzer buttons to test
3. Watch LEDs light up and counters increment

### 4. Testing
**Test 1: First Press Wins**
- Click Buzzer1 → Winner1 LED glows ✓
- Try Buzzer2, Buzzer3 → No effect ✓
- Counter1 shows 1 ✓

**Test 2: Reset Works**
- Click Reset → LED turns off ✓
- Try Buzzer2 → Winner2 LED glows ✓
- Counter1 still shows 1 (score persists) ✓

---

## Files in This Repository

### 📄 Documentation
- **README.md** - This file
- **BUILD-GUIDE.txt** - Step-by-step building instructions
- **CIRCUIT-LOGIC.md** - Detailed logic explanation
- **COMPONENTS.md** - Component specifications
- **TROUBLESHOOTING.md** - Common issues and solutions

### 🔧 Circuit Files
- **3-User-Buzzer-System.circ** - Ready-to-open Logisim circuit

---

## Components Used

| Component | Qty | Purpose |
|-----------|-----|----------|
| Buttons | 4 | User inputs (Buzzer1-3, Reset) |
| AND Gates | 3 | Priority logic (enable only first press) |
| OR Gate | 1 | Generate LOCK signal |
| NOT Gate | 1 | Invert LOCK to NOT_LOCK |
| D Flip-Flops | 3 | Latch and remember first winner |
| LEDs | 3 | Visual winner indicator |
| Counters | 3 | Track wins for each user |
| Constant | 1 | Provide value 1 to FF inputs |
| **TOTAL** | **22** | **All components** |

---

## Learning Outcomes

This project teaches:
- **Sequential Logic** - D Flip-Flops, latching
- **Combinatorial Logic** - AND, OR, NOT gates
- **Priority Encoding** - First input selection
- **Digital State Machines** - System states
- **Circuit Design** - From concept to implementation
- **Debugging** - Testing and troubleshooting

---

## Project Structure

```
3-User-Buzzer-System/
├── 3-User-Buzzer-System.circ    # Main circuit file
├── README.md                     # Overview
├── BUILD-GUIDE.txt              # Step-by-step instructions
├── CIRCUIT-LOGIC.md             # Logic explanation
├── COMPONENTS.md                # Component specs
└── TROUBLESHOOTING.md           # FAQ & help
```

---

## System Specifications

| Specification | Value |
|---|---|
| **Users** | 3 |
| **Winner Selection** | First-press priority |
| **Scoring Range** | 0-255 (8-bit counter) |
| **Component Count** | 22 |
| **Estimated Build Time** | 30-45 minutes |

---

## License

MIT License - Free to use, modify, and distribute

---

**Happy Learning! 🎉**

For detailed building instructions, see [BUILD-GUIDE.txt](BUILD-GUIDE.txt)