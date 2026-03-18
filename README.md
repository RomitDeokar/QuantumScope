# QUANTUMSCOPE // QS-01
### Interactive Quantum State Evolution Lab

> **QtHack04 -- Problem 16** | Single-file virtual experimental instrument for understanding qubit evolution, gate physics, and quantum measurement in real time, backed by physics-accurate complex linear algebra, real-time 3D Bloch sphere visualization, and educational tooling.

---

## Live Demo

Open `index.html` in any modern browser. No build step, no dependencies to install. **Zero-config, single-file architecture.**

---

## What Makes This Unique

QuantumScope is a **virtual experimental instrument for single-qubit physics** compressed into a single HTML file. Every interaction is backed by exact linear algebra on complex numbers, with the Bloch sphere serving as geometric ground truth.

### Core Philosophy
- **Single source of truth**: One `QState` object. Gate click -> matrix multiplication -> state update -> Bloch vector derivation -> all UI panels sync simultaneously.
- **Physics-first**: Real `Complex` number class with full arithmetic. Exact unitary gate matrices. Normalization checks after every operation.
- **No shortcuts**: Bloch vector computed from `2*Re(alpha*.beta)`, `2*Im(alpha*.beta)`, `|alpha|^2 - |beta|^2`. Not from angle approximations.

---

## Complete Feature Inventory

### 1. Quantum Engine (v3.1)
- **Complex number class**: Full `add`, `sub`, `mul`, `scale`, `conj`, `abs`, `abs2`, `phase`, `clone` operations
- **8 quantum gates**: H, X, Y, Z, S, T, Rx(theta), Ry(theta) with exact complex matrix definitions
- **Rx/Ry with angle slider**: Continuous rotation with synced range slider + numeric input
- **State normalization**: Automatic after every gate application with visual norm bar
- **Gate history & undo**: Full replay-capable gate sequence with single-step undo
- **State snapshot system**: Each gate saves a snapshot for timeline scrubbing

### 2. 3D Bloch Sphere (Three.js v0.160)
- **Multi-layer translucent sphere**: Phong material with specular highlights, emissive glow, inner/outer shells
- **Bright outer glow rim** (dual-shell: 1.1 + 1.18 radius) for depth perception
- **5 latitude rings** (equator highlighted in cyan) + 4 meridian rings
- **6 axis lines** with color-coded labels: |0>, |1>, +X, -X, +Y, -Y
- **Pole dots with glow halos** at north (|0>) and south (|1>)
- **State vector arrow**: Cylinder shaft + cone head + sphere tip + transparent glow aura
- **Trail animation**: Records path of state across Bloch surface (100-point buffer)
- **Smooth angular interpolation**: 8% lerp per frame for fluid transitions
- **OrbitControls**: Drag to rotate, scroll to zoom, auto-rotate at 0.6 deg/s
- **Measurement vibration**: Randomized shake effect before wavefunction collapse
- **Correct axis mapping**: Bloch Z -> Three.js Y (up), Bloch X -> Three.js X, Bloch Y -> Three.js Z
- **Enhanced lighting**: 4 point lights (cyan, red, green, blue) + ambient for rich illumination

### 3. Gate Panel, Circuit Builder & Demo Flow
- **Color-coded gate buttons**: Each gate has unique accent color (H=cyan, X=red, Y=amber, Z=green, S=purple, T=pink)
- **Hover tooltips**: Contextual gate descriptions on hover
- **Keyboard shortcuts**: H, X, Y, Z, S, T, M (measure), R (reset), U (undo), B (Bell), P (teleport), ? (guide)
- **Angle input with slider**: Synced range slider + number input for Rx/Ry continuous rotations
- **Circuit wire visualization**: Live diagram showing gate chips on wire with color-coding
- **Auto Demo mode**: One-click presentation flow for hackathon judging (`|0⟩ → H → explain → measure → Bell preset`)

### 4. Gate Physics Panel (3-Tier Explanation)
- **Unitary Matrix**: Text representation + visual 2x2/4x4 grid display
- **Physical Effect**: Plain-English description of what the gate does physically
- **Basis Change**: How the gate transforms the computational basis states
- **Bloch Transform**: Axis and angle of rotation on the Bloch sphere

### 5. Density Matrix (rho = |psi><psi|)
- **Live 2x2 density matrix**: Diagonal elements (populations) and off-diagonal (coherences)
- **Color-intensity mapping**: Background color scales with matrix element magnitude
- **Complex number display** for off-diagonal elements

### 6. Quantum State Tomography
- **Pauli expectation values**: <X>, <Y>, <Z> displayed as dynamic bar chart
- **Derived directly from Bloch vector components** (exact, no sampling)
- **Positive/negative color differentiation**

### 7. Phase Wheel Visualization
- **Canvas-rendered phase diagram** showing alpha and beta complex phases as vectors
- **Relative phase arc** in purple between the two amplitudes
- **Real-time update** on every state change

### 8. Wigner Quasi-Probability Function
- **Discrete Wigner function heatmap** rendered on 18x18 grid
- **Theta-phi parameter space** visualization
- **Cyan for positive** / **red for negative** quasi-probability regions
- **Grid overlay** with axis labels
- **Unique feature**: Maps the full qubit state onto phase space

### 9. Entanglement Witness
- **Coherence-based entanglement indicator**: Measures off-diagonal density matrix elements
- **Animated indicator dot**: Pulses purple when high coherence detected
- **Bell mode detection**: Shows "MAXIMALLY ENTANGLED" for Bell states
- **Real-time coherence value** with classification labels

### 10. Fidelity Comparator (6 Basis States)
- **Computes fidelity** |<basis|psi>|^2 to all 6 cardinal states: |0>, |1>, |+>, |->, |+i>, |-i>
- **Active highlighting** on the closest basis state (fidelity > 0.95)
- **Color-coded values**: Cyan for high fidelity, dim for low
- **Updates in real-time** after every gate application

### 11. Quantum Error Correction Simulator
- **3-bit repetition code** educational demonstration
- **Syndrome detection**: Shows 3 encoded bits with error highlighting
- **Majority-vote decoding**: Identifies and locates single-bit errors
- **Noise-aware**: Error probability increases during decoherence simulation
- **Visual feedback**: Red bits for detected errors, green for clean

### 12. Decoherence Simulator
- **T2 dephasing simulation**: Progressive random phase kicks on beta amplitude
- **Decoherence meter**: Visual bar progressing from COHERENT -> DEPHASING -> DECOHERED
- **Noise kick button**: Single random Rx rotation to simulate environmental perturbation
- **Real-time state degradation** visible across all panels simultaneously
- **Start/Stop control**: Toggle decoherence on and off

### 13. Quantum Teleportation Protocol
- **Preset demonstrating quantum teleportation** circuit
- **Simulates H -> Z -> H -> CNOT -> H -> Measure sequence**
- **Explains no-cloning theorem** and classical bit requirements
- **Full gate physics panel explanation** of the protocol

### 14. Quantum Random Walk
- **7-gate interference pattern**: H -> S -> H -> T -> H -> S -> T
- **Demonstrates quantum walk** speedup concept with interference

### 15. Circuit Timeline Scrubber
- **Visual step-by-step timeline** of applied gates
- **Click any step to time-travel** to that point in the circuit
- **Current step highlighted** in green, all steps clickable
- **Replays gate sequence** from initial state

### 16. Circuit Complexity Meter
- **Weighted gate complexity score**: T-gates worth 3x, Y-gates 2x, simple gates 1x
- **Color-coded progress bar**: Green (low) -> Amber (medium) -> Red (high)
- **Real-time complexity tracking**

### 17. Measurement System & Correlated Bell Collapse
- **Probabilistic collapse**: Uses `Math.random()` against |alpha|^2 with full logging
- **Measurement vibration animation** on Bloch sphere
- **Full-screen collapse flash overlay** (red radial gradient)
- **Multi-measurement mode**: 100-shot statistical sampling without state destruction
- **Measurement histogram**: Bar chart of |0> vs |1> outcomes with counts
- **Bell collapse cue**: In Bell preset mode, both mini Bloch spheres snap to the same pole after measurement to reinforce perfect correlation

### 18. Arrow Direction Inspector
- **Live arrow direction readout**: Explicit `ARROW_DIR`, `BASIS_ZONE`, and `PHASE_REGIME` labels under the Bloch sphere
- **Axis-verification aid**: Makes the Bloch-to-Three.js mapping auditable during demos and debugging

### 19. Bell State Entanglement
- **Dual mini Bloch spheres** rendered with separate Three.js scenes
- **Synchronized arrow animation** showing entanglement correlation
- **Orbiting cameras** for dramatic visual effect
- **Full Bell state |Phi+> physics explanation**
- **CNOT gate representation** in circuit

### 20. Purity Tracking
- **State purity bar** showing Tr(rho^2) in real-time
- **Color-coded**: Green (pure) -> Amber -> Red (mixed)
- **Tracks decoherence effects** visually

### 21. Sound Engine (Web Audio API)
- **Unique frequency per gate**: H=523Hz, X=330Hz, Y=392Hz, Z=440Hz, S=494Hz, T=587Hz
- **Measurement collapse sound**: Descending sawtooth sweep 800Hz -> 80Hz
- **Challenge success arpeggio**: C-E-G major chord sequence
- **Toggle on/off** from topbar SFX button

### 22. Quantum Challenge Mode (18 Questions)
- **18 multiple-choice questions** covering quantum mechanics fundamentals
- **Topics**: Gate effects, Bloch sphere angles, entropy, Bell correlations, no-cloning theorem, purity
- **Immediate feedback**: Correct (green) / incorrect (red) highlights
- **Running score tracker** with sound effects for correct answers

### 23. Guided Tutorial Mode
- **6-step interactive walkthrough** for new users
- **Auto-shows on first visit** (localStorage tracked)
- **Accessible via `?` key** or topbar GUIDE button
- **Covers**: qubit state, gates, Bloch sphere, measurement, advanced features

### 24. Export Capabilities
- **QASM Export**: OpenQASM 2.0 circuit file download using the standard `qelib1.inc` include
- **JSON Export**: Full state snapshot including amplitudes, Bloch vector, probabilities, metrics, gate history, histogram

### 25. Prognosis Engine
- **Prediction confidence meter**: Based on probability distribution
- **Labels**: DETERMINISTIC, UNCERTAIN, BIASED, COLLAPSED
- **Trend indicator**: Shows which state is favored

### 26. System Log
- **Color-coded event log**: OK (green), INFO (cyan), WARN (amber), ERR (red), SYS (purple)
- **Timestamped entries** with smooth fade-in animation
- **150-entry buffer** with auto-scroll and auto-prune
- **Boot sequence**: Timed system log entries simulating OS boot with module loading

### 27. Visual Design
- **Animated particle background**: 35 particles with connection lines (canvas), subtle opacity
- **Scanline overlay**: Subtle CRT-style scan effect (reduced for polish)
- **Grid overlay**: 48px cyan grid pattern at low opacity
- **Corner brackets**: CSS pseudo-element borders on all panels
- **Panel hover effects**: Border brightening + bracket opacity transition
- **Rounded corners**: Subtle `3px` radius throughout for modern feel
- **Gate button hover**: Translate-Y lift + controlled shadow
- **Dark HUD theme**: Custom CSS variables, Orbitron + Share Tech Mono fonts
- **Collapse flash overlay**: Full-screen radial gradient pulse
- **Smooth value transitions**: CSS transitions on all numeric displays

---

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `H` | Apply Hadamard gate |
| `X` | Apply Pauli-X gate |
| `Y` | Apply Pauli-Y gate |
| `Z` | Apply Pauli-Z gate |
| `S` | Apply S gate |
| `T` | Apply T gate |
| `M` | Measure qubit |
| `R` | Reset to |0> |
| `U` | Undo last gate |
| `E` | Explain current state |
| `B` | Load Bell state preset |
| `P` | Load Teleportation preset |
| `?` | Open tutorial guide |
| `F3` | Toggle Challenge mode |

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Structure | Single HTML file, no build tools |
| 3D Rendering | Three.js v0.160 (ES modules via CDN importmap) |
| Controls | Three.js OrbitControls |
| Math | Custom Complex number class |
| Audio | Web Audio API |
| Particles | HTML5 Canvas 2D |
| Phase Wheel | HTML5 Canvas 2D |
| Wigner Function | HTML5 Canvas 2D |
| Fonts | Google Fonts (Orbitron, Share Tech Mono) |
| State | Single QState object (source of truth) |

---

## Data Flow

```
Gate Click / Key Press
       |
       v
  QState.applyMatrix(gate)    <-- exact complex matrix multiplication
       |
       v
  QState.normalize()           <-- |alpha|^2 + |beta|^2 = 1
       |
       v
  updateAllUI()                <-- single function updates ALL panels:
       |
       +-- Equation display (|psi> = alpha|0> + beta|1>)
       +-- Amplitude boxes (Re + Im parts)
       +-- Probability bars + percentages
       +-- Bloch angles (theta, phi from blochX/Y/Z)
       +-- Normalization bar
       +-- State label & badge
       +-- Statistics (gates, measures, entropy, fidelity, purity)
       +-- Density matrix (rho_ij)
       +-- Tomography bars (<X>, <Y>, <Z>)
       +-- Phase wheel (canvas)
       +-- Wigner function heatmap (canvas)
       +-- Entanglement witness (coherence metric)
       +-- Fidelity comparator (6 basis states)
       +-- QEC syndrome (3-bit repetition)
       +-- Purity bar
       +-- Circuit timeline
       +-- Complexity meter
       +-- Prognosis engine
       +-- Bloch sphere animation target
```

---

## Architecture Decisions

1. **Single file**: No framework overhead. Judges can open and run instantly.
2. **ES modules**: Three.js loaded via importmap for clean module syntax.
3. **Bloch vector from components**: `blochX = 2*Re(alpha*.beta)` computed directly, not from theta/phi. This avoids all trigonometric edge cases.
4. **Three.js Y-up mapping**: Bloch Z (quantum up) maps to Three.js Y (visual up). `dir = Vector3(blochX, blochZ, blochY)`.
5. **Snapshot system**: Each gate application saves a state snapshot enabling timeline scrubbing without recomputation.
6. **position.set() pattern**: All Three.js mesh positions set via `.position.set(x,y,z)` to avoid read-only property conflicts.

---

## Bugs Fixed in This Version

- **Bell mini-sphere crash**: `Object.assign` on Three.js `Mesh.position` (read-only) replaced with `.position.set()`
- **Bloch sphere direction**: Verified correct mapping: Bloch Z -> Three.js Y, Bloch X -> Three.js X, Bloch Y -> Three.js Z
- **Bloch sphere brightness**: Enhanced with brighter Phong material, specular highlights, dual outer glow shells, 4 point lights
- **UI polish**: Reduced CRT scanline intensity, subtler particle opacity, added border-radius throughout, refined color palette

---

## Author

Built for **QtHack04 -- Problem 16** | QuantumScope QS-01 v3.1

*"The Bloch sphere is the Rosetta Stone of single-qubit quantum mechanics."*
