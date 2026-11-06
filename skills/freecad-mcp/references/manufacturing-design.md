# Manufacturing considerations in CAD

Use for compliant structures, locating closures or designing casting molds. These checks guide geometry; they do not certify material behavior or a manufacturing process.

## Compliant structures

Separate overall shape, compliant geometry and attachment geometry when practical. Rib thickness, depth, free span and boundary support influence structural response. Material hardness, surface texture and friction influence contact feel. Changing material can alter retention and tear resistance even when dimensions remain identical.

Compare one meaningful variable at a time in prototypes. Include actual curvature and relevant boundary/mating features in a coupon. A cut-out patch has different boundary stiffness from the complete part, so distinguish comparative/local results from full-part behavior. Verify geometry again after parameter changes.

## Locating closures and mating parts

Identify which features locate each degree of freedom and which provide retention. Where flushness matters, reference both surfaces to a shared datum and provide a controlled depth location, such as a shoulder; a friction fit alone may not set depth reliably. Account for tolerance accumulation and adhesive thickness or escape paths when adhesive is part of assembly.

Check seating engagement, lateral clearance, insertion/removal, and interference with enclosed components. Include functional gaps such as magnet-to-target separation in the dimensional requirements. Nominal CAD contact does not prove printed flatness, sealing or retention.

## Printed snap hooks

For a first estimate of a cantilever hook, relate the outer-fibre strain to thickness t, free length L and deflection d by strain = 1.5 t d / L^2, and compare it with a conservative limit for the actual material and orientation. This guides geometry only. Layered prints are weaker across layers, so a hook that stands upright in the print bends against its weakest direction and can fail well below the estimate. Prefer geometry whose bending stress runs along the layers, add a fillet at the root, and lengthen or thicken the beam when the margin is thin.

Allow clearance for printing error on every sliding or catching surface, and measure it on the actual sloped contact rather than along one axis. Check that the catch can be printed: a catch hanging from a wall prints as an overhang. Provide insertion and release slopes when repeated opening is required, and expect some vertical play before the hook engages. Keep new features clear of existing face tolerance (see [complex geometry](complex-geometry.md)). Print a coupon in the real orientation and material before applying hooks to the whole part, and label the design as calculated, not tested, until then.

## Casting-mold geometry

Evaluate filling, air escape and demolding separately. Channel width alone does not establish fillability: inspect constrictions, branching paths, last-fill regions and high points in the intended mold orientation. Degassing mixed material does not replace cavity venting.

Choose parting surfaces, core placement and release directions before constructing a simple Boolean negative. Undercuts may need removable inserts or split mold pieces. Perforations require reliable shutoff surfaces; gaps there can cast membranes over intended openings. Design registration, closing stops, clamping and paths for gates, vents and overflow. Keep seams and gate remnants away from critical surfaces where possible.

Check that mold components themselves can be manufactured and assembled. Consider draft, surface finish and texture transfer where relevant, without prescribing a universal draft angle or mold clearance. Verify material compatibility, flow and cure requirements from current supplier information for the actual mold surface/coating. Mark an unbuilt or untested mold as a proposal; validate process assumptions with an appropriate trial.
