---
layout: post
title:  "Customizing the GHCi prompt "
date:   2017-07-24 00:06:32 +0530
feature: http://i.imgur.com/Ds6S7lJ.png
comments: true
---

I'm going to show you how to make your GHCi prompt the Haskell logo.

## Steps:

- Firstly, install and select one of the many [nerd fonts](https://github.com/ryanoasis/nerd-fonts) as your terminal font.
- Now, edit your `ghci.conf` or `.ghci` file accordingly:
```
:set prompt "\ESC[94m\STX\ue61f  \ESC[m\STX"
```

And start up GHCi again... and there you go. Haskell logo as the prompt.
<figure>
<a href="http://i.imgur.com/WtkjfAp.png"><img src="http://i.imgur.com/WtkjfAp.png"></a>
</figure>
