# Component Specifications

## Quick Reference

### Input Components

#### Button
- **Type**: Momentary Push Button
- **Function**: Digital input (0=unpressed, 1=pressed)
- **Output Pin**: Right side
- **Logic Level**: High (1) when pressed
- **Quantity**: 4 (Buzzer1, Buzzer2, Buzzer3, Reset)

### Logic Gates

#### AND Gate (2-input)
- **Function**: Output is 1 only if BOTH inputs are 1
- **Input Pins**: Left (top and bottom)
- **Output Pin**: Right
- **Quantity**: 3 (SET1, SET2, SET3)

#### OR Gate (3-input)
- **Function**: Output is 1 if ANY input is 1
- **Input Pins**: Left (top, middle, bottom)
- **Output Pin**: Right
- **Quantity**: 1
- **Configuration**: Must set to 3 inputs in properties

#### NOT Gate
- **Function**: Inverts input (0→1, 1→0)
- **Input Pin**: Left
- **Output Pin**: Right
- **Quantity**: 1

### Memory Components

#### D Flip-Flop (Rising Edge Triggered)

**Pin Configuration**:
- **D Input** (Left, top): Data input
- **Clock Input** (Bottom, center): Triggering signal
- **Clear Input** (Bottom, left): Asynchronous reset
- **Q Output** (Right, top): Output state
- **Q_NOT Output** (Right, bottom): Inverted output

**Quantity**: 3 (FF1, FF2, FF3)

#### Counter (8-bit Binary)

**Pin Configuration**:
- **Clock Input** (Bottom, center): Increment trigger
- **Clear Input** (Bottom, left): Reset to 0
- **Output**: Count value display

**Configuration**:
- Width: 8 bits
- Range: 0 to 255

**Quantity**: 3 (Count1, Count2, Count3)

### Output Components

#### LED (Light Emitting Diode)

**Pin Configuration**:
- **Input Pin** (Left): Data signal
- **No output**

**Customization**:
- **oncolor**: Color when lit (set to #00FF00 for green)
- **offcolor**: Color when off (default: black)

**Quantity**: 3 (Winner1, Winner2, Winner3)

### Constant Values

#### Constant (Wiring Library)

**Function**: Provides fixed digital value
- **Output Pin**: Right side
- **Configuration**: Set Value to 0x1 (means 1)
- **Quantity**: 1

---

## Connection Checklist

### Inputs to Logic Gates
- [ ] Buzzer1 → AND1 (input 1)
- [ ] Buzzer2 → AND2 (input 1)
- [ ] Buzzer3 → AND3 (input 1)
- [ ] NOT_LOCK → AND1 (input 2)
- [ ] NOT_LOCK → AND2 (input 2)
- [ ] NOT_LOCK → AND3 (input 2)

### Flip-Flop Configuration
- [ ] Constant(1) → FF1 D input
- [ ] Constant(1) → FF2 D input
- [ ] Constant(1) → FF3 D input
- [ ] SET1 → FF1 Clock
- [ ] SET2 → FF2 Clock
- [ ] SET3 → FF3 Clock
- [ ] Reset → FF1 Clear
- [ ] Reset → FF2 Clear
- [ ] Reset → FF3 Clear

### Lock Signal Generation
- [ ] FF1 Q → OR (input 1)
- [ ] FF2 Q → OR (input 2)
- [ ] FF3 Q → OR (input 3)
- [ ] OR output → NOT (input)

### Outputs
- [ ] FF1 Q → Winner1 LED
- [ ] FF2 Q → Winner2 LED
- [ ] FF3 Q → Winner3 LED
- [ ] SET1 → Count1 Clock
- [ ] SET2 → Count2 Clock
- [ ] SET3 → Count3 Clock

---

For detailed specifications, see TROUBLESHOOTING.md