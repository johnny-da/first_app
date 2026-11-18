# Stage 4 Visual and Interaction Checks

- Default 20 ft simply supported beam renders calculated support reactions of 10 k each, shear/moment/deflection paths, and maxima of 10 k, 50 kip-ft, and 0.609 in.
- All three plot SVGs use the same x mapping and tick positions. Hovering at midspan places all three crosshair lines at x = 10 ft and reads V = 0 k, M = 50 kip-ft, y = 0.609 in.
- With a 10 k point load at 5 ft, hovering at the load reads the post-load shear of 2.5 k and continuous moment of 75 kip-ft; crosshair positions match across all plots.
- Dragging the point load from 5 ft to 6.75 ft updates its input, stored analysis, reaction labels, and plot paths. Keyboard arrow movement advances it by 0.25 ft and refreshes the plots.
- Span, support, and section changes redraw the analysis plots and reaction diagram. Check-card values remain the stage-3 placeholders.
- At the browser's mobile layout width, analysis precedes inputs, all three SVG plots have equal widths, and the document has no horizontal overflow. The browser host's visual viewport is narrower than its layout viewport, which crops the screenshot at the right edge when zoomed; measured page content remains within the layout viewport.
