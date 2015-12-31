# Runorraise

## Original

http://dwm.suckless.org/patches/runorraise

## Changes

    * reduce amount of changes to main source to ease patch application
    * add window name matching
    * improve window class matching and add window name matching

## Usage:

The original patch enforced a 5 element limit on the runorraise
argument, using the last element for the class name. So you would
really only get 3 elements to use (i.e. 5 elements minus the class
name and terminating NULL field) and if you didn't use them you would
waste space padding the array with NULLs. This change removes that
restriction and adds window name hint matching, which is likely the
hint you actually want to use to match windows seeing as the class
hint encapsulates multiple window types and as far as I know there's
no way for a user to set it.

config.h:
```c
#include "runorraise.c"
ClassHintedCmd singletontermcmd = {
    /* it's just like window rules! use xprop to get the class,
     * instance (name) hints
     * you can omit either, but not both.
     */
    .class = "URxvt",
    .name = "singleton",
    .spawncmd = { "urxvtc", "-name", "singleton", NULL }
};
// ... static Key keys[] = {
    { MODKEY|ShiftMask,             XK_a,      runorraise,          {.v = &singletontermcmd} },
```

