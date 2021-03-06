+++
title = "Trackpad Drivers for Linux on a Mac"
aliases = ["2015/08/04/mtrack/"]
layout = "blog/single.html"
[taxonomies]
tags = [
  "Arch Linux",
]
+++

If you're like me and have Mac hardware but run Linux you might also run into the slight annoyance with the trackpad drivers X.org defaults to.

If you haven't explored, there is a fantastic replacement called [`mtrack`](https://github.com/BlueDragonX/xf86-input-mtrack) that I've had great luck with.

<!-- more -->

Here's an example of my configuration in `vim /etc/X11/xorg.conf.d/10-mtrack.conf`

```
Section "InputClass"
    MatchIsTouchpad "on"
    Identifier "Touchpads"
    Driver "mtrack"
    Option "Sensitivity" "0.5"
    Option "IgnorePalm" "on"
    Option "IgnoreThumb" "on"
    Option "FingerHigh" "15"
    Option "ClickFinger1" "3"
    Option "ClickFinger2" "2"
    Option "ClickFinger3" "0"
    Option "TapButton1" "1"
    Option "TapButton2" "3"
    Option "TapButton3" "2"
    Option "SwipeDistance" "1400"
    Option "Swipe4Distance" "1400"
    Option "SwipeLeftButton" "9"
    Option "Swipe4LeftButton" "9"
    Option "SwipeRightButton" "8"
    Option "Swipe4RightButton" "8"
    Option "SwipeUpButton" "10"
    Option "Swipe4UpButton" "10"
    Option "SwipeDownButton" "11"
    Option "Swipe4DownButton" "11"
EndSection
```

It works decently! I like how in Firefox I can even use it to go back/forward with a swipe just like on Mac!
