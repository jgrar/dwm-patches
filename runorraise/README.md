# Runorraise

## Original

http://dwm.suckless.org/patches/runorraise

## Applies to

http://git.suckless.org/dwm/commit/?id=3465bed290abc62cb2e69a8096084ba6b8eb4956

## Changes

The original patch enforced a 5 element limit on the runorraise
argument, using the last element for the class name. So you would
really only get 3 elements to use (i.e. 5 elements minus the class
name and terminating NULL field) and if you didn't use them you would
waste space padding the array with NULLs. This change removes that
restriction and adds window name hint matching, which is likely the
hint you actually want to use to match windows seeing as the class
hint encapsulates multiple window types and as far as I know there's
no way for a user to set it.

 * reduce amount of changes to main source to ease patch application
 * add window name matching
 * improve window class matching and add window name matching

## Usage:

Just like window rules; use xprop(1) to get the "name, class"
pair.

config.h:
```c
// ...
#include "runorraise.c"

static const char *rorcmd[] = {"urxvtc", "-name", "ror", NULL};

// ... static Key keys[] = {
    { MODKEY|ShiftMask,	XK_a,	runorraise,	{.v = &(RoR)(.name = "ror", .spawn = (char **)rorcmd} },
```
