# CAD-linked print preparation

Use when preparing a FreeCAD part for printing or assessing its manufacturability. Keep the CAD assembly orientation distinct from trial print orientations.

## Export and settings

Export the intended final objects, without accidental hidden history or duplicate instances. Check units, placement and scale: STL has no explicit unit metadata, while other formats can store units and transforms. Check mesh closure, disconnected components and tessellation appropriate to the relevant detail; a valid solid does not establish a valid or sufficiently resolved mesh.

Read actual project settings instead of inferring material/nozzle/orientation from a thumbnail. Check machine, material and process profiles, per-object overrides, transforms and cached slice state. Resolve preset inheritance where needed and inspect the effective exported settings. Preserve the original project when comparing alternatives.

For Bambu-specific preset and result interpretation, read [Bambu slicer details](slicer-bambu.md).

## Orientation, supports and fit

Use the configured printable region and height, exclusions, compensation, brim and support envelope to check fit. A nominally bed-sized part has no working margin. Transform actual geometry for tilted or irregular parts; place the lowest intended contact on the bed and verify it is neither floating nor buried. Check the slicer's compensation convention and avoid applying it again in CAD.

Evaluate first-layer contact, stability, surface quality, bridging, support contacts and removal access. For hollow lattices inspect rib undersides: a flat outer rim does not mean the internal network grows from the bed. Tilting may increase supports rather than reduce them. Compare orientations under the same declared material/process assumptions before optimizing individual candidates.

Inspect layer/toolpath previews, including initial layers and difficult transitions. A printable envelope and a warning-free slice do not establish that supports can be removed without damaging a flexible or delicate part. Contact on mating features or skin-contact surfaces can matter more than support mass.

For fit trials use the intended material, orientation and process as closely as practical. Geometry can change structural compliance but cannot by itself reproduce a different material's surface feel. Representative coupons can test local manufacture and fit without proving full-part stiffness.

## Local test pieces

Choose a coupon around the uncertainty being tested: hole alignment, an insert pocket, a latch, surface finish or a difficult unsupported region. Preserve the source model and identify the source revision and any changed dimensions on the test piece.

For a simple planar hole-pattern check, a selected face can be extruded into a slab while retaining its inner boundaries. Verify planarity, oriented face normal and intended extrusion direction; do not assume the face is X-aligned or that the underlying surface axis is the outward normal. Choose thickness for the actual test, not an unrelated default.

A face extrusion does not reproduce counterbores, internal tapers, blind-hole depths or geometry behind the selected face. When these matter, extract a volume containing the real features. For compliance or support-removal tests, include enough surrounding ribs, walls and attachment geometry to represent the local behavior. Explain what the reduced specimen omits; it cannot establish whole-part stiffness, warping or comfort.

## Validate and report

Use installed CLI capabilities when useful, after checking current help and supported settings. Separate model import, slicing, preview and project-export failures. Inspect result metadata and logs rather than relying on an exit code alone. Reslice after changes; old cached G-code is not evidence for the new placement.

Compare time/material estimates only when their definitions and assumptions match. Distinguish support, brim and model quantities where relevant. Identify derived toolpath plots as such and disclose material approximations; do not present them as native slicer screenshots.

Label incomplete or deliberately modified diagnostic outputs as analysis-only. Restore the actual machine/material settings and reslice before calling an output print-ready. Do not strip machine macros as a routine fix for an export failure. A local preparation task does not authorize uploading or starting a print.
