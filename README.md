# Demo assets

Files for demonstrating work on branches of this fork. Nothing here is part of an OpenRCT2 pull request.

## Cyclopath entertainer

**[Download `spartan.peep_animations.entertainer_cyclopath.parkobj`](https://github.com/NationalZero/OpenRCT2/raw/demo-assets/spartan.peep_animations.entertainer_cyclopath.parkobj)**

An entertainer costume that demonstrates smooth turning and 32-direction sprites. (The sprites were adapted from a
ride vehicle as a quick demo; the features aren't specific to vehicle-like costumes.)

It works in any OpenRCT2 build. Builds with smooth turning support use the extra features; other builds show it
as a normal entertainer with 4-direction sprites.

### Install

1. Download the `.parkobj` file.
2. Copy it into the `object` folder of your OpenRCT2 user directory:
   - Windows: `Documents\OpenRCT2\object`
   - macOS: `~/Library/Application Support/OpenRCT2/object`
   - Linux: `~/.config/OpenRCT2/object`
3. Start OpenRCT2. To see the turning and 32-direction sprites, use a build from the branch with smooth turning
   support.
4. Add the object to your park: open **Object Selection** (from the Cheats menu in the top toolbar, or in the
   Scenario Editor), go to the **Peep Animations** tab and tick **Cyclopath**.
5. Hire an entertainer (or open an existing one) and pick **Cyclopath** as the costume.

## Optional object keys

All of these are optional additions to a `peep_animations` object. Every animation still needs its usual
4-rotation images at `"offset"`, and those are what builds without these features use.

| Key | Where | What it does | Cyclopath |
| --- | --- | --- | --- |
| `"smoothTurning": true` | Animation group | Peeps round corners on a curve and turn around gradually instead of snapping to a new direction. | Yes |
| `"offset32"` | Animation | Image offset of a 32-rotation set: image = offset32 + rotation + frame × 32. Used instead of `"offset"` for drawing. | Yes |
| `"uphillOffset"` | Animation | Image offset of a 4-rotation set, laid out like `"offset"`, used while walking up a sloped path. | Not yet |

Each extra set uses the same `"sequence"` as its animation. Leave a key out and the normal images are used, so you
can add these to one animation at a time.

Example animation with all three image sets:

```json
"walking": {
    "offset": 1,
    "offset32": 134,
    "uphillOffset": 1190,
    "sequence": [0]
}
```

### Backward compatibility

- **Older builds** ignore keys they don't know. The extra images still load with the object but are never drawn,
  so the costume looks and walks like a normal entertainer.
- **Newer builds** only use a set when its key is present. Costumes without them, built-in or custom, are
  unchanged.
- **Saved parks** gain no new data. Uphill images are picked from slope information peeps already store, and a
  peep saved mid-turn is drawn facing one of the 4 directions in an older build, and walks on normally.

To add uphill images to an existing object, append them to the end of the object's image list and point
`"uphillOffset"` at the first one. Existing offsets don't change, so the object keeps working everywhere.
