# Lennox LMDV3530CNM – wall switch doesn't light the fireplace consistently

## Equipment
- Lennox LMDV3530CNM direct-vent gas fireplace (natural gas)
- SIT 820 millivolt gas valve
- Thermopile (not thermocouple) powers the valve; on/off via wall switch wired to TH and TP–TH terminals

## Symptom
- Pilot lights and stays lit.
- Wall switch only lights the main burner after several on/off tries.
- 2026-10-12: re-lit pilot after summer; switch worked once (after a few seconds' delay), then failed on the next off/on.

## Reference
- SIT 820 troubleshooting guide (FireParts): `sit-820-troubleshooting-guide.pdf` in this folder
  - Source: https://manuals.fire-parts.com/aws-assets/troubleshooting-guides-sit-820-systems-sit_820_troubleshooting-pdf?inline=true
  - Summary of specs and procedures: `sit-820-troubleshooting-guide-notes.md`
- Original 2024 notes: `lennox-gas-fireplace-not-lighting-old-research.pdf`

## Measurements – 2024-11-24

| Test | Setup | Reading | Spec | Result |
|---|---|---|---|---|
| Thermopile (separate check) | Burner off / on | 270 mV / 440 mV | ≥300–325 mV burner off | Burner-off reading low |
| Test 1 – thermopile | Knob at PILOT, all wires off except thermopile | 419 mV | ≥300 mV | Pass |
| Test 2 – operator head | Knob at PILOT, jumper TH ↔ TP–TH | 170 mV | ≥225 mV and < Test 1 | **Fail** |
| Coil resistance | All wires off, TP ↔ TH | 2.3 Ω | 2.25 ± 0.5 Ω (1.75–2.75) | **Pass** |
| Test 3 – thermostat circuit | Knob at PILOT, wall switch connected, ON | 208 mV | ≥145 mV and < Test 1 | Pass |

### Correction to the 2024 conclusion
The 2024 notes marked the 2.3 Ω coil reading as out of spec and concluded the valve needed replacing. The spec is 2.25 **±** 0.5 Ω, so 2.3 Ω is in spec. The guide (p. 14) condemns the valve only if Test 2 is below 225 mV **and** the coil is out of spec. The valve was not condemned.

### Interpretation
- Healthy coil plus a Test 2 voltage that sags under load points to a marginal power source: a weak or dirty thermopile, or a pilot flame not fully wrapping it.
- Test 3 (208 mV) vs Test 2 (170 mV) implies roughly 1 Ω in the switch circuit (estimate derived from the readings, not measured directly). That is a lot for a millivolt system.
- A marginal thermopile combined with a variable-resistance switch explains "works after several tries."

## Tests – 2026-10-12

| Test | Result | Meaning |
|---|---|---|
| Jumper across TH ↔ TP–TH at the valve (switch bypassed), pilot warm, knob ON, ~10 tries | **Lit every time** | Valve, coil and thermopile can light the burner. Fault is in the wall switch circuit: the switch, the wire run, or the terminals. |
| Jumper at the wall box (switch removed, wires joined) | **Lit** | Wire run and valve-end connectors are OK. Fault is the switch itself. |
| Spare regular (120 V AC) wall switches swapped in | 5 of 6 tried did **not** light; 1 did | Ordinary switch contact resistance is too much for this marginal millivolt circuit (see below). |
| Test 1 – thermopile, no load (knob PILOT, switch wires off), before cleaning | **416 mV** | Pass (≥300). Same as 2024 (419). |
| Test 2 – thermopile loaded (jumper TH ↔ TP–TH), before cleaning | **170 mV** | **Fail** (<225). Identical to 2024: the thermopile still sags under load. Baseline for comparison after cleaning. |
| Test 2 – after cleaning the thermopile and thermocouple with 400 grit | **188 mV** | Up 18 mV from 170, but still **fails** (<225). Cleaning helped a little; the thermopile itself is weak. Next: replace the thermopile. |
| Test 2 – about a week after cleaning, while turning the pilot screw | **172–175 mV** | Still **fails** (<225), and back down from 188. Adjusting the pilot screw made **no change**. |
| Switch resistance, ON, disconnected (meter on Ω) | Working spare switch: **0.6 Ω**. Original wall switch: **~3.8 Ω** | The original switch has more resistance than the valve coil itself (2.3 Ω), so it starves the coil. 0.6 Ω is enough to work but leaves little margin. Readings include meter-lead resistance; short the leads together to see how much to subtract. |

### Why most regular switches fail here
- Ordinary AC light switches rely on line voltage and current to break through the thin oxide film on their contacts. At a few hundred millivolts and tens of milliamps, that film never gets broken, so contact resistance stays high and varies from flip to flip.
- This circuit has almost no margin. The coil is about 2.3 Ω, the thermopile already sags under load (Test 2: 170 mV vs a 225 mV spec), and even a few tenths of an ohm in the switch can drop the coil current below what's needed to open the valve.
- If a switch is wired through its push-in (backstab) holes instead of the screw terminals, that adds more resistance.
- The fact that 5 of 6 switches fail is itself evidence that the thermopile is weak. A healthy thermopile usually tolerates an ordinary switch.

## Next steps
1. ~~Inspect the wall switch box~~ and ~~jumper at the wall~~: done 2026-10-12; the switch is the fault.
2. **Stress-test the one switch that worked.** Wire it on the screw terminals, not the push-in holes. Cycle it about 20 times, waiting about 30 s between tries. If it's 20 for 20, it's a usable fix for now.
3. **Better long-term switch.** Buy a switch rated for millivolt or low-voltage DC, with gold or silver contacts. These are sold as "gas fireplace wall switches" or "millivolt switches".
   - ~~Fire-Parts.ca Two-Way Gold Contact Switch (FP0514)~~: **won't fit a wall box.** The product photos show a small Carling snap-in panel rocker (about 3 cm wide, spade tabs, no mounting strap), made for fireplace control panels.
   - **Pick: ATX-LED AL-WS-R3** decorator-style (Decora) rocker on Amazon.ca, about $30 CAD (search-result price; confirm at checkout). https://www.amazon.ca/ATX-LED-AL-WS-R3-Fireplace-Switch/dp/B09T8M2551
     - Rated for low voltage including millivolt, AC or DC, 2 A. Advertised as low-resistance with self-cleaning contacts.
     - Decora form factor fits a standard single-gang box and takes a standard Decora (rectangular-opening) wall plate. Plate likely not included.
     - It's a 3-way switch; wire it as on/off using the common terminal and one traveller terminal.
   - Alternatives on Amazon.ca: Durablow WS1001-S kit (stainless plate and 20 ft wire included, about $45 CAD); Allparts AB-MVWS kit (with cover, about $75 CAD on Amazon.ca, about $13.50 USD from the US seller). Neither listing says the contacts are gold. Avoid the SkyTech SKY-WS (nickel-plated contacts).
   - After installing, verify: switch resistance ON should be about 0.1 Ω (after subtracting meter-lead resistance), well below the 0.6 Ω spare.
   - **Decision 2026-10-12: not buying a millivolt switch; budget is under $15 CAD.** No wall-box millivolt switch was found in Canada under $15; the cheapest, the Allparts AB-MVWS at $13.50 USD from a US seller, comes to about $18+ CAD before shipping. Plan instead:
     - Keep the 0.6 Ω spare switch, wired on the screw terminals.
     - Optional: buy 2–3 basic single-pole switches (a few dollars each at Home Depot or Canadian Tire), measure each with the ohmmeter, and keep the lowest.
     - Clean the thermopile and pilot to restore margin, which makes switch resistance less critical.
4. **Optional meter comparison.** Measure each switch on ohms, ON and disconnected, and flip it several times. Compare the one that works against the ones that fail; expect the failing ones to read higher or to jump around.
5. **Restore margin at the thermopile.** Full procedure and tools list: `thermopile-cleaning-procedure.md`. Clean the pilot hood, orifice and thermopile, and check the pilot flame engulfs the thermopile tip. Re-run Test 2 with the pilot warm for 5+ minutes. If it's still below 225 mV, replace the thermopile. This makes the system tolerant of switch wear again.
6. **Later, if it becomes unreliable again:** clean the pilot hood, orifice and thermopile, and check the pilot flame engulfs the thermopile tip. Re-run Tests 1–3 with the pilot warm for 5+ minutes. Replace the thermopile if Test 2 stays below 225 mV.

## Pilot flame observation (2026-10-12)
- Photo: `pilot-flame-labelled.jpg` (from `pilot-on-thermopile.HEIC`).
- The flame is soft, small and curling. It runs up one side of the thermopile but doesn't wrap the whole top. The thermocouple gets good flame.
- A thermopile only heated on one side produces less power, which likely explains much of the low Test 2.
- **Next, before buying a thermopile: raise the pilot flame.**
  1. The pilot adjustment screw is the small brass screw on top of the valve marked PILOT (guide p. 7).
  2. Turn it counter-clockwise ¼ turn at a time.
  3. Wait 3–5 min after each adjustment, then re-run Test 2.
  4. Goal: Test 2 ≥225 mV, with a steady blue flame wrapping the top ~½ in. of the thermopile.
  5. Stop if the flame turns yellow, lifts off the hood, or roars.
- If more pilot gas doesn't produce a strong flame, the pilot orifice may be partly blocked, or the bent or rusty hood may be misdirecting the flame. Gas pressure is the other possibility; that's a technician check.

## Sanding technique note
- Wrapping a strip around the rod and pulling it back and forth ("shoe-shine") is the correct method.
- Judge by result, not pressure: the sanded area should be uniform clean metal with no dark film or spots.
- For more pressure, fold the paper around the rod and pinch it with your fingertips while twisting.
- The sheath is steel, and hand-sanding at 400 grit won't damage it.
- Cleaning gave only +18 mV, so the flame is the bigger lever.

## Thermopile replacement
- **Part: Lennox 60J79** "Pilot Generator [Thermopile]", item 15 on the LMDV-3530CNM parts diagram.
- Prices found (USD; no Canadian listing confirmed):
  - Appliance Factory Parts: about $88. https://www.appliancefactoryparts.com/fireplaces/lennox/lmdv3530cnm.html
  - Fireplace Parts World: about $88–104. https://www.fireplacepartsworld.com/brands/lennox/lmdv3530cnm/2082192
  - Lennox Hearth Parts (official): about $206. https://www.lennoxhearthparts.com/cgi/display.cgi?item_num=LMDV-3530CNM
  - Amazon.com: "IHP OEM 60J79". https://www.amazon.com/IHP-OEM-Fireplace-Thermopile-Original/dp/B07JZVR1BW
- Generic 750 mV, 24 in. thermopiles cross-referenced to 60J79 exist and are cheaper, but fit and length aren't verified.
- Complete pilot assembly (thermopile, thermocouple, hood, igniter), Lennox 67L70: about $260 USD. Consider it if the bent or rusty pilot hood turns out to be aiming the flame badly.
- Difficulty: moderate DIY with no gas fittings opened.
  1. Gas OFF.
  2. Disconnect the two thermopile wires at the valve (TP, TP–TH).
  3. Undo the nut or clip holding the thermopile to the pilot bracket.
  4. Thread the new one through the same path.
  5. Reconnect the wires firmly and re-run Tests 1 and 2.

## Safety
- Keep the gas knob OFF while cleaning parts.
- If you smell gas, stop.
- Gas pressure testing and valve replacement are jobs for a licensed gas technician.

## Log
- 2024-11-24 – Initial testing (see table above).
- 2026-10-12 – Reviewed 2024 data and corrected the coil interpretation. Jumper test at the valve lit every time, pointing to the switch circuit. Next: jumper-at-the-wall test.
- 2026-10-12 – Jumper at the wall box lit the burner, so the wiring is OK and the switch is the fault. Of 6 spare regular switches tried, 5 failed and 1 worked. Next: stress-test the working switch, consider a millivolt-rated switch, and clean or replace the thermopile for margin.
- 2026-10-12 – Switch resistance (ON, disconnected): working spare 0.6 Ω, original ~3.8 Ω. Picked the Fire-Parts.ca gold contact switch (FP0514) and wrote the thermopile cleaning procedure.
- 2026-10-12 – FP0514 turned out to be a snap-in panel rocker that won't fit a wall box. Switched the pick to the ATX-LED AL-WS-R3 Decora millivolt rocker (Amazon.ca).
- 2026-10-12 – At ~$30 CAD the AL-WS-R3 was over budget, and nothing suitable was found under $15. Decided to keep the 0.6 Ω spare switch and clean the thermopile instead.
- 2026-10-12 – Pre-cleaning baseline: Test 1 = 416 mV, Test 2 = 170 mV, unchanged from 2024. Next: clean the thermopile and pilot (`thermopile-cleaning-procedure.md`), then re-test. If Test 2 is still <225 mV, replace the thermopile.
- 2026-10-12 – Cleaned the thermopile and thermocouple (400 grit). Test 2 rose to 188 mV, still under 225. Next: replace the thermopile. Identified the part as Lennox 60J79 (about $88–104 USD from aftermarket sellers).
- 2026-10-12 – Pilot flame photo: the flame is weak and runs up only one side of the thermopile. Next: raise the pilot flame with the adjustment screw and re-test before buying a thermopile.
- ~2026-10-17 – Test 2 = 172–175 mV. Turning the pilot screw didn't change it. Open question: did the flame itself get bigger?
  - Flame grew but mV didn't → bad thermopile; replace it (60J79).
  - Flame didn't grow → pilot gas restriction (blocked orifice or low gas pressure); technician.
- ~2026-10-17 – **Flame did not visibly change** with 2 full counter-clockwise turns. The screw was returned to its original position. This points to a pilot gas restriction downstream of the screw (partly blocked pilot orifice or pilot tube) or low incoming gas pressure, rather than only a weak thermopile.

## How to judge whether the pilot flame is weak
| | Healthy | Weak (yours, per photo) |
|---|---|---|
| Shape | Crisp, steady blue jets out of the hood ports, about 1 in. long | Soft, small, curling or wandering |
| Coverage | Engulfs the top ~½ in. of the thermopile and the thermocouple tip | Runs up one side of the thermopile only |
| Colour | Blue with a distinct inner cone; maybe faint yellow tips | Pale, wispy blue, no defined cone |
| Response to the pilot screw | Clearly grows or shrinks within ½–1 turn | No visible change after 2 turns |
| Test 1 (thermopile, no load) | Typically about 500–750 mV with a good flame | 416 mV |

Definitive check: a manometer on the valve's inlet pressure tap (NG ≥5" W.C. with the burner on), done by a technician, plus inspecting and cleaning the pilot orifice.

DIY clue: if the main burner flame looks full and normal and other gas appliances work, inlet pressure is probably fine, which points to the pilot orifice specifically.

### Correction (~2026-10-17)
The "weak flame" call above leaned too hard on one photo.
- Curling alone isn't evidence of a weak flame. This flared hood throws flames sideways, and they curl against the shield.
- A distinct darker-blue inner cone with a lighter outer flame means good combustion.
- What's still solid: the flame doesn't wrap the thermopile, the readings are low, and the screw changed nothing.
- **Gas supply is probably fine.** The main burner looks normal, and the BBQ, water heater, furnace and stove all work.
- Possible reason the screw did nothing: it may already have been fully open. Check by turning it **clockwise** 1 turn: the flame should shrink.

### Pilot screw check (~2026-10-17)
- Turning **clockwise** shrinks the pilot flame and eventually puts it out, so the screw works.
- Turning counter-clockwise past the original position changed nothing. The screw was already at or near **full open**, and the pilot flame is at its maximum.
- Any limit is downstream of the screw: the pilot orifice or hood. Or the flame is simply normal size, and the thermopile is the weak part.
- Screw position going forward: turn counter-clockwise until the flame stops growing, then stop.
- The lighter test below decides between the two.

### Lighter test: is it the thermopile or the flame?
With the pilot lit, knob at PILOT, and the Test 2 jumper on:
1. Hold a long-reach butane lighter flame on the **other side** of the thermopile's top for 30–60 s.
2. Watch the meter.
3. Keep the lighter flame off the wires, and don't leave it in place longer than needed.

Results:
- **Rises well (toward 225+ mV):** the thermopile can make the power; the pilot flame isn't giving it enough heat (orifice, hood or aim).
- **Barely moves:** the thermopile is worn out. Replace the thermopile (60J79).

### Torch test result (~2026-10-17)
- Test 2 setup with a **propane torch** on the thermopile: climbed quickly from about 173 mV to **280 mV**, above the 225 spec.
- Meaning: the thermopile can still produce enough power when it's well heated. The main problem is that the **pilot flame isn't delivering enough heat to it**: the flame runs up one side only.
- Caveat: a propane torch is much hotter than a pilot flame, so this doesn't prove the thermopile is in like-new condition. It does show it isn't dead.
- Don't hold a torch on it for long; excess heat can damage it.

### DIY heat-delivery checks (~2026-10-17)
- The thermopile is seated straight and doesn't move.
- All 3 hood openings were blown out again.
- The flare doesn't appear bent.
- **No change in the flame or Test 2.**

### Revised conclusion: replace the thermopile
- Surface oxidation only slightly reduces heat transfer into the sheath, and sanding already addressed it: +18 mV, which didn't last.
- The usual aging failure is **internal**: the junctions inside degrade, so output falls and internal resistance rises. Sanding can't fix that.
- Signature here: 416 mV with no load collapses to about 173 mV on the 2.3 Ω coil. That works out to roughly 3 Ω of internal resistance, which is high and points to a worn thermopile.
- Healthy units typically make about 500–750 mV with no load in a normal pilot flame.
- The torch result (280 mV) doesn't contradict this. A torch puts in far more heat than any pilot, so even a worn thermopile can pass under it.
- The pilot itself looks to be working as designed:
  - clean blue flame with a defined inner cone
  - adjustment screw works and is at full open
  - hood openings clear
  - thermopile seated properly
  - house gas supply fine
- **Decision: replace the thermopile, Lennox 60J79.** This is DIY with no gas fittings opened.
- If Test 2 is still <225 mV with the new thermopile: have a technician clean the pilot orifice.

### Thermopile removal: access (~2026-10-17)
- Photo: `thermopile-under-hood-labelled.jpg` (from `thermopile-under-hood.HEIC`). No nut was found from the control compartment.
- There's a large hex nut or body under the pilot shield, recessed, so a wrench won't fit.
- **Not yet confirmed whether that hex holds the thermopile or is the pilot gas fitting.**
- Before loosening anything, check what comes out of its bottom:
  - two wires → thermopile (safe to loosen)
  - a small metal tube → pilot gas connection (don't loosen)
- Access options for a recessed nut: crowfoot wrench on a ratchet extension, thin open-end ("ignition") wrench, or unscrew the pilot bracket (bracket screw visible) and lift the assembly for room.
- No need to remove the thermopile before ordering; the part number (60J79) comes from the model's parts list.

### Lennox installation manual (P/N 850,029M Rev. G): what it covers
Local copy: `lennox-lmdv-33-35-40-installation-manual.pdf`. Source: https://manuals.fire-parts.com/aws-assets/lennox-lmdv-33-lmdv-35-lmdv-40-lmdv-33_lmdv-35_lmdv-40_install-pdf.pdf?inline=true

- **No thermopile removal procedure.** It only covers pilot assembly removal, for gas conversion (p. 36, Fig. 68):
  1. Remove the igniter retainer clip and the igniter, carefully because the igniter breaks easily.
  2. Remove the screw securing the pilot assembly to its mounting bracket.
  3. Back off the flare nut on the pilot gas line. Don't use pipe compound on flare fittings when reassembling.
  4. Leak-test afterward.
- **Pilot flame spec (p. 25, Fig. 51, SIT pilot):**
  - steady, not lifting or floating
  - blue, with traces of orange at the outer edge
  - top **3/8 in.** of the thermopile engulfed
  - top 1/8 in. of the thermocouple engulfed
  - **flame projects about 1 in. (25 mm) beyond the hood at all three ports**
- Gas pressures (p. 35): manifold 3.5" W.C. for NG.

### Pilot flame length vs spec (~2026-10-17)
- User estimate: the flame extends about **3/4 in.** beyond the hood; the spec is about 1 in.
- That's somewhat short, which suggests mildly reduced pilot gas, most likely a partly restricted pilot orifice since the screw is already fully open. It's borderline: eyeballing a curling flame is imprecise.
- Likely both factors contribute: a slightly short pilot flame, and a worn thermopile with high internal resistance (416 mV no-load collapsing to about 173 mV).
- Best path: have a technician clean or check the pilot orifice (needs the pilot flare nut opened) and replace the thermopile (60J79) in one visit.

### Thermopile mounting (from user inspection, ~2026-10-17)
- Confirmed by tracing the wires: the large dark hex under the pilot shield is the thermopile.
- A silver hex nut directly below it turns independently. It's most likely a jam nut on the thermopile's threaded body, clamping it to the bracket.
- The firebox is sealed (direct vent), so the thermopile wires probably pass to the control compartment through a sealed grommet, not an open hole.
- Probable removal:
  1. Disconnect the wires at the valve.
  2. Unscrew the jam nut.
  3. Lift the thermopile up out of the bracket.
  4. Draw the wires through.
  The manual doesn't confirm this.
- Two-wrench access isn't possible in place. Removing the pilot assembly (one screw, plus a second hard-to-reach fastener behind it) would give access but may also mean opening the pilot gas flare nut.

## Options from here
0. **DIY first (free), since the torch test points at heat delivery:**
   - Gas off and cool.
   - Check the thermopile is fully seated and upright in its bracket, not slipped down or tilted away from the hood.
   - Clear the hood openings, especially the one facing the thermopile.
   - Look at the bent flare on the hood's front and right side: if it's bent so it deflects flame away from the thermopile, *gently* straighten it.
   - Relight and check whether the flame now reaches the top of the thermopile. Re-run Test 2.
1. **Gas technician visit:** clean the pilot orifice and measure inlet pressure. Fixes the root cause if it's a restriction. A new thermopile may still be needed afterward.
2. **Replace the pilot assembly (Lennox 67L70, about $260 USD):** new orifice, hood, thermopile and thermocouple in one part. Involves disconnecting the pilot gas tube, so a leak check is required. Technician recommended.
3. **Thermopile only (60J79, about $88 USD):** cheapest, but likely **won't** fix it if the flame is starved.
