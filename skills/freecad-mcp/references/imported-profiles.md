# Imported profiles and reference images

Use when deriving CAD geometry from DXF, SVG, raster references or imported exchange files. Preserve the source and distinguish measured requirements from inferred geometry.

## DXF/SVG to solid

Inspect units, scale, layers, transforms and a known dimension before modelling. Separate manufacturing contours from text, dimensions, hatching and construction lines. Account for the importer's settings; do not assume every imported object is part of the profile or that its coordinate system matches the target sketch.

Check intended contours for coplanarity, closure, duplicate segments, self-intersections and small gaps. Choose repair tolerances relative to the geometry and required accuracy. Do not close an intentional slot or erase a small feature merely to obtain a valid wire.

Determine boundary nesting, including holes, islands and disconnected parts. Avoid treating the first wire as the outer boundary or the largest loop as the only part. Build faces that preserve the intended voids, then check area and topology before extrusion. Resolve extrusion depth and direction from the task rather than adopting a project-specific plate thickness.

When continued editing is needed, use a manageable sketch or another suitable parametric representation. Converting a dense imported outline into thousands of constrained segments may be less useful than retaining the source profile and parametrizing the downstream operations. Inspect the imported geometry before deciding.

## Images to sketches

Use a known dimension or calibration reference for dimensional work. If unavailable, an explicitly unscaled concept can still be useful, but must not be presented as a dimensionally accurate part. A single scale factor does not correct perspective, lens distortion or different depths in a photograph. Prefer an orthographic reference or measurements when mating geometry matters.

Define the sketch plane, origin and image-to-model transform. Account for pixel Y direction, rotation and mirroring, and check a second independent dimension when possible. Distinguish object contours from shadows, dimension lines and hidden lines.

Represent intended lines, arcs and symmetry with suitable geometry and constraints; avoid tracing pixel noise or approximating every curve with many short lines. Mark uncertain features and use supplied dimensions ahead of visual estimates. Modify existing dimensions and geometry without routinely clearing constraints or downstream references.

## Exchange-file checks

Track the objects created by an import rather than assuming the first document object is the part or exporting every object in the document. An imported STEP shape does not restore the original feature history; a mesh import does not become an editable solid merely by appearing in the viewport.

For a conversion deliverable, reopen the export in an isolated document or process and compare relevant dimensions, solid count, holes and placement to the intended result. Check volume or contour agreement where it adds confidence. Keep tolerances appropriate to the format and units; neither a nonempty file nor a successful exporter return proves a correct conversion.
