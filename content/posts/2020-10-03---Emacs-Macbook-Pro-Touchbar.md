---
title: How I use the Macbook Pro touchbar with emacs
date: "2020-10-03"
template: "post"
draft: false
slug: "emacs-macbook-pro-touchbar"
category: "Tech"
tags:
  - "emacs"
  - "tech"
  - "apple"
  - "touchbar"
  - "macbook pro"
description: "Using the Macbook Pro touchbar to launch my agenda, ledger file and email client in emacs."
socialImage: "/media/emacs.png"
---

![Macbook pro touchbar](/media/touchbar.png)

## BetterTouchTool

I love my 15in Macbook Pro but I haven't found many uses for the touchbar until I started using [BetterTouchTool](https://folivora.ai "BetterTouchTool"). It's a piece of software that allows you control certain aspects of your Mac. One of the features is that it will allow you to modify the Macbook Pro touchbar. The specific feature I use to control Doom Emacs is the ability to create buttons on my touchbar. 

I've created 5 buttons that merely mimic pressing on the function keys and they only appear in my touchbar when I have emacs focused on my mac. 

This is how it's setup in [BetterTouchTool](https://folivora.ai "BetterTouchTool"):

![BetterTouchTool](/media/bettertouch.png)

## Org Capture

The first button is for capturing tasks with [org-capture](https://orgmode.org/manual/Capture.html), I have this mapped to `<f4>`. Here's what my capture buffer looks like:

![Org Capture](/media/capture.png)

## Org Agenda

The second button is to launch my [Org Agenda](https://orgmode.org/manual/Agenda-Views.html#Agenda-Views), I have this mapped to `<f1>`. I configured emacs like this to launch my agenda when `<f1>` is pressed:

```
(defun ny/switch-to-agenda ()
    (interactive)
    (org-agenda nil " ") ;; This is setup with a capture key because I set it up this way.
    (org-agenda-goto-today))
    
(map! "<f1>" #'ny/switch-to-agenda)
```


## Ledger 

The third button is to launch my current ledger file. I use [Ledger](https://www.ledger-cli.org) to manage my finances and emacs has a great package that allows me to work with this system easily. I have that mapped to `<f2>`

Here is the emacs lisp code to launch it:
```
(map! "<f2>" #'ny/switch-to-ledger)
(defun ny/switch-to-ledger ()
  (interactive)
  (find-file "~/Dropbox/finance/2020.ledger"))
```

## Mu4e (email)

The fourth button is to launch my email client which is obviously baked into emacs becuase why wouldn't it be. I use [mu4e](https://www.djcbsoftware.nl/code/mu/mu4e.html) for this and I love it because it's not only a great email client but it allows me to link emails to `todos` with `org-capture`.

Here's what the code looks like:

```
(map! "<f3>" #'ny/switch-to-mail)
  (defun ny/switch-to-mail ()
    (interactive)
    (mu4e))
```

## Elfeed

The last and final button is for my news client which again, is in emacs. I use [elfeed](https://github.com/skeeto/elfeed) for this. 

Here is the emacs code, which is just like the other snippets:

```
(map! "<f5>" #'elfeed)
```


## Conclusion

As you can see, the Macbook pro touchbar makes it quite easy to make getting to the emacs programs I use quite frequently very quickly. I really love this approach and I'm looking forward to seeing what else I can use the touchbar for, especially with emacs.
