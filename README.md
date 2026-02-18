## Directory Structure

MgH2_ReaxFF_Project/
├── potentials/
│   └── reaxff/
│       └── ffield.reax.mgoh
├── hydrogenation/
│   └── in.hydrogenation.reax
├── dehydrogenation/
│   ├── in.dehydrogenation.reax
│   └── data.mgh2
└── README.md

# Simulation 1: Hydrogenation

## Purpose
Demonstrate Mg–H bond formation via reactive MD.


## Input File
hydrogenation/in.hydrogenation.reax

## System Description
- Mg slab (hcp lattice)
- Hydrogen atoms initially placed above the slab
- Elevated temperature (≈ 800 K)

## What to Observe
- Hydrogen diffusion into Mg
- Formation of Mg–H bonds
- Charge transfer during bonding

## Run command
```
lmp -in in.hydrogenation.reax
```


# Simulation 2: Dehydrogenation

## Purpose
Demonstrate MgH₂ decomposition and H₂ release.

## Input File
- dehydrogenation/in.dehydrogenation.reax
- dehydrogenation/data.mgh2

## System Description
- Minimal MgH₂ unit (demo system)
- Temperature ramp from 300 K → 1200 K

## What to Observe
- Mg–H bond breaking
- Hydrogen recombination into H₂
- Energy and structural changes with temperature

## Run command
```
lmp -in in.dehydrogenation.reax
```


# Key LAMMPS Settings (Why They Matter)
- atom_style charge: Required for ReaxFF
- fix qeq/reaxff: Mandatory for charge equilibration
- timestep 0.25 fs: Required for numerical stability in ReaxFF
- units real: Consistent with ReaxFF parameterization

# Output & Visualization

## Dumps
Both simulations write trajectory files:
```
dump.*
```
## Visualization of the results
These can be visualized using:
- OVITO (recommended)
- VMD

Color by:
- Atom type
- Charge
- Coordination number

## How to Explain This Work (Interview-Ready)
I used ReaxFF-based reactive molecular dynamics in LAMMPS to model hydrogenation and dehydrogenation in Mg-based systems. The force field captures Mg–H bond formation and breaking, allowing me to demonstrate hydrogen uptake and release mechanisms. While high-precision bulk thermodynamics require more specialized parameterizations, this setup clearly demonstrates reactive MD capability and mechanistic understanding.

# Final Notes and Metadata

## Final Notes
Further work could include:
- Larger MgH₂ cells
- Bond analysis (fix reaxff/bonds)
- Comparison with DFT or literature data

## Metadata
- Author: Narendra Kumar
- Simulation code: LAMMPS
- Force field: ReaxFF (Mg/O/H)