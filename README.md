# FreeCAD skill

An agent skill for creating, inspecting, editing and validating FreeCAD models through an available FreeCAD integration.

The skill focuses on preserving design intent, maintainable parametric models, efficient handling of complex geometry, and checks proportionate to the change. Specialized references cover sketches and assemblies, Lattice2, scripted features, technical drawings, imported profiles and images, manufacturing and print preparation.

## Requirements

- FreeCAD and a working integration that lets your agent inspect and modify models.
- An agent that supports SKILL.md-based skills. The included UI metadata targets Codex.
- Optional workbenches or slicers only when the requested workflow needs them.

This package supplies instructions, not FreeCAD or an MCP server. Tool names and optional capabilities are discovered at runtime. It contains no CAD project files or machine-specific configuration.

## Install in Codex

Ask Codex:

```text
Use $skill-installer to install the skill from:
https://github.com/LeonB/freecad-skill/tree/main/skills/freecad-mcp
```

Alternatively, copy the entire `skills/freecad-mcp` directory into your personal `~/.agents/skills/` directory. For project-scoped use, place it in `.agents/skills/` within that project. Preserve the `references/` and `agents/` subdirectories. Avoid installing duplicate copies with the same skill name, including an existing copy under `~/.codex/skills/`.

Codex detects skill changes automatically; restart it if the skill does not appear. See the [official skill documentation](https://learn.chatgpt.com/docs/build-skills).

Other agents may use different installation locations. Follow their skill-discovery instructions and configure the FreeCAD integration separately.

## Use

Examples:

- `Use $freecad-mcp to inspect this model for interference and report the measured clearances.`
- `Make a copy, change the wall thickness, and preserve the mounting-hole positions.`
- `Create a dimensioned drawing with a section through the internal cavity.`
- `Extract a representative fit-test coupon from this part and explain what it can verify.`

## Updates and sharing

Use tagged releases for reproducible installations. On another computer, install the same release and configure FreeCAD locally. Updating a downloaded skill is a separate operation; a GitHub push does not automatically update installed copies. Back up local modifications before replacing an installation.

## Validation and limitations

The package has passed skill-format validation and local-reference checks. The guidance incorporates practical CAD workflows, but it is not a guarantee of compatibility with every FreeCAD version, workbench, MCP server or manufacturing process. The recently added drawing and import workflows have been reviewed but have not yet been exercised end to end in FreeCAD. Geometric checks, slicer checks and physical tests establish different things.

## Contributing

Keep guidance general and concise. Put conditional detail in a focused reference linked from SKILL.md. Include a reproducible example when reporting a failure; do not add private project files, credentials or personal filesystem paths. Explain what you tested and which FreeCAD/integration versions were used.

## License

MIT; see [LICENSE](LICENSE).
