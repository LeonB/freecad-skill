# Technical drawings and annotated views

Use for drawings derived from a FreeCAD model. Distinguish a linked engineering drawing from a static explanatory illustration; choose the representation that serves the requested deliverable.

## Sources, views and layout

Use the intended final objects or assembly instances as drawing sources. Check placements and visibility, and exclude duplicate history. Discover the installed TechDraw capabilities and templates rather than relying on guessed filenames or export APIs. Some rendering/export paths require a GUI; a headless model operation succeeding does not establish drawing-export support.

Establish the drawing's front direction, projection convention, units and page size. Fit views and annotations within the actual printable area and title block, using projected extents and scale rather than fixed page coordinates. Keep related orthographic views aligned; state different scales for detail views. Use sections to expose internal relationships and detail views for small features instead of crowding the main view.

## Dimensions and feature identification

Attach dimensions to the intended view geometry and verify the referenced entities after model changes. Distinguish projected measurements from true lengths on inclined geometry. Check important dimension values against the source model; do not replace measured values with desired labels to conceal a mismatch. Preserve a specified drawing standard and avoid inventing tolerances or manufacturing requirements.

Select faces using surface type, position, orientation, extent and design intent together. A normal direction alone can identify several unrelated faces; a surface's Axis property does not establish planarity. For extracted planar outlines, identify the outer boundary explicitly and preserve inner boundaries rather than assuming wire list order. Treat slots, polygons and segmented circles according to their actual geometry; do not classify every inner wire as a circular hole.

A measured diameter alone does not establish thread size, pitch, depth or fit. Obtain such callouts from feature properties, specifications or confirmed requirements. If only geometry is known, report the measured diameter and the uncertainty. Keep 3D coordinates until applying a defined view frame; check handedness and opposite views to prevent mirrored annotations.

## Export verification

Use the exporter for the requested format; changing an extension does not convert a file. Verify that the result opens in that format and inspect the rendered page for clipped views, missing dimensions, overlapping leaders, unreadable text and stale geometry. File existence or size alone is insufficient.

Retain the editable drawing and its model dependencies when requested. For a physical template, verify a known dimension at actual print size and state the intended print scale. An automatically fitted illustration is not a calibrated template.
