# Cleaning the thermopile and pilot – Lennox LMDV3530CNM

Goal: raise the thermopile's output under load (Test 2 was 170 mV in 2024; spec ≥225 mV) so the system has margin for switch and contact resistance.
Glass removal and log layout vary; follow the LMDV-33/35/40 Care and Operation manual for those steps.

## Your pilot assembly
Labelled photo: `thermopile-labelled.jpg` (from `thermopile.HEIC`). Left to right:
- **Thermocouple** (thin probe, brass base): sand the tip lightly.
- **Spark electrode** (white porcelain base): don't sand. The porcelain cracks easily.
- **Pilot hood** (round flared cap): brush and canned air only. Rust visible; one flare at the front may be bent.
- **Thermopile** (tall silver rod, right): sand the top ~1 in., especially the side facing the hood.
- **Ember wool** (fuzzy clump at the thermopile's base): move it away from the pilot so it can't deflect the flame.

To confirm which rod is which: the thermocouple's copper tube screws into the side of the valve, and the thermopile's two wires go to TP and TP–TH.

## Tools and materials
| Item | Use |
|---|---|
| Phillips and flat screwdrivers, small nut driver set | Glass frame, access panel, valve terminals |
| #0000 (extra-fine) steel wool, or 400–600 grit emery cloth or sandpaper | Polish deposits off the thermopile and thermocouple tips |
| Soft brush (old toothbrush, small paintbrush) | Pilot hood, around the pilot assembly |
| Canned air | Blow out the pilot hood, ports and dust |
| Shop vac or vacuum with a brush nozzle | Dust, spider webs, steel wool fibres |
| Flashlight and phone camera | Inspection; photograph log and ember placement before removing |
| Work gloves; towel or blanket | Handling the glass frame and laying it down |
| Multimeter (DC mV) and jumper wire | Before-and-after Tests 1 and 2 |
| Optional: DeoxIT D5 contact cleaner | Thermopile and switch wire terminals at the valve |
| Optional: ceramic fireplace glass cleaner | Clean the glass while it's out (not regular window cleaner) |
| Optional: spray bottle of soapy water | Leak check, only if you loosened any gas fitting |

## Steps
1. **Baseline.** Pilot lit 5+ min, knob at PILOT. Record Test 1 (all wires off except the thermopile) and Test 2 (jumper TH ↔ TP–TH).
2. **Shut down.** Gas knob to OFF and close the manual shutoff valve. Let it cool 30+ min; the glass and pilot get very hot.
3. **Remove the glass.** Release the glass frame latches or clips per the manual. Lay the frame flat on a towel.
4. **Photograph the logs and embers, then remove** any pieces blocking the pilot. Logs are fragile, so handle them gently.
5. **Inspect the pilot.** Look for white or black crust on the thermopile (the larger rod) and thermocouple (the thinner probe), and for spider webs or debris in the pilot hood.
6. **Clean the thermopile tip.** Lightly polish the tip and upper part with steel wool or emery cloth until it's dull metal with no crust. Don't bend it or move it relative to the pilot hood. Brush off the residue.
7. **Clean the thermocouple tip** the same way.
8. **Clean the pilot hood.** The pilot hood is the small metal cap on top of the pilot assembly, where the pilot flame comes out. It has one or more openings that aim the flame sideways onto the thermopile and thermocouple. In the SIT guide's p. 7 drawing, it's the mushroom-shaped cap between the two rods. Brush any soot or crust off the outside, then blow canned air into the openings to clear dust, spider webs and flakes. Leave it in place, and don't bend it or widen its openings; it sets the flame's direction. Don't poke wire into the pilot orifice unless the flame is still weak afterward; removing the orifice is a separate job.
9. **Vacuum** the burner area and any steel wool fibres.
10. **Valve terminals.** At the valve, remove the thermopile wires (TP, TP–TH) and the switch wires (TH, TP–TH). Clean the connectors with emery cloth or DeoxIT and tighten them firmly. Loose millivolt connections waste the same power a bad switch does.
11. **Reassemble.** Replace the logs exactly as photographed; a log blocking the pilot flame will hurt output. Reinstall the glass and check the gasket is seated and every latch is secure, because the sealed glass is part of the venting.
12. **Relight and inspect.** Open the shutoff and light the pilot. The flame should be steady and blue and wrap the top of the thermopile. Adjust the pilot screw if needed (guide p. 7).
13. **Re-test** after 5+ min warm: Test 1 and Test 2. Record the results in `findings.md`.
    - Test 2 ≥225 mV: done.
    - Test 2 still <225 mV: replace the thermopile, matching the part listed in the manual's parts list or printed on the old one.
14. **Leak check** any gas fitting you loosened with soapy water: bubbles mean a leak, so shut off the gas and call a technician.

## Safety
- If you smell gas at any point, stop, shut off the gas and ventilate.
- Never run the fireplace with the glass off.
- Valve replacement and gas pressure tests are jobs for a licensed gas technician.
