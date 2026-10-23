# team-topologies-skill

A Claude Code plugin with two skills for working with [Team Topologies](https://teamtopologies.com/) (Matthew Skelton and Manuel Pais): one for designing and reviewing team structure, one for drawing team maps with the official modeling shapes.

The goal throughout is **fast flow**: the shortest time from a need appearing to its fix running in production. Both skills judge every choice by what it does to flow.

## Skills

### `team-topologies`

A reference and review checklist for team design. Claude uses it when you design or review team structure, assign ownership, size teams or draw a team map, or when you mention team types, interaction modes, cognitive load, Conway's law or fracture planes.

It covers:

- **Review procedure**: eight checks (type, size, ownership, cognitive load, interactions, flow, Conway, anti-patterns). Each gets a verdict of holds, strained or broken, with the team concerned and the evidence.
- **Teams**: stable groups of 5–9 people, with owned areas and a mix of specialists and T-shaped generalists.
- **The four team types**: stream-aligned, enabling, complicated subsystem and platform, including the "thinnest viable platform" idea.
- **The three interaction modes**: collaboration, X-as-a-Service and facilitating, and how modes evolve over time.
- **Cognitive load**: intrinsic, extraneous and germane load, and how to size software to fit the team.
- **Conway's law** and the inverse Conway maneuver.
- **Fracture planes**: where to split a monolith or domain (business domain, regulation, rate of change, performance, and more).
- **Anti-patterns** and **signals** that a team or its area should change.
- A short glossary of **Norwegian terms**.

### `team-topologies-shapes`

How to draw Team Topologies diagrams. Claude uses it when you draw, redraw or review a team map or team interaction diagram, in SVG or any diagramming tool.

It covers:

- **Drawing steps** and a definition of done for a diagram.
- **Shape table** with the official shape, fill and stroke for each team type, interaction mode and grouping.
- **The nine diagramming principles**, such as flow from left to right, handovers drawn as diamonds, and no team between stream-aligned teams and their customers.
- **Modelling stages** for working through a model with a group: as-is, first evolution and cognitive load.
- **Inline SVG recipes** for each shape, ready to paste into a web page.

The two skills work together: `team-topologies` supplies the concepts and the review, and `team-topologies-shapes` supplies the drawing.

## Install

Add this repository as a marketplace and install the plugin:

```
/plugin marketplace add hnilsen/team-topologies-skill
/plugin install team-topologies@team-topologies-skill
```

To install without the plugin system, copy the skill folders into `~/.claude/skills/` (all projects) or `<project>/.claude/skills/` (one project):

```sh
cp -r plugins/team-topologies/skills/* ~/.claude/skills/
```

## Layout

```
.claude-plugin/marketplace.json
plugins/team-topologies/
├── .claude-plugin/plugin.json
└── skills/
    ├── team-topologies/SKILL.md
    └── team-topologies-shapes/SKILL.md
```

## Sources and credits

- *Team Topologies* by Matthew Skelton and Manuel Pais.
- The `team-topologies` skill is based on Anders Skifte's summary of the book, [Oppsummering av Team Topologies](https://medium.com/smidigalliansen/oppsummering-av-team-topologies-5a5ab0bef926) (Smidigalliansen, 2019).
- The `team-topologies-shapes` skill follows [How to use the Team Topologies Modeling Shapes](https://teamtopologies.com/how-to-use-shapes) and the official [Team Shape Templates](https://github.com/TeamTopologies/Team-Shape-Templates). The shapes are © Team Topologies, licensed [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). Diagrams that use them should carry the line "Shapes: Team Topologies, CC BY-SA 4.0".

## License

MIT, see [LICENSE](LICENSE). The Team Topologies shapes described in `team-topologies-shapes` keep their own CC BY-SA 4.0 license.
