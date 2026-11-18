# Stage 5 Check and Recommendation Validation

## Default Beam
- 20 ft simply supported W12x26 with 1 kip/ft: bending is 17.964 ksi / 30 ksi = 59.9%, green, PASS. Deflection is 0.608519 / 0.666667 in = 91.3%, amber, PASS.
- Steel recommendation is W14x22 at 22 lb/ft, the lightest listed steel section passing both checks. Apply selects W14x22 and recalculates the current result.
- Full current-analysis plus recommendation refresh measured about 13.8 ms in the browser.

## Decision Rules
- Usage boundaries: 69.99% is green, 70% is amber, 100% is amber, and values above 100% are red.
- Equal-weight steel case selects W16x26 over W12x26 because W16x26 has larger Ix.
- Lumber case recommends 2x8, the first passing size in catalog order.
- A 40 ft cantilever with a 1000 k tip load has no passing section; the UI reports that none pass and disables Apply. Both check cards show FAIL with red ratios.

## Validation Cases
All four cases still match `stage3-analysis.md`: cases 1, 2, and 4 pass both checks; case 3 passes bending and fails deflection. Calculated reactions, maximum moments/stresses/deflections, and tolerances are unchanged.

## Responsive Check
Browser layout measurements report no horizontal overflow in desktop and mobile layouts; the mobile analysis column precedes the inputs. The integrated browser screenshot capture produced tiled/repeated page images, so those images are not reliable visual evidence. Responsive conclusions here are based on DOM geometry and viewport measurements.
