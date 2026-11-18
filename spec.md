# Beam Designer

## Purpose
Instantly update shear, moment, and deflection diagrams as a beam's
supports, span, loads, or section change, and check whether it is strong
and stiff enough.

## Users
- Civil engineering students checking homework
- Engineers sizing floor beams or deck joists

## Inputs
- **Support type:** Select Simply supported (default) or Cantilever fixed at left.
- **Span:** Enter 4 to 40 ft using a number box or synced slider; default 20 ft.
- **Point loads:** An editable, removable list with an Add point load button.
	Each load is entered in kips, with downward positive, and has a draggable
	location on the beam drawing that snaps to 0.25 ft. A new point load starts
	at midspan for a simply supported beam or at the cantilever tip.
- **Uniform loads:** An editable, removable list with an Add uniform load
	button. Enter intensity in kips/ft and start and end locations in ft.
	Loads are cut off at the beam end. The initial load is 1 kip/ft from 0 ft to
	the full span.
- **Deflection limit:** Select L/240 or L/360; default L/360.
- **Self-weight:** Ignored.
- **Section selection:** Choose Steel W-shape or Douglas Fir-Larch No. 2 lumber,
	then select a listed section; default to W12x26. Steel properties use E =
	29,000 ksi and Fb = 30 ksi. Lumber properties use E = 1,600 ksi and Fb =
	0.900 ksi.

	Steel W-shape properties (Ix in in^4, Sx in in^3, weight in lb/ft):

	| Section | Ix | Sx | Weight |
	| --- | ---: | ---: | ---: |
	| W8x10 | 30.8 | 7.64 | 10 |
	| W10x12 | 53.8 | 10.8 | 12 |
	| W12x26 | 204 | 33.4 | 26 |
	| W14x22 | 199 | 28.5 | 22 |
	| W16x26 | 301 | 37.7 | 26 |
	| W18x35 | 510 | 56.9 | 35 |
	| W21x44 | 843 | 80.3 | 44 |
	| W24x55 | 1,350 | 113 | 55 |

	Douglas Fir-Larch No. 2 properties (nominal sizes use dressed dimensions;
	Ix in in^4 and Sx in in^3):

	| Nominal size | Dressed size (in) | Ix | Sx |
	| --- | --- | ---: | ---: |
	| 2x8 | 1.5 x 7.25 | 47.6 | 13.1 |
	| 2x10 | 1.5 x 9.25 | 98.9 | 21.4 |
	| 2x12 | 1.5 x 11.25 | 178 | 31.6 |

## Calculations
- Calculate support reactions from statics.
- Calculate shear V(x) and moment M(x) at intervals no greater than 1 ft,
	including every point-load location and every uniform-load start and end
	position. Show shear values immediately before and after point loads.
- Calculate deflection y(x) by integrating M/EI twice, using consistent units
	and these support boundary conditions:
	- Simply supported: y = 0 at both supports.
	- Cantilever fixed at the left: y = 0 and slope = 0 at the fixed end.
- Calculate maximum bending stress as fb = |Mmax| * 12 / Sx (ksi), where Mmax
	is in kip-ft and Sx is in in^3. Bending passes when fb <= Fb.
- Deflection passes when the maximum absolute deflection is no greater than
	L/240 or L/360, using the selected limit and L in inches.
- Recommend the lightest listed section that passes both checks. For steel,
	choose the passing section with the lowest weight, breaking ties by larger Ix.
	For lumber, choose the first passing size in the listed order. If no listed
	section passes, provide no recommendation.
- Display reactions and shear in kips, span positions in ft, moment in kip-ft,
	and deflection in inches.

## Outputs
- Show a beam drawing with its supports, load arrows, and reaction arrows.
- Show three filled diagrams stacked and aligned on the same x-axis: shear,
	moment, and deflected shape. Label the maximum value on each diagram.
- Show a hover crosshair synchronized across all three diagrams; at position x,
	display V, M, and y.
- Show Bending and Deflection check cards with actual and allowable values, a
	ratio bar, and PASS or FAIL. Use green below 70%, amber from 70% through 100%,
	and red above 100% of the allowable value.
- Show the lightest passing section suggestion with a button to apply that
	section.
- Update the drawing, diagrams, checks, and recommendation instantly whenever
	an input changes.

## Look and feel
- Use a commercial engineering web app style: light background, dark blue
	cards, soft shadows, few accent colors, and a fun font.
- Place inputs on the right and the drawing, diagrams, and checks on the left;
	stack these areas on mobile.
- Use short labels with units. 

## Validation
- Use L/360 for these hand-checked cases. Report reactions in kips, moment in
	kip-ft, bending stress in ksi, and deflection in inches.
- **1.** 20 ft simply supported W12x26 with 1 kip/ft uniform load: reactions
	10.000 k up at each support; |Mmax| = 50.000 kip-ft; fb = 17.964 ksi,
	bending PASS; |ymax| = 0.609 in versus 0.667 in allowable, deflection PASS;
	overall PASS.
- **2.** 20 ft simply supported W12x26 with a 10 k downward point load at 5 ft:
	reactions 7.500 k up at the left support and 2.500 k up at the right support;
	|Mmax| = 37.500 kip-ft; fb = 13.473 ksi, bending PASS; |ymax| = 0.340 in
	at x = 8.820 ft versus 0.667 in allowable, deflection PASS; overall PASS.
- **3.** 10 ft cantilever W12x26 with a 5 k downward point load at the free end:
	fixed-end reactions 5.000 k up and 50.000 kip-ft counterclockwise; |Mmax| =
	50.000 kip-ft; fb = 17.964 ksi, bending PASS; |ymax| = 0.487 in versus
	0.333 in allowable, deflection FAIL; overall FAIL.
- **4.** 12 ft simply supported Douglas Fir-Larch No. 2 2x10 joist with
	0.05 kip/ft uniform load: reactions 0.300 k up at each support; |Mmax| =
	0.900 kip-ft; fb = 0.505 ksi, bending PASS; |ymax| = 0.147 in versus
	0.400 in allowable, deflection PASS; overall PASS.

## Out of scope
- Self-weight
- Shear stress
- Lateral-torsional buckling
- Load combinations
- Continuous beams
- Saving designs

## Build stages
1. **Layout mockup, no calculations:** Create the page layout with inputs on
	the right and the beam drawing, diagrams, and checks on the left. Use
	clearly marked placeholders that cannot be mistaken for calculated results.
	Check desktop and mobile layouts, stacking, text fit, and placeholder clarity.
2. **Inputs and editable beam:** Add the specified controls, defaults, load
	lists, bounds, and basic beam drawing. Keep analysis diagrams and checks as
	placeholders. Check defaults, slider/number synchronization, add/remove
	behavior, load placement and clipping, support-specific load placement, and
	quarter-foot drag snapping.
3. **Calculation engine:** Implement reactions, shear, moment, deflection,
	bending stress, and limits. Verify section-property values against
	authoritative tables before using them. Check all four Validation cases
	against expected results with documented tolerances, plus equilibrium,
	shear jumps, and support boundary conditions.
4. **Diagrams and synchronized interaction:** Render filled shear, moment, and
	deflection diagrams on aligned axes, with maxima and a shared hover crosshair.
	Connect input changes to immediate updates. Check axis alignment, values at
	load locations and endpoints, crosshair synchronization, and redraws after
	input changes and load dragging.
5. **Checks and section recommendations:** Add the bending and deflection
	check cards, ratio colors, section recommendation, and apply button. Check
	the 70% and 100% color thresholds, steel weight selection and tie-breaking,
	lumber ordering, no-passing-section behavior, and all four Validation cases.