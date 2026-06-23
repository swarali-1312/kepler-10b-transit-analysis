# Transit Light Curve Analysis of Exoplanet Kepler-10b

**Author:** Swarali Nandkishor Shingne  
**Tools:** Python · lightkurve · NumPy · Matplotlib  
**Data:** NASA Kepler mission (KIC 11904151)

---

## Overview

This project detects the transit of exoplanet Kepler-10b in real photometric data from NASA's Kepler space telescope, and estimates the planet's radius from the measured transit depth.

Kepler-10b is one of the first rocky exoplanets confirmed by the Kepler mission — a super-Earth orbiting its host star every ~0.84 days. Its transit signal, a fractional brightness dip of less than 0.02%, is a good test of basic transit-detection techniques.

---

## Background: How Transits Work

When a planet crosses in front of its host star (as seen from Earth), it blocks a small fraction of the starlight, causing a temporary dip in observed brightness.

The transit depth is related to the planet-to-star radius ratio:

$$\text{depth} = \frac{\Delta F}{F} = \left(\frac{R_p}{R_*}\right)^2$$

Measuring the depth allows us to estimate the planet's physical size.

---

## Method

1. **Download light curve** — Searched for and downloaded Kepler long-cadence photometry of Kepler-10 (KIC 11904151) using `lightkurve`.
2. **Clean and flatten** — Removed NaN values; applied `flatten()` to suppress long-term stellar variability, preserving short-duration transit features.
3. **Phase fold** — Folded the light curve on the known orbital period of Kepler-10b (≈ 0.837491 days), aligning all transit events.
4. **Bin** — Binned the folded light curve (52 bins) to average down noise and reveal a clean U-shaped transit profile.
5. **Measure transit depth** — Computed depth = 1 − F_min from the binned normalized flux.
6. **Estimate planet radius** — Used R_p = R_* √(depth), with R_* = 1.065 R☉ for Kepler-10.

---

## Results

| Quantity | Value |
|---|---|
| Measured transit depth | ~1.86 × 10⁻⁴ |
| Planet radius (R☉) | ~0.0145 R☉ |
| Planet radius (R⊕) | **~1.6 R⊕** |

The estimated radius of ~1.6 R⊕ is consistent with the known properties of Kepler-10b, confirming it as a rocky super-Earth.

---

## Files

```
1st_project_exoplanets_.ipynb    # Main analysis notebook
```

---

## Dependencies

```
pip install lightkurve numpy matplotlib astropy
```

---

## Notes

This is my first project in exoplanet data analysis, undertaken independently to build familiarity with real telescope data, phase-folding techniques, and basic transit photometry. It forms part of my broader interest in observational exoplanet science and stellar physics.
