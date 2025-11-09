## Op-Amp Performance Report (15:35 Run)

<img width="1930" height="991" alt="image" src="https://github.com/user-attachments/assets/ee17c7c6-789d-45c3-9097-806f83ce051e" />

### Performance Summary

| Metric | Target | Result | Status |
|---|---|---|---|
| Gain @ 1 kHz | 38–42 dB | 44.5 dB | Fail |
| Input Offset | ≤ 5 mV | -41.3 nV | Pass |
| Slew Rate (Rise) | ≥ 5 V/µs | ~4.5e-7 V/µs | Fail |
| Slew Rate (Fall) | ≥ 5 V/µs | ~4.5e-7 V/µs | Fail |

### Notes

- Input offset is extremely low, almost zero. This likely means the differential pair isn’t properly biased; the offset value is not meaningful in the current state.
- Slew rate is near zero. The required value is in the order of MV/s, but the circuit is giving µV/s, indicating almost no current through the differential pair.
- Gain is higher than target, which also points to very low device currents (gm too low, ro too high).

### Main Issue

The amplifier is **not biased correctly**. The tail current source is not supplying sufficient bias current.

### Next Steps

- Increase bias current in the input differential pair (adjust M11 / reference branch).
- After fixing bias, re-evaluate slew rate and adjust compensation/bias levels accordingly.
- Re-check and fine-tune gain after bias and SR are stable.

**Flow:** Fix bias → Verify SR → Re-tune gain.
