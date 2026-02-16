# FAQ

## Which OpenSCAD version should I use?

Use a current stable OpenSCAD release (2021.01+ recommended).

## I only want numeric entry fields in Customizer. Are sliders required?

No. This project intentionally avoids numeric slider range annotations in the primary parameter block so typed values and step arrows are the main input method.

## Why do my lid and box not fit well?

Tune `Lid_Lip_Gap` in `0.05 mm` increments and print a short calibration pair. Printer, material, and cooling profile all affect final fit.

## What is a good starting value for `Lid_Lip_Gap`?

Start at `0.10` for PLA and increase as needed. PETG and ABS often need slightly larger values.

## Why are my side openings not where I expect?

Global offsets (`All_Openings_Right`, `All_Openings_Up`) combine with each side-local move parameter. Reset one layer of offsets to zero and re-apply intentionally.

## Which way is positive for side-local opening move values?

- `Move_Opening_Front_to_Right`: positive moves right (`+X`)
- `Move_Opening_Back_to_Right`: positive moves left (`-X`)
- `Move_Opening_Right_to_Right`: positive moves toward back (`+Y`)
- `Move_Opening_Left_to_Right`: positive moves toward front (`-Y`)

## Why are my side override sizes not applied?

Side override width/height values apply only when greater than `0`. A value of `0` means "use global opening size".

## Why do I get an assertion failure about opening height and width?

`All_Opening_Height` and `All_Opening_Width` must both be greater than `0`.
Either dimension can be larger (vertical, horizontal, or square opening profiles are allowed).

## Why are bottom openings colliding with the center post?

Enable both `Enable_Post=true` and `Bottom_Opening_Avoid_Post=true` so the model splits openings around the center clearance region.

## What do `Bottom_Opening_Axis` and `Bottom_Opening_Orientation` each control?

- `Bottom_Opening_Axis`: where openings are arranged as a sequence.
- `Bottom_Opening_Orientation`: rotation of each individual opening shape.

## What does bottom-opening secondary `Custom` alignment do?

Secondary `Custom` centers the opening line inside the custom margin window on the perpendicular axis (left/right window for `Along Y`, front/back window for `Along X`).

## Why does `Bottom_Opening_Spacing=0` look different from a fixed number?

`0` enables auto spacing derived from alignment mode and available room. Any positive number forces explicit spacing.

## My stabilizers overlap side openings. How do I prevent that?

Use the relevant avoid toggles:

- `Stabilizer_Avoid_Front_Opening`
- `Stabilizer_Avoid_Back_Opening`
- `Stabilizer_Avoid_Left_Opening`
- `Stabilizer_Avoid_Right_Opening`

Then adjust stabilizer counts/margins.

## What does stabilizer `Custom` alignment do now?

`Custom` uses custom margins as bounds and attempts fixed-pitch placement (`3 * Stabilizer_Width`) from the start margin. If that pattern does not fit, it falls back to distributed placement inside the same bounds.

## What does `Closed_Post` do?

It changes post inner cut depth so the post base is effectively closed instead of open through the floor-side interior.

## When should I use slicing mode?

Use slicing when full-size parts exceed your printer bed limits or when you want smaller printable modules that snap together.

## How do I export slices correctly?

1. Set `Enable_Slicing=true`.
2. Set `Slice_Count`.
3. Set `Slice_Piece_To_Render` to `1..Slice_Count`.
4. Export each index as an STL.

Use `Slice_Piece_To_Render=0` only for multi-part preview.

## Why did I get an assertion failure for slice/clip parameters?

The model enforces:

- `Slice_Piece_To_Render` is an integer in `0..Slice_Count`
- `Slice_Count >= 2` when slicing is enabled
- `Clips_Per_Edge >= 1` when slicing is enabled
- `Clip_Tolerance >= 0`
- Clip tab width/depth/height all `> 0`

## How do I run automated OpenSCAD smoke checks?

- GitHub Actions: `.github/workflows/scad-smoke.yml`
- Windows local: `scripts/scad-smoke.ps1`
- Linux/macOS local: `bash scripts/scad-smoke.sh`
- Bash fallback: set `OPENSCAD_BIN` if `openscad` is not on PATH.

The smoke set includes an expected-fail assertion case to guard invalid slicing input.

## Slice clips are too tight. What should I change first?

Increase `Clip_Tolerance` by `0.05` and test one seam before reprinting all pieces.

## Slice clips are too loose. What should I change first?

Decrease `Clip_Tolerance` in small steps and retest. You can also increase `Clip_Tab_Width` or clip count for more retention.

## Can I disable the center post entirely?

Yes. Set `Enable_Post=false`.

## Where should reusable preset builds and assets go?

Use `library/` for curated presets and associated images/STLs.

## Where should community-created variants go?

Use `community/` for user-contributed builds, remixes, and showcase assets.

## What license applies to this repository?

`CC BY-NC-SA 4.0` for project content, with third-party portions retaining their original licenses (see `THIRD_PARTY_NOTICES.md`).
