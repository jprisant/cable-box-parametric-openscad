# Validation Rules

This page documents every model assertion in `cable-management-box-parametric.scad`, what triggers it, and how to resolve it.

## Current Assertions

## Override dimensions must be non-negative

```scad
assert(Override_Opening_Height_Front >= 0 && Override_Opening_Width_Front >= 0 &&
       Override_Opening_Height_Back >= 0  && Override_Opening_Width_Back >= 0  &&
       Override_Opening_Height_Left >= 0  && Override_Opening_Width_Left >= 0  &&
       Override_Opening_Height_Right >= 0 && Override_Opening_Width_Right >= 0,
       "Height and width overrides must be positive or zero");
```

Why:

- Override values use `0` as sentinel for "use global default".
- Negative dimensions are invalid geometry inputs.

Fix:

- Keep overrides at `0` or any positive number.

## Global opening width/height must be positive

```scad
assert(All_Opening_Height > 0 && All_Opening_Width > 0,
       "All_Opening_Height and All_Opening_Width must be > 0");
```

Why:

- Side openings must have non-zero physical dimensions.
- Width can be greater than height (horizontal slot), and vice versa.

Fix:

- Set both values above `0`.

## Slice index must be valid integer

```scad
assert(is_int(Slice_Piece_To_Render) &&
       Slice_Piece_To_Render >= 0 &&
       Slice_Piece_To_Render <= Slice_Count,
       "Slice piece to render must be an integer in range 0..slice count");
```

Why:

- `0` is reserved for all-slices preview.
- `1..Slice_Count` maps to specific slice outputs.

Fix:

- Use `0` or an integer from `1` to `Slice_Count`.

## Slice count must be at least 2 when slicing

```scad
assert(!Enable_Slicing || Slice_Count >= 2,
       "Slice count must be >= 2 when slicing is enabled");
```

Why:

- Slice mode with fewer than two slices is undefined.

Fix:

- Set `Slice_Count >= 2` when `Enable_Slicing=true`.

## Clips per edge must be at least 1 when slicing

```scad
assert(!Enable_Slicing || Clips_Per_Edge >= 1,
       "Clips per edge must be >= 1");
```

Why:

- Seam connector layout assumes at least one clip position.

Fix:

- Keep `Clips_Per_Edge` at `1` or higher.

## Clip tolerance must be non-negative

```scad
assert(Clip_Tolerance >= 0, "Clip tolerance must be >= 0");
```

Why:

- Negative tolerance would invert male/female clearance semantics.

Fix:

- Use `0` or a positive tolerance.

## Clip dimensions must be positive

```scad
assert(Clip_Tab_Width > 0 && Clip_Tab_Depth > 0 && Clip_Tab_Height > 0,
       "Clip tab dimensions must be > 0");
```

Why:

- Zero or negative clip geometry yields invalid seam bodies.

Fix:

- Set all clip dimensions above `0`.

## Common Assertion Scenarios

## "Slice piece to render must be an integer in range 0..slice count"

Typical cause:

- `Slice_Piece_To_Render` is larger than `Slice_Count`.

Resolution:

- Increase `Slice_Count` or reduce selected slice index.

## "All_Opening_Height and All_Opening_Width must be > 0"

Typical cause:

- One of the global opening dimensions is set to `0`.

Resolution:

- Set both to positive values, e.g. `20 x 40` for a horizontal slot.

## "Clip tab dimensions must be > 0"

Typical cause:

- One of `Clip_Tab_Width`, `Clip_Tab_Depth`, or `Clip_Tab_Height` set to `0`.

Resolution:

- Restore positive dimensions; start with defaults.

## Authoring Guidance for New Assertions

When adding new constraints:

1. Keep the condition narrow and user-actionable.
2. Make the message explicit and include expected range.
3. Document it here and in `FAQ.md` if users are likely to hit it.
4. Add/update smoke scenarios if it protects a common failure mode.
