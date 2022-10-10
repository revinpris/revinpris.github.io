---
layout: post
title: "Font rendering exactly like macOS on Linux"
date: 2017-08-08 00:12:14 +0530
feature: https://ucarecdn.com/3a5af0a1-89a0-4f24-a0b5-c44eabc77963/
comments: true
---
(Note from 2020: Infinality has been deprecated for a while now. Follow the tutorial at your own risk.)


Today I'm going to show you how to make your fonts look almost *exactly* like macOS on Linux.

## Background

I've been obsessing over how Macs render fonts, especially Fira Mono, for months. I was so obsessed that I quit programming and reading to go on a quest to one day, render Fira Mono the way Macs do.

Yesterday I did it. And I want to share how I did it to save some of you the *pain* that I have endured for this.

This tutorial will be aimed at Arch Linux users specifically, though the instructions can be applied to any distribution of (GNU/)Linux.


## Steps (for Arch Linux):

1. Get freetype2 with infinality patches. For Arch Linux, the package is `freetype2-infinality`<sup>[AUR](https://aur.archlinux.org/packages/freetype2-infinality/)</sup>. You don't need fontconfig with infinality patches.
2. Put this in your `infinality-settings.sh`. For Arch Linux, this file is located in `/etc/profile.d/`.
```sh
export INFINALITY_FT_FILTER_PARAMS="03 32 38 32 03"
export INFINALITY_FT_GRAYSCALE_FILTER_STRENGTH=100
export INFINALITY_FT_FRINGE_FILTER_STRENGTH=0
export INFINALITY_FT_AUTOHINT_HORIZONTAL_STEM_DARKEN_STRENGTH=0
export INFINALITY_FT_AUTOHINT_VERTICAL_STEM_DARKEN_STRENGTH=0
export INFINALITY_FT_WINDOWS_STYLE_SHARPENING_STRENGTH=0
export INFINALITY_FT_CHROMEOS_STYLE_SHARPENING_STRENGTH=0
export INFINALITY_FT_STEM_ALIGNMENT_STRENGTH=0
export INFINALITY_FT_STEM_FITTING_STRENGTH=0
export INFINALITY_FT_GAMMA_CORRECTION="1000 99"
export INFINALITY_FT_BRIGHTNESS="-10"
export INFINALITY_FT_CONTRAST="15"
export INFINALITY_FT_USE_VARIOUS_TWEAKS=false
export INFINALITY_FT_AUTOHINT_INCREASE_GLYPH_HEIGHTS=true
export INFINALITY_FT_AUTOHINT_SNAP_STEM_HEIGHT=0
export INFINALITY_FT_STEM_SNAPPING_SLIDING_SCALE=0
export INFINALITY_FT_USE_KNOWN_SETTINGS_ON_SELECTED_FONTS=false
 ```
and either reboot, or restart the X server.
3. (Optional) Install `fontconfig-ubuntu`<sup>[AUR](https://aur.archlinux.org/packages/fontconfig-ubuntu/)</sup> for an even better, and a rendering even closer to macOS (I know this sounds counter-intuitive, but trust me.)

## Steps (for generic Linux):
1. Follow the steps given [here](https://github.com/bohoomil/fontconfig-ultimate) in the Quick Installation instructions.
2. Same as the one for Arch Linux.
3. If you're on Ubuntu, you don't need to install fontconfig for ubuntu, obviously. But I am unaware of any other ports of ubuntu font config to distributions other than Arch. If you are, please bring it to my notice.


And that should do the trick. If the fonts are a bit too bold for you, you can change `INFINALITY_FT_USE_VARIOUS_TWEAKS` to `true` and that makes them lighter.

If that still doesn't fix it, try [customizing your own configuration from this file](https://github.com/bohoomil/fontconfig-ultimate/blob/master/freetype/generic_settings/infinality-settings.sh).



