# SIT 820 troubleshooting guide – notes

Source: FireParts "SIT Gas Control Valve" troubleshooting guide (rev. 01/2020), 19 pages. Local copy: `sit-820-troubleshooting-guide.pdf`.
The page cross-references inside the guide's flowchart are off by 1–2 pages; the page numbers below are the actual printed ones.

## Flowchart (pp. 1–3)

| Step | If NO, check |
|---|---|
| Press the igniter: spark at the pilot hood? | Igniter wire connections, electrode position, pinched or broken ignition wire, cracked porcelain electrode base, then replace the igniter |
| Knob to PILOT, push in, press igniter: pilot lights? | Realign the knob. With a flame wand held at the pilot hood (gas off), push the knob in. **Wand flame bends away:** air in the line, purge it (p. 6). **Doesn't bend:** no gas; check the pilot screw isn't closed, shutoffs are open, and gas is reaching the valve. Then clean the pilot orifice and tube, then replace the valve. |
| Pilot flame correct? | Adjust the pilot (p. 7), check orifice size and partial blockage, check inlet pressure (p. 8) |
| Release the knob: pilot stays lit? | Relight and hold 30 s; test the thermocouple (pp. 9–10) and pilot coil (EPU, p. 11) |
| Knob ON + switch ON: burner on? | Knob really at ON, thermostat calling for heat, wiring correct; then Tests 1–3 (pp. 12–15) |
| Burner flame correct? | Regulator set for fuel type, orifice size, inlet and outlet pressure, burner blockage; last resort, replace the valve (bad diaphragm) |

## Test specs (multimeter on DC mV; pilot lit about 3 min first)

| Test | Leads | Good reading | Page |
|---|---|---|---|
| Test 1 – thermopile | TP ↔ TP–TH, all wires off except thermopile | ≥300 mV; if not, adjust the pilot or replace the thermopile | 12 |
| Test 2 – operator head | Same, with jumper TH ↔ TP–TH | ≥225 mV and < Test 1. Equal to Test 1 = open head; <225 = too much resistance (see p. 14) | 13 |
| Coil resistance | TP ↔ TH | 2.25 ± 0.5 Ω. Replace the valve only if Test 2 <225 mV **and** the coil is out of spec | 14 |
| Test 3 – thermostat circuit | Jumper removed, switch wires on, switch ON | ≥145 mV and < Test 1. Equal to Test 1 = switch circuit problem | 15 |
| Switch circuit continuity | Switch wires off the valve, switch ON | Continuity; none = bad wires or switch | 16 |
| Thermocouple | Using a thermocouple adapter | ≥6 mV | 9–10 |
| EPU (pilot coil) | Socket center ↔ ground | Continuity, about 0.018 ± 0.003 Ω | 11 |
| Inlet gas pressure | Inlet tap, burner on | NG ≥5" W.C.; LP ≥11" W.C. | 8 |
| Outlet gas pressure | Outlet tap, burner on | NG 1.8–3.5" W.C. The LP value is printed as "2.7 / 11", which looks like a typo; check the rating plate | 17 |

## Running Tests 1 and 2

Setup:
- Remove the lower grille or louvre to reach the valve.
- Find the three screw terminals on the valve: TH, TP–TH and TP.
- The thermopile's two wires go to TP and TP–TH. The wall-switch wires go to TH and TP–TH (often stacked with a thermopile wire on TP–TH).
- Meter on DC millivolts. On a 2 V range, 0.419 means 419 mV. A negative reading only means the leads are reversed.
- Light the pilot, leave the gas knob at **PILOT**, and wait 5+ minutes so the thermopile reaches full output (the guide says about 3 min).

**Test 1 – thermopile alone (no load)**
1. Disconnect the switch wire from TH, and the switch wire on TP–TH if it's separate. Leave both thermopile wires connected.
2. Probe TP and TP–TH.
3. Pass: **≥300 mV**.

**Test 2 – thermopile powering the valve coil (loaded)**
1. Same as Test 1, plus a short jumper from TH to TP–TH. This acts like a perfect switch. With the knob at PILOT, the main burner won't light.
2. Probe TP and TP–TH again. Let the reading settle about 30 s.
3. Pass: **≥225 mV and lower than Test 1**.
   - Equal to Test 1: the operator coil is open (bad valve).
   - Below 225 mV: weak thermopile or poor pilot flame, given the coil measured in spec.

Afterward: remove the jumper, reconnect the switch wires tightly, and refit the grille.

Optional switch-drop check: with the switch wires connected, the switch ON and the knob at PILOT, probe TH to TP–TH. Good is under about 50 mV. A higher reading means the switch or wiring is losing power.

## Pilot (p. 7)
- Soft blue flame that contacts both the thermocouple and the thermopile.
- Adjustment screw: clockwise = smaller flame, counter-clockwise = larger.

## Purging air (p. 6)
- Loosen the inlet pressure tap 2–3 turns, leave it open until the air is purged, then retighten.
