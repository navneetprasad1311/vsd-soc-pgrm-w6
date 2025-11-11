# Day 3 - Design library cell using Magic Layout and ngspice characterization

## Theory
Day 3 bridges circuit-level understanding with layout and simulation. It introduces how a CMOS inverter is designed, laid out using Sky130 PDK, simulated in ngspice, and verified through DRC checks in Magic.

---

### 1. IO Placer Revision
- **Concept:** Optimize padframe/pin placement to minimize crossover and meet package routing needs.  
- **Why it matters:** Poor IO layout can cause routing congestion and timing degradation.  
- **Practical Notes:** Map package pins → die pads → PCB nets, considering power and signal distribution.

---

### 2. SPICE Deck Creation for CMOS Inverter
- **Concept:** SPICE deck defines circuit netlist, models, and stimuli for simulation.  
- **Why it matters:** It serves as the basis for functional and timing analysis.  
- **Practical Notes:** Include `sky130.lib.spice`, device sizes, voltage sources, `.tran` and `.measure` statements.

---

### 3. SPICE Simulation of CMOS Inverter
- **Concept:** Perform DC and transient analysis to observe logic levels and switching behavior.  
- **Why it matters:** Validates inverter performance (VOH, VOL, delay, power).  
- **Practical Notes:** Extract switching threshold (Vm) and propagation delays from waveform plots.

---

### 4. Switching Threshold (Vm)
- **Concept:** The point where Vin = Vout, indicating balance between PMOS/NMOS.  
- **Why it matters:** Determines noise margins and design symmetry.  
- **Practical Notes:** Adjust transistor sizing (Wp/Wn) to tune Vm near Vdd/2.

---

### 5. Static and Dynamic Simulation
- **Concept:** Static (DC) checks logic levels and leakage; dynamic (transient) checks delay and power.  
- **Why it matters:** Both together ensure correctness and performance.  
- **Practical Notes:** Dynamic power ≈ C·V²·f; include parasitics for accuracy.

---

### 6. Lab: Clone and Explore `vsdstdcelldesign`
- **Concept:** Use Git to obtain standard-cell inverter example and scripts.  
- **Why it matters:** Enables reproducible Sky130 experiments.  
- **Practical Notes:** Follow repository README, check PDK paths, and run included testbenches.

---

### 7. CMOS Fabrication Process (Conceptual)
- **Active Region Creation:** Defines transistor zones.  
- **Well Formation:** Forms N/P-wells for isolation.  
- **Gate Formation:** Defines transistor channel length.  
- **LDD and S/D Formation:** Improves reliability and drive strength.  
- **Interconnect Formation:** Builds local and global routing layers.  
- **Why it matters:** Each step contributes to transistor function and cell integrity.

---

### 8. Lab: Sky130 Layers, Layout and LEF
- **Concept:** Map logic layers to PDK-defined physical layers (poly, diff, metal).  
- **Why it matters:** LEF abstracts layout for placement tools.  
- **Practical Notes:** Generate `.lef` from Magic layout and verify pin geometries.

---

### 9. Lab: Create Std-Cell Layout and Extract SPICE
- **Concept:** Draw inverter layout in Magic, extract parasitics, and produce `.spice` netlist.  
- **Why it matters:** Enables LVS and post-layout simulation.  
- **Practical Notes:** Use `extract` and `cif2spice` commands in Magic.

---

### 10. Sky130 Tech File Labs
- **Concept:** Integrate Sky130 models and tech rules for accurate simulation.  
- **Why it matters:** Ensures layout and SPICE use foundry-verified parameters.  
- **Practical Notes:** Include model files, corner libraries, and proper `.include` paths.

---

### 11. Characterize Inverter using Sky130 Models
- **Concept:** Sweep voltage, temperature, and load corners (TT, SS, FF) to generate timing data.  
- **Why it matters:** Foundation for `.lib` cell characterization.  
- **Practical Notes:** Use `.measure` for delay/power; automate via scripts.

---

### 12. Magic Tool and DRC Rules
- **Concept:** Learn DRC rules, violation categories, and commands in Magic.  
- **Why it matters:** DRC ensures manufacturability and prevents silicon failures.  
- **Practical Notes:** Use `drc check`, fix violations, and note rule codes.

---

### 13. Sky130 PDK Introduction and Setup
- **Concept:** PDK provides tech files, SPICE models, LEFs, and rules.  
- **Why it matters:** Essential for layout, extraction, and simulation accuracy.  
- **Practical Notes:** Clone SkyWater PDK and configure environment paths.

---

### 14. Loading Sky130 Tech Rules in Magic
- **Concept:** Load tech files via `.magicrc` to use correct rulesets.  
- **Why it matters:** Ensures layer mapping and DRC behavior align with Sky130 standards.

---

### 15. Poly.9 DRC Error Fix
- **Concept:** Identify and correct spacing/overlap issues in poly layers.  
- **Why it matters:** Reinforces understanding of geometric DRC constraints.  
- **Practical Notes:** Modify poly geometry or spacing, then recheck DRC.

---

### 16. Poly Resistor Spacing and Tap Rules
- **Concept:** Maintain required spacing between resistors, diffusion, and taps.  
- **Why it matters:** Prevents parasitic coupling and unwanted junctions.  
- **Practical Notes:** Use guard rings and diffusion isolation.

---

### 17. DRC Challenge Exercises
- **Concept:** Decode and fix DRC rule errors; identify missing or incorrect rules.  
- **Why it matters:** Builds understanding of rule interpretation and tech-file debugging.  
- **Practical Notes:** Document fixes, track revisions, and verify rule correctness.

---

## Labs