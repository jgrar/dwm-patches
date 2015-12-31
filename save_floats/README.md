# Savefloats

## Original

http://dwm.suckless.org/patches/save_floats

## Applies to

http://git.suckless.org/dwm/commit/?id=3465bed290abc62cb2e69a8096084ba6b8eb4956

## Changes

The original version of this patch only saves float geometry on
togglefloating() (default MOD+shift+space). I've added float geometry
saving to all layout changes (occurring through setlayout()) because I
feel like that is the expected behaviour.

## Bugs

Opening a window in floating layout and then switching to another
workspace, changing layout, switching back to the original workspace
(the one with the window you just made) and back again and then
changing back to floating layout leaves an artefact of the new window
in the new workspace.

