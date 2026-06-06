# Troubleshooting Guide

## Common Issues and Solutions

### Issue 1: Wire Turns Red Instead of Green

**Problem**: Wire appears RED instead of GREEN

**Causes**:
- Connecting output to output (should be output to input)
- Connecting input to input
- Wrong pin type

**Solutions**:
1. Verify connection direction: [Output] → [Input]
2. Check pin types (outputs on RIGHT/BOTTOM, inputs on LEFT/TOP)
3. Rotate component if needed: Right-click → Rotate
4. Delete and reconnect with correct pins

---

### Issue 2: Buttons Don't Respond

**Problem**: Clicking buttons in simulation has no effect

**Causes**:
- Simulation is not running
- Button is not connected
- Wrong tool selected

**Solutions**:
1. Verify simulation running: Simulate → Start (or Ctrl+K)
2. Check button connection: Right-click → Properties
3. Use Poke tool (not Delete tool)
4. Test with Probe tool on button output

---

### Issue 3: All Three LEDs Light Up Simultaneously

**Problem**: When pressing any button, multiple LEDs light up

**Causes**:
- OR gate configured incorrectly
- Missing NOT gate
- NOT_LOCK not connected properly
- AND gates not blocking

**Solutions**:
1. Check OR gate: Right-click → Properties → Set inputs to 3 (not 2)
2. Verify NOT gate connected to OR output
3. Verify NOT_LOCK connects to all AND gates
4. Test: Press button → only one LED should light

---

### Issue 4: LEDs Don't Light Up at All

**Problem**: No LED lights when buttons pressed

**Causes**:
- Flip-flops not clocking
- Q outputs not connecting to LEDs
- Buttons not pressing
- D input not set to Constant(1)

**Solutions**:
1. Test button signal with Probe
2. Test AND gate outputs (SET signals)
3. Test FF Q outputs with Probe
4. Verify Constant(1) connected to FF D inputs
5. Check LED input connections

---

### Issue 5: Counters Not Incrementing

**Problem**: Button pressed but counter stays at 0

**Causes**:
- Counter not connected to SET signal
- Counter width misconfigured
- Clear signal blocking increment

**Solutions**:
1. Verify: SET1 → Count1 Clock, etc.
2. Right-click Counter → Properties → Width: 8
3. Test SET signal with Probe
4. Verify Clear pin not always active

---

### Issue 6: Reset Button Doesn't Work

**Problem**: Pressing Reset button doesn't clear system

**Causes**:
- Reset not connected to Clear pins
- Clear pins wired incorrectly
- Reset button wiring issue

**Solutions**:
1. Verify Reset connects to:
   - FF1 Clear, FF2 Clear, FF3 Clear
   - Count1 Clear, Count2 Clear, Count3 Clear (optional)
2. Right-click each component → Properties → Find Clear pin
3. Test Reset signal with Probe

---

### Issue 7: System Locks Permanently

**Problem**: After first button press, nothing triggers anymore

**Causes**:
- LOCK signal stuck at 1
- FF Q won't reset
- Clear signal not working

**Solutions**:
1. Test LOCK signal with Probe
2. After Reset, LOCK should become 0
3. Verify all FF Clear pins connected to Reset
4. Test each Q output with Probe

---

## Quick Diagnostic Checklist

When something doesn't work:

```
☐ Is simulation running? (Simulate → Start)
☐ Are wires green? (Not red)
☐ Is Poke tool selected? (Not Delete tool)
☐ Are all components connected?
☐ Does Constant show 1? (Not 0)
☐ Is OR gate set to 3 inputs?
☐ Does Reset button have output wire?
☐ Are probes showing expected values?
☐ Have you tried Ctrl+Z (undo)?
☐ Have you tried File → Save/Reload?
```

---

## Debugging Tools

### Probe Tool (Most Useful)
1. From Wiring library: Select "Probe"
2. Click on any wire or output
3. Probe shows signal value: 0 or 1
4. Use multiple probes to trace signal path
5. Look for where signal gets stuck at wrong value

### Zoom
- View → Zoom → Zoom In/Out
- Or use scroll wheel

---

For complete troubleshooting guide, see project documentation.