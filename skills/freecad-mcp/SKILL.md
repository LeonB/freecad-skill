---
name: freecad-mcp
description: Create, inspect, edit, and validate FreeCAD models through an available FreeCAD integration. Use for parametric modelling, sketches, assemblies, geometry repair, and CAD-linked manufacturing or export checks. Not for unrelated slicer operation or development of an MCP server.
---

# FreeCAD modelling

## Establish the task and live state

Discover the available FreeCAD tools and their schemas; do not assume a particular server, tool name, filesystem layout, or installed workbench. Check FreeCAD/OCCT versions and optional capabilities when the operation depends on them. If direct integration is unavailable, use an available supported workflow or explain the missing capability; do not pretend a file edit changed the live model.

Inspect the relevant open document, file path, object Names and Labels, dependencies, Body Tips, placements, visibility, and error state. Saved files may differ from unsaved live work. Read applicable project instructions, treating dated notes as context rather than overriding current user intent.

Before changing geometry, identify the requested change and the properties that must remain unchanged: for example a mating contour, overall envelope, hole locations, wall thickness, or appearance. Use existing requirements and measurements; ask only when an unresolved choice materially changes the design. Preserve the source when the user requests a copy or comparison.

## Choose a maintainable representation

Prefer editing the feature, sketch, or expression that controls the geometry. Keep a small set of meaningful parameters and preserve downstream dependencies. Use native modelling features where practical; use scripted geometry when it materially improves the result. Label static snapshots as static and distinguish source/control objects from the final export objects.

Use a group for organization, an App::Part for an assembly coordinate system, links for shared instances, a compound for separate shapes, and a fusion for joined material. A PartDesign Body normally represents one contiguous solid with a coherent feature history. Verify that the chosen representation matches the intended parts.

Read only the reference relevant to the task:

- [Parametric modelling and assemblies](references/modelling.md): sketches, constraints, references, placements, mating features, and tolerance definitions.
- [Technical drawings](references/technical-drawings.md): TechDraw views, dimensions, annotations, and verified drawing exports.
- [Imported profiles and reference images](references/imported-profiles.md): DXF/SVG contour preparation, image calibration, extrusion, and exchange-file checks.
- [Lattice2 patterns](references/lattice2.md): inspecting or creating irregular repeated placements with that optional workbench.
- [Complex geometry](references/complex-geometry.md): expensive Booleans, fillets, splines, and local repair.
- [Scripted parametric features](references/scripted-features.md): FeaturePython, expensive rebuilds, persistence, and delivery dependencies.
- [Print preparation](references/print-preparation.md): CAD exports, print orientation, supports, and slice validation; includes a link to optional Bambu-specific details.
- [Manufacturing design](references/manufacturing-design.md): compliant structures, flush closures, or casting-mold geometry.

## Execute safely in the live session

Wrap a coherent document edit in a transaction where supported. Recompute at dependency boundaries, check the result, then commit or abort. Committing is not saving. Preserve unrelated placements, visibility and material appearance; use supported view APIs for the installed version.

Document and GUI operations belong on the GUI thread. Use asynchronous tools only according to their documented thread and commit semantics. Run potentially blocking or crash-prone kernel operations on independent snapshots in an isolated process when available. Never overwrite or reload an open document from an older file to recover from a failed operation.

A timeout may leave a mutation running. Inspect its status and the live document before retrying; do not queue duplicate edits. Preserve unsaved work and report a concrete blocker if execution is stuck. Do not kill or restart the user's application without authorization.

## Verify proportionately and deliver

Scale checks to the change. Appearance-only edits need visual verification; ordinary geometry edits need relevant feature state, non-null/valid shapes, expected solid counts and dimensions. Use full BOP and mesh checks for operations whose complexity or failure modes warrant them. Recheck affected dependencies and interfaces, without repeating expensive checks on unchanged geometry unless new evidence calls them into question.

Compare the stated invariants against the approved source. Matching bounding boxes alone does not prove matching contours or surfaces. For fit, inspect actual clearances, interference and assembly/removal paths in a common coordinate system. Zero overlap does not prove manufacturability or reliable retention.

For visual comparisons, use consistent scale, camera, color and visibility. Include sections or other views when needed to expose the changed geometry. A valid Shape does not establish that the correct object is displayed.

Export the explicitly intended parts, including coupons or supports when requested; exclude unintended history and duplicates. Verify format, units, transforms and representation. Clearly distinguish checked CAD geometry, checked slices, and physically tested parts.

Report what changed, what was preserved, relevant checks, limitations, saved paths and reopening dependencies. Keep project-specific dimensions, materials and trial results in project notes, not in this general skill.
