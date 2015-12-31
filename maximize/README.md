# Maximise

## Original

http://dwm.suckless.org/patches/maximize

## Applies to

http://git.suckless.org/dwm/commit/?id=3465bed290abc62cb2e69a8096084ba6b8eb4956

## Changes

I was unhappy with scripted solutions for automatic on-window-open
maximization using xdotool (wmctrl wouldn't even work for me),
preferring it to just be provided by the window manager I've added a
window rule which automatically starts a window maximized.

Changes also include:

 - updating the patch to apply to 3465bed290ab

   * Change boolean values to integers

 - removing redundant size saving in maximize() as resizeclient() does
   this already

## Usage

There's not much to it really, just flip the new ismax field of Rules
from 0 to non-zero!

```c
// ... static const Rule rules[] = {
    /* class    instance          title       tags mask     isfloating     ismax         monitor */
    { NULL,     "maximiseme",     NULL,       0,            1,             0,            -1 },
// ...
const char *maximisethiscmd[] = {"urxvtc", "-name", "maximiseme", "-e", "example", NULL};
```

