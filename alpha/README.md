# Alpha

## Original

http://dwm.suckless.org/patches/alpha

## Applies to

http://git.suckless.org/dwm/commit/?id=bb3bd6fec37174e8d4bb9457ca815c00609e5157

## Changes

  - All color specification comes with an alpha channel.
  - Added RGBA() helper macro.
  - Now uses XftColorAllocValue() instead of XftColorAllocName(). Apparently the latter is
    slow due to a round-trip.

## Usage

Pretty straight forward, configure the colors array in config.h by specifying the
individual RGBA hex values:
```c
static const XRenderColor *colors[][3] = {
	/*               fg                     bg                 border               */
	[SchemeNorm] = { RGBA(bb,bb,bb,OPAQUE), RGBA(22,22,22,d0), RGBA(44,44,44,OPAQUE) },
	[SchemeSel] =  { RGBA(ee,ee,ee,OPAQUE), RGBA(00,55,77,d0), RGBA(00,55,77,OPAQUE) },
```

## Bugs

 - Changing the alpha value doesn't do anything (under compton) even though there
   is tansparency.
