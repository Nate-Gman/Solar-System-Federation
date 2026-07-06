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
> each subsystem.

---

## Requirements

- Python 3.9+
- `numpy`
- `pygame` (only needed for the interactive viewer; the CLI checks below run headless)

```bash
pip install numpy pygame
```

The renderer is a pure-Python software rasterizer (numpy-vectorized painter's
algorithm + normal-based Lambert flat shading + backface culling) — no GPU or
external assets required. Background gradient and starfield use numpy bulk
pixel operations for performance.

---

## Running it

```bash
python SSF.py               # interactive 3D viewer (default)
python SSF.py --selftest    # headless build + physics + entanglement + proof checks
python SSF.py --feasibility # real-world feasibility report
python SSF.py --proof       # prove the math holds (23 + 3 = 26 runtime-verified lemmas)
python SSF.py --export-obj  # export the model as OBJ + MTL files
```

`--selftest`, `--feasibility` and `--proof` are headless and print to the terminal;
they're the fastest way to see what the model does without opening a window.

---

## The five interactive modes (press `TAB` to cycle)

| Mode | What it shows |
|------|----------------|
| **PREVIEW** | Navigable 3D view of the whole ark at true scale, with a component inspector, exploded/assembly/section views, and a scale bar. |
| **TEST DRIVE** | Live physics: planets orbit under real gravity, the Caplan thruster fires, the sail adds photon-pressure thrust, the quantum core accumulates reads. |
| **DOCKING** | Six-phase approach to a target star: accelerate → coast → decelerate → gravity assist → final approach → bind orbit, with real thrust-vectored cross-track steering. |
| **SHOWCASE** | The three tiny subsystems enlarged to fill the view at true 1:1 aspect: the QCPU chip, the 5D glass disc, and the IQEC communicator. |
| **INFO** | The full engineering specification, including the three **PROOF** sections and their full derivations. |

### Controls

**Global:** `TAB` cycle modes · `I` info · `H` help · `L` labels · `R` reset · `ESC` quit

**PREVIEW:** drag = orbit · right-drag = pan · wheel = zoom · click a part to pin it ·
`1` full · `2` exploded · `3` assembly · `4` section · `E` explode · `X` section ·
`[` `]` step assembly · `A` all · `C` clear

**TEST DRIVE:** `SPACE` toggle thruster · `,` / `.` time-warp

**DOCKING:** `SPACE` engage docking · `,` / `.` approach speed

**SHOWCASE:** `1` QCPU chip · `2` glass disc · `3` IQEC comms · `[` `]` cycle ·
drag = orbit · wheel = zoom

---

## The proof system (`--proof`)

The model is a *provable* digital twin. Three groups of lemmas re-derive every
headline number and assert it against the value the program uses. If any lemma ever
drifts, `--selftest` and `--proof` fail loudly.

| Group | Lemmas | Covers |
|-------|:------:|--------|
| **QCPU** | 9 | Readout clock, standard quantum limit, LDPC error suppression, QND backaction read budget, Jaynes–Cummings entanglement, concurrence, distillation, throughput scaling. |
| **5D glass + light-computation pyramid** | 8 | Depth closure, diffraction limit, voxel count, 5D multiplexing, the exact capacity identity, density bound, photonic throughput, light-speed causality. |
| **Ship mechanics** | 6 | Gyro burst limit, flywheel momentum, CMG thrust-vectoring, rail-ejection recoil, disc spin/read mechanics, sail radiation pressure. |
| **Symphony of Self-Differentiation** | 1 | Executable proof: True Nothing bootstraps growing structure via recursive self-reference (growth, seed, closure verified). |
| **Majority-voting qubit read** | 1 | Repetition-code error suppression: M reads → effective error drops exponentially (binomial tail bound). |
| **Hybrid classical-quantum OS** | 1 | Numpy state-vector quantum emulator: Bell state, VQE iteration, classical-quantum command delegation. |

**26 lemmas total — all currently PASS.** They also render in **INFO** mode under the
"… PROOF — THE MATH HOLDS" sections and the new dedicated sections.

---

## What's modeled (all at true metric scale)

- **Central star** — Sun analogue (real solar radius, mass, luminosity).
- **Caplan thruster** — Dyson-powered plasma jet + counter-jet; derived thrust/accel.
- **Dyson swarm** — full-luminosity capture feeding the thruster and core.
- **Super Glass Pyramid** — houses the GmansQP quantum-photonic compute core.
- **GmansQP QCPU** — 1,121-qubit chip + an ultra-optimized 3-qubit variant.
- **Majority-voting qubit read** — M=11 reads achieves <1e-9 error from 1% single-read error.
- **Hybrid classical-quantum OS** — classical OS delegates to numpy state-vector quantum emulator (H/X/Y/Z/S/T/CNOT gates, depolarizing noise, Bell state, VQE).
- **Symphony of Self-Differentiation** — executable philosophical proof: True Nothing → growing universe via recursive self-reference.
- **5D glass disc** — quarter-sized fused-silica archive, bootstrap-on-disc.
- **IQEC communicator** — 3-chip entanglement-assisted light-speed link.
- **Gyro-Tug discs** — control-moment gyroscopes for attitude + fine steering.
- **8 terraformed planets**, **stellar sail**, **target star system**, and
  **star-lifting / harvesting** streams.

---

## Honest engineering notes

The model refuses to fake physics. A few figures were reconciled from the aspirational
blueprint to what the math actually allows (each is derived and provable):

- **Caplan acceleration ≈ 7.7×10⁻¹⁰ m/s²** (single source of truth used by the sim),
  reached only with a *full* Dyson swarm (~1 L☉). Star consumption ≈ 4.9 % per Myr.
- **Gyro-Tug discs spin at ~6 RPM, not 3000** — a 10 km rim at 3000 RPM would need
  ~1571 km/s, far past the CNT bursting speed. RPM is capped at the material limit
  with a 4× stress margin.
- **5D disc: ~1.08 PB binary / ~5.4 PB (5397 TB) 5D**, derived from disc geometry and
  the diffraction limit (10 nm voxels require ~29× sub-diffraction writing).
- **Disc read ≈ 2.4 TB/s**, derived from the actual spindle mechanics.
- **Interstellar link ≈ −131 dB/hop over 10 repeater hops**; entanglement adds no FTL.

These are more modest than the round blueprint numbers — that is the price of the math
actually holding.

---

## Project files

| File | Purpose |
|------|---------|
| `SSF.py` | The entire digital twin (single file). |
| `officialgoal.md` | The blueprint / design brief. |
| `Projectgoal.md` | The full source conversation and detailed design notes. |
| `overview.md` | Conceptual architecture and per-subsystem science. |
| `README.md` | This file. |
| `ReferenceCode/` | Sibling pure-Python renderers used as reference (flysuit, Main, LS, SE, GmansRun, …). |
