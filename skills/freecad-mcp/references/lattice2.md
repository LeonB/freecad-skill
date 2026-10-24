# Optional Lattice2 patterns

Use when the project already uses Lattice2 or irregular sketch-driven placements justify it. Confirm the workbench and relevant object types are available. Native patterns or links may be simpler for regular repetition; do not add a workbench dependency without a useful reason.

Model one source feature and repeat it rather than maintaining unrelated copies. A common positions sketch can drive both sides of a mating pair. An Attachable Placement may reference a sketch vertex, with an Attached Placement Subsequence enumerating the remaining positions. Separate chains can share positions while using different orientations or height offsets.

Inspect the installed pattern's `FeaturesToCopy`, `BaseFeature`, `PlacementsFrom`, `PlacementsTo`, `Referencing` and `SignOverride` where present. The source placement defines the reference frame; it need not be the source object's origin. Check attachment offsets and parent placements. Determine whether material is added or removed from the actual result, not the label.

After editing or reordering placement-driving geometry, verify count, order, orientation, alignment, resulting solids and Body Tips on both mating parts. Preserve an established working setup unless the requested change needs a different construction. Include the workbench dependency when delivering files.
