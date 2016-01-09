# Statuscolors

## Original

http://dwm.suckless.org/patches/statuscolors

## Applies to 

http://git.suckless.org/dwm/commit/?id=3465bed290abc62cb2e69a8096084ba6b8eb4956

## Changes

This fix removes the gaps/spaces in the dwm status bar that are
introduced on color scheme change. This is particularly an issue if
you're using something like mkb with arguments that alter the scheme:

```sh
... START="\x03" SEP="\x02" ... mkb
```

Which will result in something like:

![gaps-issue-before](https://cloud.githubusercontent.com/assets/466092/12215859/51731a8c-b719-11e5-9de9-c3759fa8d3d1.png)

The color scheme change at the seperator breaks the progress meter.
This is because drw_colored_text() is drawing a new box for every
group of colored text. The solution is to embed colorscheme changing
into the text drawing function, only creating one box around all the
text. Here is the above fixed:

![gaps-issue-after](https://cloud.githubusercontent.com/assets/466092/12215858/5170e0d2-b719-11e5-96a2-deabbd696171.png)

