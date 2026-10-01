# OrcaSlicer Process Presets (Bambu Lab P1S)

Custom OrcaSlicer process presets for a Bambu Lab P1S. Each preset is a small
override JSON that inherits from a stock Bambu Studio profile
(`0.16mm Optimal @BBL X1C`) and only changes what matters — speeds, walls,
seams, and infill — so fixes in the stock profiles still flow through.

## Presets

### 0.16mm Quality @P1S

General-purpose profile for visual parts: cases, covers, decorative
models, anything where surface finish matters more than raw strength.

- 120 mm/s outer walls at 3000 mm/s², 150 mm/s top surfaces at 1500 mm/s²
- Arachne wall generator, aligned external sloped seams placed away from
  overhangs
- Single top wall over 5 top shell layers for clean surfaces
- 10% gyroid sparse infill — light, prints fast, adequate for parts that
  aren't under load

### 0.16mm Quality Mechanical @P1S

Inherits everything from the Quality preset and toughens it for functional
parts that sit under sustained load: Skadis/pegboard mounts, brackets,
clamps, handles.

- 30% gyroid sparse infill
- 4 wall loops — perimeters add more stiffness than infill does, so both
  were raised

## When to use which

| Part type | Preset |
| --- | --- |
| Decorative models, cases, anything appearance-first | 0.16mm Quality @P1S |
| Skadis hooks, wall mounts, brackets, clamps | 0.16mm Quality Mechanical @P1S |
| Under sustained load **and** near heat or carrying real weight | Mechanical preset **plus PETG or ABS/ASA** |

The last row matters: PLA creeps under constant stress and will sag over
months. For anything hanging weight permanently, switch the filament
profile too — the process presets work with either.

## Installing

OrcaSlicer loads user presets from its user folder. On this machine that is:

```
~/Library/Application Support/OrcaSlicer/user/default/process/
```

Copy both JSON files there (the Mechanical preset must sit alongside the
Quality preset since it inherits from it) and restart OrcaSlicer. Or just
import each file via Process → edit dropdown → the import button.
