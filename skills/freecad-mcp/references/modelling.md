# Parametric modelling and assemblies

## Sketches and dependencies

Inspect the existing constraints and expressions before editing a sketch. Distinguish driving dimensions from reference measurements, construction geometry from profiles, and intentional freedom from missing constraints. Check closed profiles where a feature requires them. Resolve conflicting or redundant constraints at their source; do not add dimensions simply to make the solver report fully constrained.

Use explicit units when assigning dimensions. Give shared design dimensions meaningful aliases or properties and reference them through expressions. Avoid circular dependencies. After a parameter edit, check the affected downstream features and their attachment state, not just the edited sketch.

Prefer stable datum geometry and intended design references over incidental edges of generated faces when practical. Face/edge indices and geometric selection heuristics can both change after topology changes. Verify selected references after edits; do not assume a particular FreeCAD version's topological naming mitigates every case. Preserve working references unless changing them serves the task.

## Coordinates and assembly intent

Identify local versus global coordinates, including nested Body, App::Part and App::Link placements. Verify whether Shape already includes an object's placement before transforming it; do not apply the same transform twice. Account for instance transforms when measuring repeated parts.

Distinguish merely positioning components from defining assembly constraints or joints. Follow the assembly workbench already in use when suitable, and inspect its available APIs rather than mixing incompatible constraint systems.

For dimensions that must match, use a shared source where practical. Define clearance explicitly as radial, diametral, per-side or total; do not mix these conventions. Separate nominal geometry, manufacturing allowance and measured fit. Account for accumulated tolerances when several features set a position. Check insertion and removal, not only the final assembled intersection.

## Invariants and comparisons

Measure the properties the user wants preserved. A total footprint includes protrusions, clips and flexible parts if they are within the user's scope. A matched bounding box is a coarse check; use section contours, projected outlines, surface distances or Boolean differences when those better express the requirement. State numerical tolerance and the limits of sampled comparisons.

For alternative designs, retain a clear approved baseline and identify the active candidate. Avoid accumulating indistinguishable copies or relying on labels alone as object identifiers. Do not delete source history or the user's comparisons merely to tidy the tree.
