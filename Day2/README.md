# Day 2 - Good floorplan vs bad floorplan and introduction to library cells

## Theory

### Utilization Factor and Aspect Ratio
**Concept:** Utilization = ratio of standard-cell area to total core area; aspect ratio = core width:height.  
**Why it matters:** High utilization causes routing congestion; low wastes area.  
**Practical notes:** Use 60–75% utilization and adjust aspect ratio for better pin/power distribution.

---

### Pre-Placed Cells
**Concept:** Large macros or IPs (e.g., memories) are fixed before cell placement.  
**Why it matters:** Affects routing, power planning, and congestion.  
**Practical notes:** Define fixed regions and routing channels in DEF.

---

### Decoupling Capacitors
**Concept:** Stabilize voltage and suppress noise during switching events.  
**Why it matters:** Prevents IR drop and ground bounce.  
**Practical notes:** Include on-chip or package decaps and verify with PDN simulation.

---

### Power Planning
**Concept:** Design of power distribution networks (PDN) using straps, grids, and vias.  
**Why it matters:** Ensures reliable low-impedance power delivery.  
**Practical notes:** Plan coarse global and fine local rails; run IR-drop analysis.

---

### Pin Placement and Blockages
**Concept:** Pin and blockage locations affect routing and timing efficiency.  
**Why it matters:** Poor pin placement leads to congestion and timing issues.  
**Practical notes:** Review auto pin placement near critical paths and define keepout zones.

---

### Running Floorplan in OpenLANE
**Concept:** Define core size, utilization, aspect ratio, and macro placement.  
**Why it matters:** Floorplan sets the base for power and placement stages.  
**Practical notes:** Configure in `config.json` and inspect results in `init_floorplan.def`.

---

### Reviewing Floorplan Layouts
**Concept:** Floorplan outputs: DEF, LEF, and blockage files.  
**Why it matters:** Early visualization detects layout issues.  
**Practical notes:** Use Magic or KLayout to view macros, rails, and aspect ratio.

---

### Viewing Floorplan in Magic
**Concept:** Magic visualizes floorplan and verifies layer mapping.  
**Why it matters:** Helps debug DRC issues early.  
**Practical notes:** Load LEF/DEF with `sky130.tech` and check DRC results.

---

### Library Binding and Placement Optimization
**Concept:** Logical cells bound to physical library cells and placed within floorplan.  
**Why it matters:** Ensures correct mapping and connectivity.  
**Practical notes:** Verify no unmatched or missing LEFs.

---

### Placement Optimization
**Concept:** Minimizes wirelength (HPWL) and delay via timing-driven placement.  
**Why it matters:** Reduces timing violations and congestion.  
**Practical notes:** Tune cost functions; use incremental fixes for hotspots.

---

### Standard Cell Libraries and Characterization
**Concept:** Libraries define timing, power, and physical data (.lib, .lef).  
**Why it matters:** Accurate timing analysis depends on correct characterization.  
**Practical notes:** Generate .lib via SPICE simulations across process corners.

---

### Congestion-Aware Placement (RePlAce)
**Concept:** Uses density and connectivity optimization to reduce overflow.  
**Why it matters:** Improves routability and timing closure.  
**Practical notes:** Adjust density targets and smoothing factors.

---

### Cell Design and Characterization Flow
**Concept:** From schematic → layout → parasitic extraction → SPICE → .lib.  
**Why it matters:** Produces reusable, verified standard cells.  
**Practical notes:** Ensure DRC-clean layout and corner-based timing tables.

---

### Circuit and Layout Design
**Concept:** Sizing transistors, ensuring balance between delay and area, then implementing DRC-compliant layout.  
**Why it matters:** Affects performance and manufacturability.  
**Practical notes:** Maintain consistent pin alignment and cell height per PDK rules.

---

### Timing Basics
**Concept:** Setup/hold, clock-to-Q, and propagation delays govern correct sequencing.  
**Why it matters:** Defines STA timing closure conditions.  
**Practical notes:** Use equations like `Tclk ≥ Tclk→Q + Tcomb + Tsetup + Tskew`.

---

### Propagation Delay and Transition Time
**Concept:** Delay = input-to-output response time; slew = signal edge transition.  
**Why it matters:** Both affect timing, noise, and crosstalk.  
**Practical notes:** Observe delay tables indexed by slew and load in .lib files.

---

## Labs