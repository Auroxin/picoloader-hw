# Notice

This repository is a derivative of the **PicoLoader** project by **makeo**:

> PicoLoader — <https://github.com/makeo/PicoLoader>
> Licensed under the GNU General Public License v2.0 (GPL-2.0).

The flex PCB design and the printed mounts in the upstream project were originally made by
**silversteel**. The whole repository is distributed under GPL-2.0; see [`LICENSE`](LICENSE).

## Files taken unchanged from upstream

These files are byte-identical to their upstream counterpart and are redistributed under
GPL-2.0:

| File in this repository | Upstream path |
| --- | --- |
| `3d-print/Drive_PlugV1.1.stl` | `mount/Drive_PlugV1.1.stl` |
| `3d-print/Fold_KeyV1.2.stl` | `mount/Fold_KeyV1.2.stl` |
| `hw/flex/GamecubeConnectors.kicad_sym` | `flex/InterposerFlex/Kicad/GamecubeConnectors.kicad_sym` |

## Files modified for this repository

Modified in October 2026 while preparing this repository:

| File in this repository | Based on | Change |
| --- | --- | --- |
| `hw/flex/Flex.kicad_pro`, `Flex.kicad_sch`, `Flex.kicad_pcb` | `flex/InterposerFlex/Kicad/` | re-saved with KiCad 10, silkscreen and layout edits, footprint library flattened |
| `hw/flex/Library.pretty/DVDCN_FLEX_PADS.kicad_mod` | `flex/InterposerFlex/Kicad/GamecubeConnectors.pretty/` | pad geometry edited |
| `hw/v1.1/`, `hw/v1.1A/`, `hw/v1.2A/` | board revisions | published here, see each folder's `README.md` |
| `hw/v1.1A/pcb-render-v1.1A-top.png`, `hw/v1.2A/pcb-render-v1.2A-top.png`, `hw/flex/Flex.png`, `extras/` | — | renders and product graphics made for this repository |

## Copyright

* PicoLoader concept, firmware, original flex PCB and mounts: makeo and upstream contributors.
* Board revisions v1.1, v1.1A, v1.2A, the renders and the edits listed above: Auroxin.

Keep this notice and the GPL-2.0 licence with any redistributed copy of these files.
