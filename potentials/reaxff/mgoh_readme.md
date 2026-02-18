# Mg/O/H ReaxFF Force Field (LAMMPS)

## Overview
This repository contains a **ReaxFF reactive force field for Mg/O/H systems**, extracted and prepared for use with **LAMMPS**.  
The force field is intended for **reactive molecular dynamics (MD)** simulations involving magnesium, hydrogen, and oxygen, with a focus on **hydrogenation and dehydrogenation processes** in Mg-based systems.

---

## Force Field Description

- **Force field type:** ReaxFF (Reactive Force Field)
- **Elements included:** H, O, Mg
- **Element order in force-field file:**  H O Mg
- **File name:** 

---

## Source and Reference

This force field was extracted from the Supporting Information of the following paper:

**Yong Zhang, Zheng Mei, Fang-Chao Hou, Xiao-Hong Wu,  
Yun-Hui Hou, Min Li, Jing Sun, Liang Song**

> *Development of a ReaxFF reactive force-field modeling for magnesium nanoparticles and water system*  
> **Applied Surface Science**, 2025  
> DOI: **10.1016/j.apsusc.2025.163207**

Specifically, the parameters were taken from **Section S3: “ReaxFF parameter set for Mg/O/H”** of the Supporting Information.

---

## Intended Use (What This Force Field IS Valid For)

This ReaxFF parameterization is suitable for:

- Reactive MD simulations of **Mg-based systems**
- **Hydrogenation of Mg** (Mg–H bond formation)
- **Dehydrogenation of MgH₂** (Mg–H bond breaking and H₂ formation)
- **Mg nanoparticles and surfaces**
- **Mg–H, Mg–O, and O–H chemistry**
- **Water-assisted reactions**
- Oxidation and hydroxylation effects
- Demonstration of **reactive MD capability** in Mg systems

This makes the force field well suited for:
- Method demonstrations
- Proof-of-capability studies
- Mechanistic investigations
- PhD interviews and preliminary research

---

## Limitations (What This Force Field Should NOT Be Used For)

This force field is **not optimized** for:

- High-precision **bulk MgH₂ thermodynamics**
- Quantitative benchmarking of **MgH₂ formation enthalpy**
- Ideal, oxygen-free bulk MgH₂ equilibrium studies
- Long-term hydrogen storage cycling predictions without additional validation

For fundamental bulk MgH₂ thermodynamics, more specialized **Mg–H-only ReaxFF parameterizations** should be considered.

---

## File Extraction Notes

- The force field was **manually extracted** from the Supporting Information.
- Only the numerical ReaxFF parameter block (general parameters → hydrogen bond section) was included.
- **Training-set geometries, EOS data, and coordinate blocks were intentionally excluded**, as required for a valid `ffield.reax` file.

---

## Usage with LAMMPS

### Pair style
```lammps
pair_style reaxff NULL
```

### Pair coefficients
```
pair_coeff * * ffield.reax.mgoh H O Mg
```

### Note: The element order must match the order in the force-field file.