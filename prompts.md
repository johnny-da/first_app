# Prompt Log

- Asked: Set up the single-file web app project layout with top-level `AGENTS.md`, `spec.md`, `prompts.md`, and `index.html`, plus numbered folders for planning, validation, and output. Do not build the app.
- Changed: Added the requested folder READMEs and top-level scaffold files; documented the layout and file-placement rule in `AGENTS.md`.
- Worked: Yes; the requested structure was created and checked.

- Asked: Update only Purpose, Users, and Inputs in `spec.md` for the beam designer; do not build the app.
- Changed: Expanded the purpose, added user groups, specified the input controls/defaults and load behavior, and added steel and lumber property tables.
- Worked: Yes; the requested specification sections were updated without changing other sections or building the app.

- Asked: Update only the Calculations section of `spec.md` with analysis sampling, support boundary conditions, pass/fail checks, section recommendations, and display units. Do not build anything.
- Changed: Specified statics reactions, V(x) and M(x) evaluation points, integrated deflection with support conditions, bending and deflection criteria, lightest-passing recommendations, and units.
- Worked: Yes; only the Calculations section was changed in the spec, and no app was built.

- Asked: Update only Outputs and Look and feel in `spec.md` with beam/diagram displays, synchronized crosshair, check cards, section suggestion, responsive engineering-app styling, and a preloaded example. Do not build anything.
- Changed: Specified the drawing, aligned filled diagrams, hover values, pass/fail cards and ratio colors, apply-section action, instant updates, layout, styling, and initial beam/load.
- Worked: Yes; only the requested spec sections were changed, and no app was built.

- Asked: Update only Validation and Out of scope in `spec.md` with four hand-checked beam cases and the specified exclusions. Do not build anything.
- Changed: Added reactions, maximum moments, bending stresses, maximum deflections, and bending/deflection/overall results for each case; listed all requested exclusions.
- Worked: Yes; only the requested spec sections were changed, and no app was built.

- Asked: Build stage 1 from `spec.md` as a single-file `index.html` mockup with all inputs, outputs, and plots shown using realistic placeholders. Do not implement calculations.
- Changed: Replaced the empty HTML shell with a responsive static mockup, including beam/load drawing, three response plots, placeholder checks and recommendation, and all specified input controls.
- Worked: Yes; desktop and mobile layouts were checked and screenshots saved in `03_output/`.

- Asked: Build only stage 2 from `spec.md`; keep calculations in clearly named functions separate from drawing code.
- Changed: Added input state and controls for support, span, sections, loads, load bounds/clipping, snapping and beam drawing updates. Kept analysis outputs static and added no structural calculations.
- Worked: Yes; browser checks passed for bounds, syncing, load edits and dragging, support-specific defaults, section switching, clipping, and unchanged static outputs.

- Asked: Build only stage 3 from `spec.md`; put calculations in clearly named functions separate from drawing code.
- Changed: Added statics reactions, dense shear/moment event sampling, deflection integration, bending/deflection checks, and current-state analysis calculation. Corrected runtime steel Sx values using AISC-v16 transcriptions and recorded validation results and table discrepancies in `02_validation/stage3-analysis.md`.
- Worked: Yes; all four hand cases and additional equilibrium, shear-jump, clipping, and support-boundary checks passed. Visible plots and check cards remain static placeholders.

- Asked: Build only stage 4 from `spec.md`; keep calculations in clearly named functions separate from drawing code.
- Changed: Replaced static shear, moment, and deflection plots with calculated filled SVG diagrams, maxima, synchronized crosshair values, and calculated support reactions. Connected input changes, dragging, and keyboard nudges to redraws; kept check cards and recommendation static.
- Worked: Yes; browser checks for plot alignment, endpoint/load-point hover, drag/keyboard updates, reaction redraws, and mobile stacking passed. Results are in `02_validation/stage4-visual-checks.md`.

- Asked: Build only stage 5 from `spec.md`; keep calculations in clearly named functions separate from drawing code.
- Changed: Added live bending/deflection cards with ratio thresholds, PASS/FAIL states, steel/lumber passing-section selection, no-pass state, and Apply behavior. Kept analysis logic separate from card rendering.
- Worked: Yes; ratio boundaries, steel tie-breaking, lumber order, no-pass behavior, Apply selection, and all four validation cases passed. Details are in `02_validation/stage5-checks.md`.

- Asked: Build only the Print / Save PDF engineering summary report described in `spec.md`; do not alter calculations or screen layout behavior.
- Changed: Added a header print button, a print-only beam/load summary table, current report date, and portrait-letter print styling that hides interactive controls and retains the drawing, plots, checks, and recommendation.
- Worked: Print-media visibility and the default report's one-page layout were checked. Native PDF generation could not be exercised because the shared browser does not expose `Page.printToPDF`.

- Asked: Build only the Include beam self-weight feature described in `spec.md`.
- Changed: Enabled the default-OFF toggle, added the lumber weights, added self-weight as a derived full-span load in the calculation input path, used candidate-specific weights for recommendations, and labeled the load in the beam drawing and print summary.
- Worked: Yes; the W12x26 case with self-weight matches case 5, prior validation cases remain unchanged with the toggle OFF, and lumber/candidate-weight checks passed.
