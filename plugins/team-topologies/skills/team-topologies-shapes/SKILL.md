---
name: team-topologies-shapes
description: How to draw Team Topologies diagrams with the official modeling shapes, colours and diagramming principles. Use when drawing, redrawing or reviewing a team map, team interaction diagram or Team Topologies figure, in SVG or any diagramming tool.
---

# Drawing Team Topologies

Sources: Team Topologies, "How to use the Team Topologies Modeling Shapes" (https://teamtopologies.com/how-to-use-shapes), and the official templates in https://github.com/TeamTopologies/Team-Shape-Templates (draw.io and Excalidraw libraries). The shapes are © Team Topologies, licensed CC BY-SA 4.0. Any diagram that uses them carries the attribution line: "Shapes: Team Topologies, CC BY-SA 4.0".

For the concepts themselves (team types, interaction modes, cognitive load, the review checklist), use the `team-topologies` skill. This skill covers the drawing.

A team interaction model is a **snapshot** for discussion, not an org chart and not a taxonomy. It shows how change flows to customers and where cognitive load sits.

## Steps when drawing or redrawing a diagram

1. **Flow**: put customers on the right, so change flows from left to right. Add the dashed grey "flow of change" arrow if the flow isn't obvious.
2. **Teams**: draw every team with its official shape and colour (see the shape table below). Any team that doesn't behave like one of the four types gets the undefined team shape. Don't force it into a type.
3. **Nothing between stream-aligned teams and customers**: if a team does sit there (a release or QA stage, for example), draw it as an undefined team and put a handover diamond on each handoff. Then the problem is visible instead of hidden.
4. **Interactions**: put an interaction shape on the boundary between the two teams. X-as-a-Service is a triangle pointing at the consumer. Collaboration is a parallelogram, facilitating is a circle. Draw any ongoing collaboration as an undefined interaction. When one interaction spans several teams, mark the teams involved with a black asterisk "*".
5. **Groupings**: platforms are a square-cornered dotted rectangle around the platform teams. Value stream groupings and other groupings use the same outline. A platform can contain lower-level platforms, so nest them freely.
6. **Size**: draw a team with a bigger responsibility as a bigger shape of the same type.
7. **Snapshot**: label the diagram "as-is" or "to-be" and add a date. Show an evolution as a sequence of snapshots.
8. **Check** the result against the shape table and the nine principles, and fix every deviation, or name it in the caption.

A diagram is done when every team has an official shape, every arrow-like relationship is one of the interaction shapes, nothing but customers sits to the right of the stream-aligned teams (or the exceptions are drawn as undefined teams with handovers), and the caption carries the snapshot label and the attribution.

## Shape table

Team shapes are **solid** (opacity 100%), because teams are long-lived. Interaction shapes are **50% opacity with a dashed stroke**, because interactions are meant to change. The shapes are designed to stay distinguishable without colour, so always keep the shape and orientation, not just the colour. Stroke width is 2.

| Element | Shape | Fill | Stroke |
|---|---|---|---|
| Stream-aligned team | horizontal rectangle, rounded corners | `#FFEDB8` | `#FFD966` |
| Enabling team | **vertical** rectangle, rounded corners | `#DFBDCF` | `#C27BA0` |
| Complicated subsystem team | octagon | `#FBDBBA` | `#F6B26B` |
| Platform team | horizontal rectangle, square corners | `#B7CDF1` | `#6D9EEB` |
| Undefined team type | horizontal rectangle, rounded corners, **dotted** border | none / white | `#000000` |
| X-as-a-Service | triangle, point towards the consumer | `#B4B4B4` at 50% | `#999696`, dashed |
| Collaboration | parallelogram | `#E3E0EE` at 50% | `#967EE2`, dashed |
| Facilitating | circle | `#E3EFDE` at 50% | `#78996B`, dashed |
| Undefined interaction | rectangle, square corners | none | dashed |
| Temporal coupling | trapezoid | none | dashed |
| Handover | diamond | none | dashed |
| Platform grouping | rectangle, square corners | none | dotted |
| Value stream grouping | rectangle, square corners | none | dotted |
| Undefined grouping | rectangle, square corners | none | dotted |
| Flow of change | wide arrow pointing right | none | `#595959`, dashed |

Enabling teams are pink in the official tools. The book printed them purple, but use the template colours. The book's other old forms are retired too: hatched squares for collaboration, dotted circles for facilitating, and two white bars for X-as-a-Service.

## The nine diagramming principles

1. Change flows from left to right.
2. Draw teams that don't behave like a Team Topologies type as undefined teams.
3. Make handovers obvious with the handover diamond.
4. Stream-aligned teams have no handoffs. No other team stands between them and their customers.
5. Stream-aligned teams don't provide X-as-a-Service directly. Their data or services are offered through a platform.
6. When X-as-a-Service or collaboration spans several teams, mark the teams with "*".
7. Collaboration is short and purposeful. Draw an ongoing one as an undefined interaction.
8. Platforms are fractal: a platform can depend on lower-level platforms.
9. Capture "as-is" and "to-be" as snapshots of each evolutionary step.

## Modelling stages

Use these when building a model with a group. Model together, never alone.

- **Stage A, as-is**: list today's teams using whatever names the organisation uses. Map each team to a type, or to undefined. Trace the flow from idea to production and mark every handover and bottleneck. Map the interactions, using undefined interactions where in doubt, and flag long-running collaboration.
- **Stage B, first evolution**: replace the undefined teams with stream-aligned teams of 5–9 people that own the flow end to end. Repeat until no undefined teams are left.
- **Stage C, cognitive load**: mark the sources of load on each stream-aligned team (the guide uses a brain sticker). Then, in this order, check whether each source can be removed:
  - Can a platform team take it over as X-as-a-Service?
  - Can a complicated subsystem team take it over, first in collaboration and then as X-as-a-Service?
  - Can an enabling team close a skill gap by facilitating, for a limited time?
  
  Keep sensing, and redraw when flow slows down.

## SVG recipes

These are for inline SVG on a web page. Keep the official fills in both light and dark themes. They are light colours, so put dark text on them (`#1b1b1b`) in both themes, and draw page-level text and lines from the page's theme tokens.

```svg
<!-- Stream-aligned: horizontal, rounded -->
<rect x="0" y="0" width="240" height="56" rx="12" fill="#FFEDB8" stroke="#FFD966" stroke-width="2"/>
<!-- Enabling: vertical, rounded -->
<rect x="0" y="0" width="56" height="200" rx="12" fill="#DFBDCF" stroke="#C27BA0" stroke-width="2"/>
<!-- Complicated subsystem: octagon (w=h=60, corner cut 15) -->
<path d="M15,0 H45 L60,15 V45 L45,60 H15 L0,45 V15 Z" fill="#FBDBBA" stroke="#F6B26B" stroke-width="2"/>
<!-- Platform team: square corners -->
<rect x="0" y="0" width="240" height="56" fill="#B7CDF1" stroke="#6D9EEB" stroke-width="2"/>
<!-- Platform grouping: dotted, square, around the platform teams -->
<rect x="0" y="0" width="520" height="96" fill="none" stroke="currentColor" stroke-width="2" stroke-dasharray="2 4"/>
<!-- Undefined team: rounded, dotted -->
<rect x="0" y="0" width="240" height="56" rx="12" fill="none" stroke="currentColor" stroke-width="2" stroke-dasharray="2 4"/>
<!-- X-as-a-Service: triangle pointing at the consumer (here: up) -->
<path d="M20,0 L40,34 H0 Z" fill="#B4B4B4" fill-opacity="0.5" stroke="#999696" stroke-width="2" stroke-dasharray="5 3"/>
<!-- Collaboration: parallelogram -->
<path d="M12,0 H60 L48,30 H0 Z" fill="#E3E0EE" fill-opacity="0.5" stroke="#967EE2" stroke-width="2" stroke-dasharray="5 3"/>
<!-- Facilitating: circle -->
<circle cx="18" cy="18" r="16" fill="#E3EFDE" fill-opacity="0.5" stroke="#78996B" stroke-width="2" stroke-dasharray="5 3"/>
<!-- Handover: diamond -->
<path d="M14,0 L28,14 L14,28 L0,14 Z" fill="none" stroke="currentColor" stroke-width="2" stroke-dasharray="5 3"/>
<!-- Undefined interaction: square rectangle, dashed -->
<rect x="0" y="0" width="40" height="24" fill="none" stroke="currentColor" stroke-width="2" stroke-dasharray="5 3"/>
<!-- Temporal coupling: trapezoid, dashed -->
<path d="M8,0 H40 L48,24 H0 Z" fill="none" stroke="currentColor" stroke-width="2" stroke-dasharray="5 3"/>
```

Place an interaction shape so it overlaps the edge between the two teams it connects, not in free space with a line. The legend lists each shape that is used, drawn at its real size.
