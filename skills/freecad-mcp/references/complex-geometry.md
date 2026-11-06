# Complex geometry and expensive operations

Use for dense patterns, difficult fillets, spline repair or kernel operations likely to block. Ordinary modelling does not require this entire workflow.

## Diagnose and reduce the problem

Distinguish basic shape validity, per-face checks, full-shape BOP checks and mesh checks. Passing one does not establish the others. Inspect maximum stored geometry tolerance where supported: unusually large tolerances can conceal a local failure. Judge tolerances relative to part scale and function; no universal repair tolerance fits every model.

Isolate the offending feature or edge loop before rebuilding everything. Use geometric selections tied to design intent rather than hard-coded topology indices, and verify those selections after changes. Neither centroid height nor bounding-box height alone universally identifies the upper face of a curved shell.

Use cheap previews to resolve layout decisions before expensive operations. For repeated openings, a grid-phase change can improve boundary cells without changing pitch or the outer envelope. Check actual sliver shape; bounding-box width can accept a thin diagonal fragment. Keep preview and approved geometry distinguishable.

Stage operations into useful checkpoints such as envelope, cutters, Booleans, fillets and repair. Reuse unchanged stages during diagnosis. A new parametric generator must also rebuild genuinely from its declared inputs; returning a stored final shape is not a baseline rebuild test.

Try operation orderings appropriate to the geometry. Rounding an outer envelope before perforation may avoid a much more complicated edge network. Local fillets can succeed where a collective operation fails, but can be slower and may require visibly different radii. Record fallbacks, retain stage/count progress and check the final combined shape. Do not silently weaken a requested radius or feature to obtain a valid solid.

## Spline repair

A continuity finding such as `GeomAbs_C0` may concern representation rather than a visible crack. Distinguish it from self-intersection, invalid curves on surfaces, and tiny edges.

If the installed runtime provides PythonOCC and FreeCAD's conversion bridges, `ShapeUpgrade_ShapeDivideContinuity` with suitable boundary, pcurve and surface criteria is one possible repair tool. Check API availability before use. Choose 2D and 3D tolerances deliberately: stricter settings can introduce microscopic edges. Do not broadly raise tolerances to suppress unexplained errors.

Verify geometry again after healing. Compare shape, bounds, solids and critical interfaces with the approved source. Large volume differences can reflect either actual geometry changes or numerical integration sensitivity; investigate rather than assuming either explanation. Sampled surface distances are not guaranteed global maximum deviations.

## Tolerance and contact in Booleans

Read the maximum stored tolerance before and after each Boolean and compare it with the inputs rather than with an absolute number. A jump of an order of magnitude marks a damaged result even when validity checks still pass; reject it instead of saving it. Inputs that already carry a large tolerance, for example from earlier cuts or lofts, make later Booleans fragile.

Avoid coincident or nearly coincident contact: a feature starting exactly on a cut face, a cutter built from the same sphere or surface that made an existing face, or a feature placed within the stored tolerance of an existing face or edge. Overlap a new feature into the material by a margin and let it end clear of shared surfaces. Test one feature at several positions before committing all of them; a tolerance jump that depends on position points at local face quality, not at the feature. Then add the small features in one combined operation per heavy shape.

Operations between shapes that only touch along a face, such as two halves of a split part, can be extremely slow. Check clearance on isolated features or on snapshots instead.

For results built from spline lofts, B-rep volume can be unreliable and may disagree with the expected material by a large factor. Cross-check with the volume of a closed tessellated mesh, and treat valid single-solid topology together with a closed mesh as the minimum before accepting a result.

If offsetting a composite spline outline returns a null result, approximate the outline as a dense polygon and use rounded joins; rebuild smooth curves through the offset points when a low-face-count result is needed.

## Execution and validation

Run risky operations on independent snapshots outside the live GUI where possible. Check the operation result before applying it to the document. For long BOP checks, retain compact progress and explicit error summaries; exceptions are failures, not empty diagnostic results.

If native OCCT diagnostics must be redirected, do so only in the isolated worker and restore file descriptors. Process-wide output redirection in a live application's background thread can affect unrelated work.

For persistent generators, publication and rebuild state, also read [scripted features](scripted-features.md).
