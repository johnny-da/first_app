# Stage 3 Analysis Validation

All four cases were run through the named calculation functions in `index.html`. Reactions and moments are in kips and kip-ft, stress in ksi, and deflection in inches. Comparisons use tolerances of 0.001 for reactions, moments, and stress, and 0.002 in for deflection. Pass/fail comparisons use the exact unrounded results.

| Case | Reactions | `|Mmax|` | `fb` | `|ymax|` and location | L/360 limit | Result |
| --- | --- | ---: | ---: | --- | ---: | --- |
| 1. 20 ft simply supported W12x26, 1 kip/ft full-span UDL | 10.000 k up at each support | 50.000 | 17.964 | 0.608519 in at 10.00 ft | 0.666667 in | Bending PASS; deflection PASS; overall PASS |
| 2. 20 ft simply supported W12x26, 10 k at 5 ft | 7.500 k up left; 2.500 k up right | 37.500 | 13.473 | 0.340173 in at 8.82 ft | 0.666667 in | Bending PASS; deflection PASS; overall PASS |
| 3. 10 ft cantilever W12x26, 5 k at free end | 5.000 k up and 50.000 kip-ft CCW at fixed end | 50.000 | 17.964 | 0.486815 in at 10.00 ft | 0.333333 in | Bending PASS; deflection FAIL; overall FAIL |
| 4. 12 ft simply supported DF-L No. 2 2x10, 0.05 kip/ft full-span UDL | 0.300 k up at each support | 0.900 | 0.505 | 0.147421 in at 6.00 ft | 0.400000 in | Bending PASS; deflection PASS; overall PASS |

## Additional Checks
- The shear/moment grid spacing is at most 0.05 ft and includes exact point-load and uniform-load boundaries. Point loads have separate before/after shear samples; the 4 k point-load check produced a 4 k shear jump with continuous moment.
- Reaction equilibrium passed for the listed cases. A uniform load entered from -2 to 12 ft on a 10 ft beam was clipped to 0–10 ft.
- Simply supported deflection is zero at both supports. Cantilever deflection and slope are zero at the fixed end.
- Changing UI inputs updates the stored analysis result; the visible plots, check cards, and recommendation remain static placeholders at this stage.

## Section Property Basis
The runtime steel catalog uses properties transcribed from AISC Shapes Database v16.0 on these section pages: [W8x10](https://buildrefs.com/sections/american/aisc/w-shapes/w8x10/), [W10x12](https://buildrefs.com/sections/american/aisc/w-shapes/w10x12/), [W12x26](https://buildrefs.com/sections/american/aisc/w-shapes/w12x26/), [W14x22](https://buildrefs.com/sections/american/aisc/w-shapes/w14x22/), [W16x26](https://buildrefs.com/sections/american/aisc/w-shapes/w16x26/), [W18x35](https://buildrefs.com/sections/american/aisc/w-shapes/w18x35/), [W21x44](https://buildrefs.com/sections/american/aisc/w-shapes/w21x44/), and [W24x55](https://buildrefs.com/sections/american/aisc/w-shapes/w24x55/). Ix and weight matched the spec. The AISC-hosted spreadsheet was blocked in this environment, so these are secondary transcriptions citing AISC, not a direct check of the primary file.

The spec's Sx entries differ from the AISC-v16 transcriptions for seven sections. The runtime catalog uses: W8x10 7.81, W10x12 10.9, W12x26 33.4, W14x22 29.0, W16x26 38.4, W18x35 57.6, W21x44 81.6, and W24x55 114 in^3. `spec.md` was not changed in this stage; reconcile its table before treating the written spec and runtime catalog as identical.

Lumber Ix/Sx values were checked from the spec's dressed dimensions using `Ix = b*h^3/12` and `Sx = b*h^2/6`, and match the listed values to rounding. Lumber E and Fb remain the values supplied in the spec.
