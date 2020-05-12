# Handjet

By: David Březina <david@mrbrezina.com>
Released in: May 2020

## Scripts

- Arabic
- Armenian
- Cyrillic
- Greek
- Latin

## Source files

In principle all glyphs remain the same across all masters except for two special glyphs: `shape` and `grid` which control the element changes in Handjet.

There are three source files.

`Handjet-Shapes.glyphs` contains individual layers for the `shape` and `grid` glyphs. Glyphs named `SHAP-XXXX` become layers in the `shape` glyph on the `SHAP` axis. Glyphs named `wght-XXX` specify tranformation (scale) applied to the shape glyph (their content is not copied, only the transformation is copied). Glyphs named `opsz-XXX` specify the layers in `grid` glyph along the `opsz` axis. All of these layer-glyphs are combined together using a macro `compile shape glyph.py`.

`Handjet-Characters.glyphs` contains all characters in a single layer. Note that `shape` and `grid` glyphs are also in one layer. Warning: the grid spacing in font info is set to 120!

`Handjet-Uprights.glyphs` is the source used for production, it contains all characters in all required masters (27 masters specified in the font info). Note that `shape` and `grid` have many brace layers to avoid the need for many more masters in the font info. Warning: the grid spacing in font info is set to 1! This is important, otherwise the contours in the `shape` glyph may be crippled.

To populate the `Handjet-Uprights.glyphs` one needs to:

1. Copy all glyphs from `Handjet-Characters.glyphs` and replicate the single master to all masters using the `replicate in all layers.py` macro.
2. Copy all glyphs from `Handjet-Shapes.glyphs` and compile the `shape` and `grid` glyphs anew using the `compile shape glyph.py` macro.
3. Make sure you preserve all font info settings during this process.

The masters and instances in the `Handjet-Uprights.glyphs` can be set up using macros too, but this should not be necessary. Warning: there are too many instances in the font info which seems to crash Glyphs app when one opens the relevant tab in the font info.

