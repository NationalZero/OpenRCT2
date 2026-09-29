# Demo assets

Files for demonstrating work on branches of this fork. Nothing here is part of an OpenRCT2 pull request.

## Cyclopath entertainer

**[Download `spartan.peep_animations.entertainer_cyclopath.parkobj`](https://github.com/NationalZero/OpenRCT2/raw/demo-assets/spartan.peep_animations.entertainer_cyclopath.parkobj)**

An entertainer costume that demonstrates vehicle-style turning. Its animation group sets `"vehicleTurning": true`,
and its animations provide 32-rotation sprites through `"vehicleOffset"` alongside the usual 4-rotation `"offset"`.

### Install

1. Download the `.parkobj` file.
2. Copy it into the `object` folder of your OpenRCT2 user directory:
   - Windows: `Documents\OpenRCT2\object`
   - macOS: `~/Library/Application Support/OpenRCT2/object`
   - Linux: `~/.config/OpenRCT2/object`
3. Start OpenRCT2 built from the branch with vehicle-style entertainer support.
4. Add the object to your park: open **Object Selection** (from the Cheats menu in the top toolbar, or in the
   Scenario Editor), go to the **Peep Animations** tab and tick **Cyclopath**.
5. Hire an entertainer (or open an existing one) and pick **Cyclopath** as the costume.

Builds without the feature ignore the extra keys and use the 4-rotation sprites with normal walking.
