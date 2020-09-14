---
title: Emacs syncing with Dropbox and Beorg for iOS
date: "2020-09-08"
template: "post"
draft: false
slug: "emacs-syncing-dropbox-beorg"
category: "Tech"
tags:
  - "emacs"
  - "tech"
  - "beorg"
description: "Emacs syncing with Dropbox and Beorg for iOS"
socialImage: "/media/emacs.png"
---

Emacs             |  Dropbox | Beorg
:-------------------------:|:-------------------------:|:-------------------------:
![Emacs](/media/emacs.png)  | ![Dropbox](/media/dropbox.png) | ![Beorg](/media/beorg.png)|

I'm an emacs and iOS user. I've basically live in emacs and I love it. Having my life in plain text just give me so much clarity.

I use [Beorg on iOS](https://beorgapp.com) to maintain my agenda and capture tasks for [org-mode](https://orgmode.org) on the go but it turns out, the syncing with Dropbox and emacs (on the desktop) doesn't entirely work "out of the box" unless you have a couple of things in your emacs config. 

Everything works fine with syncing files up to Dropbox when things change but to get emacs on the desktop to update automagically, you'll need the following settings in your emacs config turned on.

[Auto save visited mode](https://www.gnu.org/software/emacs/manual/html_node/emacs/Auto-Save-Control.html) is used to save files in the background when you don't save them explicitly. This is critical when you change an org file on your desktop that you want to sync to [Beorg](https://beorgapp.com).
```
(auto-save-visited-mode t)
```

[Auto revert mode](https://www.gnu.org/software/emacs/manual/html_node/emacs/Reverting.html) is used when you change an org file in [Beorg](https://beorgapp.com) that you want emacs on the desktop to automagically reload in the background. 
```
(auto-revert-mode t)
```

With both of these settings turned on, [Beorg](https://beorgapp.com) on iOS and Dropbox it makes this setup pretty magical. Everything is always up to date and in sync. Just watch your buffers update in real time :)
