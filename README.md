# SSF.py — PKEF: Solar System Federation

### GmansQP Stellar Ark — a nomadic, life-bearing, multi-star "solar-system ship"

`SSF.py` is a complete, single-file, standalone **interactive 3D digital twin** of the
GmansQP Stellar Ark described in [`officialgoal.md`](officialgoal.md). It treats an
entire solar system as a modular, self-propelled spacecraft and models — at true
metric scale — its propulsion, quantum-photonic compute core, 5D glass archive,
light-speed communicator, docking, and growth.

Every headline number is **derived from a named law of physics or information theory
and checked at runtime** (`python SSF.py --proof`). Where the blueprint asked for
something a real material or the diffraction limit can't do, the model is reconciled
to what physics actually allows and the reason is shown — see *Honest engineering
notes* below.

> See [overview.md](overview.md) for the conceptual architecture and the science of
> each subsystem. The committed specifications are the **optimized family** —
> `optimizedinfornmational1–5.md` (overview §8) — which rebuild every subsystem at
> its physics optimum: the model runs Config **O** (the effort-realistic tier);
> O+/O++/Ω and U-series are named stretch/target bounds, and the IQEC's Mode S is
> carried as directive-premise (ε-conditional), never as demonstrated physics.

---

## Requirements

- Python 3.9+
- `numpy`
- `pygame` (only needed for the interactive viewer; the CLI checks below run headless)

```bash
pip install numpy pygame
```

The renderer is a pure-Python software rasterizer (numpy-vectorized painter's
algorithm + normal-based Lambert flat shading + backface culling + mesh- and
face-level screen-space LOD culling) — no GPU or external assets required.
Background gradient and starfield use numpy bulk pixel operations for
performance.

---

## Running it

```bash
python SSF.py               # interactive 3D viewer (default)
python SSF.py --selftest    # headless build + physics + entanglement + proof checks
python SSF.py --feasibility # real-world feasibility report
python SSF.py --proof       # prove the math holds (116 runtime-verified lemmas, 18 groups)
python SSF.py --export-obj  # export the model as OBJ + MTL files
python SSF.py --hit         # run Tensor-Flower Comet Redirection System (hit.py v5.1)
                             #   [--hit-ns N] Monte Carlo sims per campaign (default 300)
                             #   [--hit-perturb] enable n-body perturbations (solar system)
                             #   Opens the NATIVE pygame dashboard in the SSF window:
                             #   12 tabs (SCOPE, IMPACT, 3D VIEW, STATS, CONSOLE,
                             #   CONFIG, SALVO, TRAJECTORY, SPHERE NAV, 3D SPHERE,
                             #   PARALLEL, PARALLEL 3D) -- no browser, no server
```

`--selftest`, `--feasibility` and `--proof` are headless and print to the terminal;
they're the fastest way to see what the model does without opening a window.

In the interactive viewer, press **`F11`** to toggle fullscreen mode. The window is
also resizable by dragging its borders.

---

## The five interactive modes (press `TAB` to cycle)

| Mode | What it shows |
|------|----------------|
| **PREVIEW** | Navigable 3D view of the whole ark at true scale, with a component inspector, exploded/assembly/section views, and a scale bar. |
| **TEST DRIVE** | Live physics: planets orbit under real gravity, the Caplan thruster fires, the sail adds photon-pressure thrust, the quantum core accumulates reads. |
| **VOYAGE** | Eight-phase approach to a target star navigated on the reference **hit.py** course engine: RK4 escape hyperbola out of the home well (v_inf ≈ 15 km/s), ballistic cruise, RK4 capture arc into the target well (backward-propagated onto the 3162 AU bind orbit, ≈14.5 km/s capture burn), with 8 equal-time approach gates carrying dv-correction Jacobians. The ship marker rides the integrated course, not a scripted line. |
| **SHOWCASE** | 15 subsystems enlarged to fill the view at true 1:1 aspect: QCPU chip, 5D glass disc, IQEC communicator, Earth (Green Planet), spiral transfer, Hohmann transfer, retrograde descent, cone thruster, GM3QC 3-qubit chip, Tensor-Flower comet redirection, Ship Engine (HOHEV-H2 marine rotary), Super Glass Pyramid, Extended Solar System (docking / terraforming / resourcing preview), Infinity Core Grain, Eternal Apex Pyramid. |
| **INFO** | The full engineering specification, including the three **PROOF** sections and their full derivations. |

### Controls

**Global:** `TAB` cycle modes · `D` toggle digital QCPU fallback mode (default **OFF** = quantum/photonic) ·
`I` info · `H` help · `L` labels · `R` reset · `F11` fullscreen toggle · `ESC` quit

**PREVIEW:** drag = orbit · right-drag = pan · wheel = zoom · click a part to pin it ·
`1` full · `2` exploded · `3` assembly · `4` section · `E` explode · `X` section ·
`[` `]` step assembly · `A` all · `C` clear

**TEST DRIVE:** `SPACE` toggle thruster · `,` / `.` time-warp

**VOYAGE:** `SPACE` engage docking · `,` / `.` approach speed

**SHOWCASE:** `1`-`0` select subsystem (items 1-10) · `[` `]` cycle all 15 items ·
drag = orbit · wheel = zoom · `SPACE` play/pause Earth greening (item 4) ·
`,` / `.` time-warp · `G` reset greening · `ENTER` drill into sub-units (atomic scale + math proofs) · `BACKSPACE` exit · `B` launch native Tensor-Flower dashboard

---

## Digital QCPU fallback mode (`D`, default OFF)

The QCPU normally reads out over its photonic QND channel (the behavior described
throughout this doc). Pressing `D` engages a second, independently-modeled path: a
classical binary (CMOS) shadow register per qubit, clocked like a real cryo-CMOS
control ASIC (Intel Horse Ridge II–class, 3.0 GHz at the 4K stage, qubits stay at
`chip_temp_mK`). This mirrors how real fault-tolerant quantum computers keep a
classical control/monitoring path alongside the qubits.

- **Throughput ≈ 8.41×10¹¹ reads/s** (clock / cycles-per-read × 1,121 qubits, parallel bus — ~8× faster than photonic QND)
- **Error ≈ 2.1×10⁻¹⁷** (Hamming(7,4) over a 1×10⁻⁹ raw cryo-CMOS bit error rate)
- Reading the classical shadow register causes **no QND backaction** — coherence is
  preserved while the mode is engaged. The trade is **precision and quantum capability**
  (binary thresholding vs continuous amplitude; cannot prepare, entangle, or read out
  superposition), not throughput — it's a monitoring/safe-mode fallback, not a quantum replacement.
- Visible live in **TEST DRIVE**, **VOYAGE**, and **SHOWCASE** (QCPU chip) HUDs, and
  proven in **INFO** under "DIGITAL QCPU FALLBACK MODE".

---

## The proof system (`--proof`)

The model is a *provable* digital twin. Groups of lemmas re-derive every headline
number and assert it against the value the program uses. If any lemma ever drifts,
`--selftest` and `--proof` fail loudly.

| Group | Lemmas | Covers |
|-------|:------:|--------|
| **QCPU** | 14 | Readout clock, standard quantum limit, LDPC error suppression, QND backaction read budget, Jaynes–Cummings entanglement, concurrence, distillation, throughput scaling, readout closure (g/Δ, Purcell), tier ladder (O/O+/O++/U/U+/U++), Omega qudit, mK energy budget. |
| **5D glass + light-computation pyramid** | 9 | Depth closure, diffraction limit, voxel count, 5D multiplexing, the exact capacity identity, density bound, photonic throughput, light-speed causality, and the miniature `GlassDisc5D` simulation obeying the identical voxel-count/bit-packing identities at reduced N. |
| **Pyramid synchronicity** | 8 | TIR light trap (Snell's law), resonance Q factor (optical cavity), synchronicity residual (Phi growth > 0), presidual (vacuum zero-point energy), optical current (P/Z_0), light trace (TIR path), Cauchy dispersion (spectral sorting), symphony closure (Phi^n -> Omega). Ties Somethingfromnothing.md concepts to CODATA constants and Simulation.py optical laws. |
| **Ship mechanics** | 6 | Gyro burst limit, flywheel momentum, CMG thrust-vectoring, rail-ejection recoil, disc spin/read mechanics, sail radiation pressure. |
| **Operation Green Planet** | 9 | Earth to scale, evaporation energy budget, saturation volume, sea-level impact, greening timeline, biomass growth, cost closure, relativity checked, life-bearing-world stats (ET feedback, CO₂, rainfall, albedo). |
| **Optimized Green Planet** | 10 | Mk II thin-shell hull, delivery rate law (ρ·C·u·Δq), capture stack, trigger doctrine, inland seas (Qattara+Chotts), delivered volume, mobile fleet reach, pellet/FMNR seeding, brine-as-product P&L, bottleneck register. |
| **Solar-system flight** | 7 | Kepler III + circular speed, vis-viva, Hohmann transfer, spiral apsis-walk, retrograde descent, RK4 course-engine faithfulness, engine identity (`SSF.rk4_propagate`/`pf_2d` return bit-identical states to hit.py's own `prop`/`pf`, on hit.py's `BODIES` table). |
| **Cone thruster** | 3 | Photon-pressure liner thrust, 3-mode ordering, shape-shifting steering. |
| **IQEC communicator** | 12 | No-FTL, photon rate from laser power, Friis link budget, photon-limited channel capacity, consumable entanglement, fidelity >99%, QKD key rate, superdense ≤2× bound, Mode L rate ladder, Mode S sensitivity law (directive-premise), memory-vs-hop doctrine (T_mem ≥ 2·t_hop), replay ladder, causality engineering (Tolman guard). |
| **Symphony of Self-Differentiation** | 1 | Executable proof: True Nothing bootstraps growing structure via recursive self-reference (growth, seed, closure verified). |
| **Majority-voting qubit read** | 1 | Repetition-code error suppression: M reads → effective error drops exponentially (binomial tail bound). |
| **Hybrid classical-quantum OS** | 1 | Numpy state-vector quantum emulator: Bell state, VQE iteration, classical-quantum command delegation. |
| **Digital QCPU fallback mode** | 1 | Classical CMOS shadow-register throughput + Hamming(7,4) error suppression, and the quantum/digital toggle contrast. |
| **Tensor-Flower comet redirection** | 4 | Newton shooting convergence, RK4 energy conservation, STM tensor symmetry, gate correction improvement. |
| **Solar-system steering + binary docking** | 8 | Combined forward thrust from 4 systems (Caplan 65% + Cone 25% + Sail 10%), steering balance (lateral < 2% of forward — one asymmetric cone segment's share, not the whole ring), steering authority bounded by balance, thrust fractions sum to 1, binary gravitational capture (binding energy > KE), binary orbit period (Kepler III), combined 2-star thrust (≈4x Caplan), Hill stability + resource merge (11 planets, 2 Dyson swarms). |
| **Human archive + simulated universe housing** | 4 | Pyramid level floor area (same shrinking cross-section the facet-band showcase uses), human-data archive sized against a labeled planning figure using the *same* glass disc already proven for storage, simulated-universe compute budget *derived* from the *same* QCPU throughput already proven for readout (not asserted as infinite), per-slot state space via the *same* read-language-overlay mechanism the disc uses. |
| **Optimized hardware** | 8 | Grain voxel density + capacity, apex pyramid geometry/mass, apex compute ceiling, chip tier ladder closure, QCPU power/dissipation, manufacturing blueprint process stations, LC path latency, apex-geometry render footprint equals engineering footprint. |
| **Optimized ark doctrine** | 10 | Variable v_e mission dial (F=2P/v_e, ṁ=2P/v_e²), Svoronos tug + statite bias, engine-star L/M selection (solar→BH pod), tow-bond transmission limit, galactic flyby schedule, lever-arm encounter shaping, gravity tractor, exchange capture ("the cheat"), 4-rule multi-star stability law, deflect-first + SGL + star-lift breeder. |

**116 lemmas total across 18 groups — all currently PASS.** The selftest also verifies the GM3QC showcase build (344 meshes, 3 sub-units), Tensor-Flower integration (382 meshes, 3 sub-units, Newton convergence, STM symmetry, 21-body solar system), the Ship Engine reference showcase (303 meshes, 4 sub-units), the Super Glass Pyramid showcase (168 meshes, 4 sub-units), the Extended Solar System showcase (256 meshes, 4 sub-units), the QCPU's human archive/multiverse sub-unit (73 meshes), and full liability waiver integration (1019 lines loaded). They also render in **INFO** mode under the
"… PROOF — THE MATH HOLDS" sections and the other dedicated sections.

---

## What's modeled (all at true metric scale)

- **Central star** — Sun analogue (real solar radius, mass, luminosity).
- **Caplan thruster** — Dyson-powered plasma jet + counter-jet; derived thrust/accel.
- **Dyson swarm** — full-luminosity capture feeding the thruster and core.
- **Super Glass Pyramid** — houses the GmansQP quantum-photonic compute core. Synchronicity physics: TIR light trap (Snell's law), resonance Q (optical cavity), residual (Phi growth), presidual (vacuum ZPE), optical current (P/Z_0), light trace (TIR path), Cauchy dispersion, symphony closure — 8 proof lemmas tying Somethingfromnothing.md to CODATA constants. Also its own full-detail showcase (item 12, 168 meshes, 4 sub-units).
- **Human data archive + simulated universe housing** — two goals housed on the *same* hardware, nothing new invented: a redundant glass-disc array on the pyramid's 12 levels backs up a labeled human-data planning target (3.0 ZB, ≈3.49×10⁵ discs at 3× redundancy, using **~8.5×10⁻⁸%** of total floor area); the QCPU's proven throughput bounds a *derived* (not asserted-infinite) compute budget of 101,909 concurrent bounded "stable universe" simulation slots. 4 proof lemmas (`archive_multiverse_proof()`). QCPU showcase sub-unit 10 (73 meshes).
- **GmansQP QCPU** — 1,121-qubit chip + an ultra-optimized 3-qubit variant,
  committed at **Config O** of the optimized chip spec (`optimizedinfornmational2`
  v3.0): Ta-on-Si transmons, Purcell-budgeted readout closure (κ/2π 8.33 MHz,
  F = 5×10³, T₁ = 343 µs), 90.9 M accurate reads/s/qubit → **1.02×10¹¹ reads/s
  chip-wide**, ~10 µW @ 20 mK / ~15 kW wall, 36 logical qubits on the gross-code
  qLDPC layer. Stretch tiers O+ (1.65 T/s), O++ (3.30 T/s), O++Ω (6.59 Tb/s)
  and the 3-qubit U-series are verified bounds, not committed claims — full
  tier ladder in overview §8.2.
  The showcase spec panel carries a full **VERIFIED COMPUTE STATS** block (read
  rates, error/fidelity chains, WDM lane totals, latency, glass-compute ceiling,
  universe slots — every number cited to its lemma) and a **manufacturing
  blueprint**; sub-drilldown 11 is the exploded 4-layer fabrication stack with
  8 numbered process stations (wafer prep → TFLN → LC photonic → CMOS assembly).
- **GM3QC** — standalone 3-qubit chip showcase (reduced from QCPU, 344 meshes, 3 drill-down sub-units with math proofs).
- **Tensor-Flower Comet Redirection System** — full hit.py v5.1 integration: Newton shooting, 12-gate Jacobian Dv corrections, Monte Carlo impact dispersion, STM tensor, projectile energy model (Tsiolkovsky), 5-barrel swarm, parallel scope, target orbit prediction, 21-body solar system (1 Sun + 20 planets + moons). CLI: `--hit [--hit-ns N] [--hit-perturb]`. In-viewer key `B` launches the native pygame dashboard (`tf_dashboard.py`) with 12 interactive tabs rendered inside the SSF window. Showcase item 10 with 3 drill-down sub-units (gate Jacobians, Monte-Carlo dispersion, projectile energy model).
- **Solar-system flight (showcase 5/6/7)** — the three transfer modes from the `landing.jpg` blueprint: spiral apsis-walk, Hohmann transfer, straight retrograde descent. hit.py is the engine for all three, not a model of it: `SSF.rk4_propagate`/`pf_2d` *are* hit.py's `prop`/`pf` called on hit.py's `BODIES` gravity table (bit-identical, lemma 7), the Hohmann map's Newton shooter re-derives the closed-form ellipse to ~1e-8, and the descent runs the same RK4 with Earth's µ installed. All 16 blueprint callouts are named meshes — solo one in PREVIEW to isolate it — and `--selftest` asserts each one is present in the map it belongs to.
- **Ship Engine (HOHEV-H2)** — 240,000 DWT hydrogen cargo ship (400m LOA, 61m beam, bulbous bow): 8-chamber rotary H2 engine, kinetic flywheel, axial-flux generator, 6 transmission gear rings with gear teeth, clutch plate with friction segments, drive shaft + coupling flange, supercharger, closed-loop steam recovery (boiler + 3 compound expander stages + steam generator + connecting pipes), 8 pitched solar roof panel pairs (180,000 m² PV), 8 electrolysis tanks, 6 H2 buffer tanks (350 bar), 4 EM-rail propulsion pods, 24 heave-fin wave generators, 12 fabric sails, 12 deck rotors, 16 battery banks (structural Li-S), full deck outfit (36 container stacks, radar mast + rotating scanner, anchor gear + windlasses, deck crane, lifeboats + davits, nav lights, genset stacks, bulwark rails). **303 meshes, 36 specs, 4 drill-down sub-units** (rotary powertrain, transmission + wet-clutch stack, closed-loop steam heat recovery, energy-harvest + propulsion suite). Ported from ReferenceCode/SE.py (3,810 lines). Showcase item 11.
- **Extended Solar System (docking, terraforming, resourcing preview)** — multi-planetary-life "test drive": home system colored by `terraform_pct` (same data as PREVIEW) with biosphere glow on life-bearing worlds, heliosphere bubble + Dyson swarm ring; an **8-phase color-segmented docking corridor** with the real `voyage_nav()` course insets — the RK4 departure hyperbola and the backward-propagated capture arc with all 8 hit.py approach gates as hot markers; star-lifting/resourcing streams feeding a fabrication zone; the target star system (Alpha Centauri analogue) with binary binding-orbit rings and a post-dock binary preview; a **rogue planet** with its own bind orbit (free-floating capture target); and a ring of 6 real candidate expansion stars (Alpha Cen, Barnard's, Wolf 359, Sirius, Epsilon Eridani, Procyon) sized by distance/priority with next-hop markers on the priority-1 hop. Same physics as PREVIEW/VOYAGE, enlarged into its own showcase. **256 meshes, 4 drill-down sub-units** (home-system terraforming, docking + resourcing, target + expansion map, optimized-ark doctrine panel). Showcase item 13.
- **Infinity Core Grain (item 14)** — the implant/suit SKU from optimizedinfornmational1 §3, rendered as its own glass-voxel showcase (implant package, contact coils, neuro pads, fiducials, merged VCSEL array). **81 meshes, 50 specs, 3 drill-down sub-units.**
- **Eternal Apex Pyramid (item 15)** — the corrected station monolith from optimizedinfornmational1 §6 (gantry, PSU, radiators, control pedestal, beacons, uplink dish, guard posts + safety chain, alignment lasers, human scale figure). **104 meshes, 27 specs, 3 drill-down sub-units.**
- **Digital QCPU fallback mode** — classical CMOS shadow-register readout, toggle `D` (default OFF).
- **Majority-voting qubit read** — M=11 reads achieves <1e-9 error from 1% single-read error.
- **Hybrid classical-quantum OS** — classical OS delegates to numpy state-vector quantum emulator (H/X/Y/Z/S/T/CNOT gates, depolarizing noise, Bell state, VQE).
- **Symphony of Self-Differentiation** — executable philosophical proof: True Nothing → growing universe via recursive self-reference.
- **5D glass disc** — quarter-sized fused-silica archive, bootstrap-on-disc. **Infinite data** via read-language overlays: 2^(2.58×10¹⁶) datasets from one fixed disc (Symphony of Self-Differentiation). **Light computation**: the 5D voxel lattice is a photonic interferometer — runs on natural sunlight, synthetic laser, or femtosecond pulse. **8× classical translator ASICs** (cryo-CMOS, 1.5 GHz, 8 mW total; 128 lanes × 100 Gb/s each = 1.6 TB/s per ASIC) read photonic output to classical bits — the glass does the computing, the chips are just the port. **122 meshes, 104 specs, 6 drill-down sub-units** (layered structure, single layer + voxels, femtosecond write, light-computation pyramid, infinite data via Symphony, light computation + classical CPU). The spec panel includes the derived optics/mechanics (diffraction limit, super-resolution gain, far-field bound, ECC/bootstrap budgets) and a **GLASS CRYSTAL COMPUTE — VERIFIED CLAIMS** block mapping each "infinite compute" claim to its proven number (48.6 ps pass, 2.58×10¹⁶ voxel-DOF/pass, 101,909 universe slots, ≤ c).
- **IQEC communicator** — 3-chip entanglement-assisted light-speed link
  (`optimizedinfornmational5`): **Mode L** ~240 Gbps effective over 17 relay
  nodes (18 hops @ 0.243 ly, 8×10¹² pair bank, 500 m swarm aperture — hop size
  set by the memory-vs-hop doctrine), plus **Mode S** collapse-ratio steering
  carried strictly as directive-premise (µs-class latency *conditional* on a
  measured ε, gated by the ε-metrology campaign; a null result degrades
  gracefully to Mode L). Tolman-guard causality checks route Mode S through
  the pulsar anchor frame — full spec in overview §8.5.
- **Gyro-Tug discs** — control-moment gyroscopes for attitude + fine steering.
- **8 terraformed planets**, **stellar sail**, **target star system**, and
  **star-lifting / harvesting** streams.

---

## Honest engineering notes

The model refuses to fake physics. A few figures were reconciled from the aspirational
blueprint to what the math actually allows (each is derived and provable):

- **Caplan acceleration ≈ 7.7×10⁻¹⁰ m/s²** (single source of truth used by the sim),
  reached only with a *full* Dyson swarm (~1 L☉). Star consumption ≈ 4.9 % per Myr.
- **Gyro-Tug discs spin at ~71 RPM, not 3000** — a 200 m rim at 3000 RPM would need
  ~31 km/s, far past the CNT bursting speed (≈1,491 m/s). RPM is capped at the material
  limit with a 4× stress margin. Discs downscaled from 10 km moonlets to 200 m
  spacecraft-class flywheels on a 0.8 AU ring.
- **5D disc: ~3.2 PB binary / ~25.8 PB (25,791 TB) 5D**, derived from disc geometry and
  the diffraction limit (10 nm voxels require ~29× sub-diffraction writing).
- **Disc read ≈ 94 TB/s**, derived from the actual spindle mechanics.
- **Interstellar link ≈ −125.2 dB/hop over 18 repeater hops** (0.243 ly each);
  entanglement adds no FTL.

These are more modest than the round blueprint numbers — that is the price of the math
actually holding.

### Performance fix: the Symphony proof no longer hangs the app

The Symphony of Self-Differentiation proof (`symphony_proof()`) recursively applies
`Phi(S) = S ∪ relations(S) ∪ translations(S)`. Relation-count grows ~n(n+1)/2 per
step, so `|S|` grows quadratic-recursively (1, 3, 9, 52, 1422, 1013124, …) — each
step's input size roughly squares. The original implementation also accumulated
results via repeated `frozenset | {..}` unions (O(current size) per union inside an
O(n²) loop ⇒ O(n⁴) total), and iterated 8 steps unconditionally. Past step 4 this
made `build_info()` — called once, unconditionally, in `App.__init__` — take
unbounded time, which is why the window would launch and immediately show as **"Not
Responding"**: it never got past initialization to draw a single frame.

The fix: accumulate into a mutable `set` (O(n²) total, not O(n⁴)) and cap the demo at
`N_ITER=6` steps, where growth is still unambiguous (over 1,000,000× in 5 steps) but
every step finishes in milliseconds. `--selftest` now completes in **~10 s** (was:
hangs indefinitely) and the app opens instantly. See the code comment at
`symphony_proof()` for the full derivation.

### Performance fix: renderer hot-path (profiler-driven)

Profiled with `cProfile` under `SDL_VIDEODRIVER=dummy` (headless, no window needed):

- **Per-frame rotation matrices were rebuilt from scratch by every mesh**, even
  though hundreds of meshes across the ark share the same `spin` factor (most
  static parts default to `spin=1.0`). `_rotz_T_cached()` memoizes `rot_z(theta).T`
  for the lifetime of one `render()` call; `Mesh.__init__` also precomputes its
  (static, never-changing) tilt rotation once instead of every frame.
- **The alpha-polygon bounding-box loop** built `xs`/`ys` Python lists and called
  the generic `min()`/`max()` builtins on them for every translucent face (tens of
  thousands per frame). Every face is arity 3 or 4 by construction, so this is now
  unrolled into direct comparisons — no list allocation, no generic builtin call.
- **The QCPU chip's qubit honeycomb lattice** built two `Mesh` objects (a sphere +
  an annulus) *per qubit* — up to 1,152 `Mesh` objects for the 24×24 SHOWCASE grid,
  each costing its own `world_verts()`/`isfinite()`/list-append dispatch every
  frame. Both primitives are surfaces of revolution about Z, so their original
  per-instance spin was already visually inert; `_instance()` bakes all copies'
  geometry into ONE `Mesh` (same triangles on screen, 1/1000th the Python-level
  mesh count). Applied to the qubit lattice, SNSPDs, reflector rings, and TSVs in
  both `build_qcpu_chip()` and `build_qcpu_showcase()`.
- **SHOWCASE mode rendered all showcased systems at once on startup** — `App.__init__`
  built `showcase_rend` over *all* of `build_showcase()`'s parts instead of just the
  selected one, only narrowing to one part after the user pressed `1`-`0`. This ×'d
  the mesh count and visibly overlaid all systems' labels until the first keypress.
  Fixed by calling `_set_showcase(0)` at init, same as the keyboard/click handlers use.

Net effect (measured, `--selftest`/`--proof` unaffected, all 116 lemmas still pass):
PREVIEW/TEST DRIVE/VOYAGE ≈23% faster per frame; SHOWCASE ≈27% faster *in addition
to* no longer rendering 9× the intended geometry. Verified numerically: merged/cached
`world_verts()` output is bit-for-bit identical to the original per-mesh formula.

### Performance fix: renderer round 2 — transform fusion + LOD culling

A second profiler pass over `render()` removed the remaining per-mesh dispatch
cost and added screen-space LOD at two levels:

- **Per-frame transform fusion** — `world_verts()` used to apply
  `Rz(angle·spin) + tilt + pivot` per mesh, then `render()` applied the camera
  `RT` separately (3–4 numpy calls per mesh per frame). All of it is now folded
  into ONE cached 3×3 `A = Rz·tilt·RT` per (spin, tilt) key, plus a batched
  pivot transform (`part._pivots @ RT + eo` — every pivot of a part in a single
  matmul). Each mesh costs one `(n,3)` matmul + broadcast add.
- **Grouped transforms** — meshes sharing `(spin, tilt)` inside a part share
  the same `A`, so their vertices are concatenated **once** (lazily cached as
  `part._groups`) and transformed in a single big matmul — replacing ~2,000
  tiny per-mesh numpy calls per frame with a handful of big ones. Face indices
  **and** the per-face shading metadata (base color, alpha, emissive) are also
  pre-concatenated per group, so a frame only needs a vectorized keep-mask +
  one offset add (`np.take` on cached index stacks — no per-group Python
  rebuilds).
- **Mesh-level LOD cull** — each mesh lazily caches `_bndr`, a bounding-sphere
  radius about its local origin; rotations preserve norms, so `2·_bndr·scale`
  upper-bounds the projected screen span at any view angle. Meshes projecting
  under ~1.4 px contribute no visible pixels and are skipped wholesale — the
  keep-mask is one vectorized comparison. Labels, picking, and solo isolation
  use their own world-space paths, so tooltips and drill-ins still work on
  culled meshes.
- **Face-level batched cull** — each surviving face's screen-space bounding box
  is computed once in the batch pass (the old unrolled per-face `min`/`max`
  loop was a top profile hot spot) and reused by the draw loop. One vectorized
  `keep` masks backface **OR** non-finite **OR** fully off-surface **OR**
  sub-pixel (~0.8 px); the isfinite terms also guarantee every surviving face
  is safe for `int()` coords, so even the alpha path no longer scans vertices
  for NaN.
- **Section view** (`X`) keeps the original unfused chain — it's a rare path
  that needs true world-space z for the cut plane, so the fused fast path is
  skipped there rather than approximated.

---

## Project files

| File | Purpose |
|------|---------|
| `SSF.py` | The entire digital twin (main file, imports `tensor_flower.py` and `reference_systems.py`). |
| `tensor_flower.py` | Tensor-Flower Comet Redirection System module (hit.py v5.1 port: System class, solar system, n-body, STM, Monte Carlo, energy model, web server). |
| `tensor_flower_dashboard.html` | Browser dashboard HTML template (12 tabs: SCOPE/IMPACT/3D VIEW/STATS/CONSOLE/CONFIG/SALVO/TRAJECTORY/SPHERE NAV/3D SPHERE/PARALLEL/PARALLEL 3D). |
| `officialgoal.md` | The blueprint / design brief. |
| `Projectgoal.md` | The full source conversation and detailed design notes. |
| `Goal.md` | Operation Green Planet specification (Earth terraforming). |
| `overview.md` | Conceptual architecture and per-subsystem science (§8 = the optimized spec family in full). |
| `infornmational1–4.md` | Baseline informational specs (superseded by the optimized family). |
| `optimizedinfornmational1.md` | Optimized 5D disc, Infinity Core grain, orchestration, Eternal Apex, manufacturing & power; QCPU Config-O integration. |
| `optimizedinfornmational2.md` | GmansQP chip v3.0: Purcell-budgeted readout closure, C/O/O+/O++/Ω/U tier ladder, IQEC NOTE*. |
| `optimizedinfornmational3.md` | Optimized propulsion/capture/docking: variable-v_e dial, Star Tug, engine-star L/M doctrine, lever-arm shaping, exchange capture, 4-rule stability, deflect-first defense, star-lift breeder. |
| `optimizedinfornmational4.md` | Operation Green Planet Mk II: thin-shell fleet, capture-η stack, trigger doctrine, inland seas (Qattara+Chotts), relay cascade, pellet/FMNR seeding, optimized P&L. |
| `optimizedinfornmational5.md` | IQEC master blueprint: Mode L (photon-limited) + Mode S (directive-premise), 17-relay memory-vs-hop chain, pair economy, causality/Tolman guard, ε-metrology campaign. |
| `README.md` | This file. |
| `Liability waiver` | Full 50-section liability waiver + terms of use (1019 lines, loaded at runtime into INFO mode). |
| `reference_systems.py` | Reference system showcase builders ported from the ReferenceCode/ programs. Only the Ship Engine builder (SE.py, 303 meshes) is used by SSF.py — showcase item 11. The other builders in this file (FlySuit 234 meshes, Hover Bike 152, Lightsaber 113, Rotary EV 115) are retained as library code but are no longer wired into the showcase. |
| `ReferenceCode/` | Sibling pure-Python renderers used as reference (flysuit, Main, LS, SE, GmansRun, hit.py, …). |
