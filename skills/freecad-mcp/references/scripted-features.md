# Scripted parametric features

Use when native features are insufficient or an existing model uses FeaturePython. A property list attached to a fixed shape is not a parametric generator.

## Dependencies and recompute

Expose a small set of meaningful inputs and explicit source links. State which inputs are live references and which are fixed snapshots. Keep the controlling object and final output unambiguous, especially when a lightweight downstream feature modifies an expensive source. Avoid recomputing identical shared geometry independently for every repeated accessory.

Choose between ordinary automatic recompute and an explicit expensive rebuild. Ordinary features should update their geometry from changed inputs. An explicit-rebuild design should mark changes pending, preserve the approved shape while computing, and propagate that pending state to downstream results. Do not label an old shape as representing new parameter values.

For isolated workers, snapshot the parameters and source geometry. Publish on the GUI thread only after required checks pass and the document, target and inputs still match the request. Reject stale results and retain the approved shape on failure. Use transactions for publication and save explicitly afterward when appropriate.

Initialize a supported view provider and verify the viewport. Visibility=True and a valid Shape do not prove a new scripted object is rendered. Preserve supported material/appearance properties when replacing shapes.

## Persistence and delivery

Test a saved document in a fresh process with its required modules loaded. Verify proxy restoration, source links, parameter values, recompute and shape state. Test that an ordinary feature actually changes geometry; for explicit-rebuild features test pending detection and a genuine controlled rebuild. Changing and restoring a parameter should recover the expected state. Input ranges do not certify every parameter combination.

Avoid external document links or absolute machine-specific paths unless intentional and disclosed. Package required modules and an appropriate loading mechanism, or document the required installation. Test reopening with those delivered dependencies rather than relying on the current session's imports. Check optional workbench compatibility as needed.

## Change detection for expensive builds

Use explicit inputs and a documented geometry signature only where a cached/approved result needs one. Raw BREP bytes may change after save/restore because of numeric formatting or kernel state flags. If normalization is necessary, exclude only verified non-geometric differences and retain topology, placements and meaningful geometry. Test that real geometry edits still invalidate the result. Do not reset signatures on every load just to conceal restore mismatches.
