# Bambu Studio details for CAD comparisons

Use only with Bambu projects or the installed Bambu Studio CLI. Names and behavior can change between versions; check current local help, configuration and result files.

In 3MF archives inspect project settings, model/object settings, component transforms, plate assignments and slice metadata. Confirm the actual printer/variant, nozzle, `filament_settings_id`, filament type, `print_settings_id`, and object-to-filament assignment. Thumbnails and stored slices may be stale.

Useful fit/settings fields include `printable_area`, `printable_height`, `bed_exclude_area`, `filament_shrink`, support settings and brim settings. Interpret values according to the installed version. When compensation is expressed as measured length / target length × 100, the geometric multiplier is its reciprocal, not the percentage itself; verify that convention before applying it.

Preset files can inherit other presets and include machine-code templates. Loading only the leaf JSON can miss relevant settings. Verify the effective values in the produced project/G-code; do not assume successful CLI invocation means the intended profile was used.

Examine per-plate warnings, object bounds, toolpath envelope and output files. A slice may succeed while project export fails. Validate the destination and CLI argument conventions before changing the print process.

Result fields for model and total material may account for brim differently from support. Verify the grouping, or cross-check extrusion by feature if needed. Check units rather than trusting a label blindly. Model-time estimates can omit preparation, calibration or filament handling.

If diagnostic machine-code changes were unavoidable, keep the results clearly separate from printable files and explain the limitation. Preserve the actual original profiles. A diagnostic file without normal startup, shutdown or tool handling must be resliced with the real profiles before printing.
