# picoloader solderless flex — in production

![PicoLoader solderless flex, top view](Flex.png)

The 30-pin flex that connects the main board to the console. It taps the DVD-drive flex
connector with `DVDCN_FLEX_PADS`, so the install needs no soldering.

* 98.46 × 61.01 mm, 2 footprints
* `Library:DVDCN_FLEX_PADS` on the DVD-drive side, `Library:Hirose_FH12-30S-0.5SH_1x30-1MP_P0.50mm_pad`
  for the FFC to the main board
* `GamecubeConnectors.kicad_sym` and both project footprints ship with the project, so the
  schematic opens without missing-library warnings

The flex is shared by every board revision; the silkscreen still reads `Rev1.1` because the
outline has not changed since. See [`../3d-print/`](../3d-print) for the `Fold_KeyV1.2.stl`
part that creases the cable at the right position.

Open `Flex.kicad_pro` with KiCad 10 or newer.
