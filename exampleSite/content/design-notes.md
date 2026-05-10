---
title: Design Notes
weight: 40
---

This page demonstrates **Hextra shortcodes** available in any content page — useful for assembly guides, design notes, and project documentation.

## Callouts

{{% callout type="warning" %}}
**v0.3.0 errata:** Pin header J3 footprint is mirrored. Apply bodge wire between pins 8–9 or use the corrected v0.3.1 board files.
{{% /callout %}}

{{% callout type="info" %}}
All KiCad source files are available in the [GitHub repository](https://github.com/laenzlinger/hugo-kicad-site/tree/main/example).
{{% /callout %}}

{{% callout %}}
The Arduino Uno Shield template is included with KiCad and makes a good starting point for custom shields.
{{% /callout %}}

## Assembly Steps

{{% steps %}}

### Order PCBs

Upload Gerber files to your preferred fabricator. Recommended: 1.6mm FR4, HASL finish, green solder mask.

### Solder SMD components

Start with the smallest components (0402 passives), then ICs. Use solder paste and hot air or reflow oven.

### Solder through-hole connectors

Install pin headers last — they're tallest and would block access to SMD pads.

### Test

Power up with current-limited supply. Check 3.3V and 5V rails before connecting to Arduino.

{{% /steps %}}

## Tabs (Variant Comparison)

{{< tabs items="2-layer,4-layer" >}}
{{< tab >}}
**2-layer stackup** — suitable for simple shields with low-speed signals.

| Layer | Usage |
|-------|-------|
| Top | Signal + components |
| Bottom | Ground plane |

Cost: ~$5 for 5 boards (JLCPCB)
{{< /tab >}}
{{< tab >}}
**4-layer stackup** — recommended for high-speed or mixed-signal designs.

| Layer | Usage |
|-------|-------|
| Top | Signal + components |
| Inner 1 | Ground plane |
| Inner 2 | Power plane |
| Bottom | Signal + components |

Cost: ~$15 for 5 boards (JLCPCB)
{{< /tab >}}
{{< /tabs >}}

## Details (Collapsible)

{{% details title="BOM sourcing notes" %}}
- C1–C4: Use X7R or X5R dielectric, avoid Y5V for decoupling
- U1: Check LCSC stock before ordering — often backordered
- J1–J3: Generic 2.54mm pin headers, any supplier
{{% /details %}}

## Connector Placement

The Arduino Uno shield template places all pin headers along the board edges to match the standard Arduino form factor:

| Connector | Pins | Function |
|-----------|------|----------|
| J1 | 1×8 | Digital I/O 0–7 |
| J2 | 1×6 | Analog inputs A0–A5 |
| J3 | 1×10 | Digital I/O 8–13 + GND/AREF |

## Mounting Holes

Four M3.2 mounting holes match the Arduino Uno board-to-board spacing. Use 11mm standoffs for proper clearance.
