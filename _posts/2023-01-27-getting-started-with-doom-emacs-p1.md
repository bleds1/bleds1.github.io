---
layout: post
title: "A Beginners Guide: Getting Started with Doom Emacs"
date: 2023-01-27 14:00:00
categories: emacs
---
## Introduction

![Image 1](/assets/images/dashboard-doom-emacs-pigmentandpixels-1.png){:height="400px" width="600px"}{:style="display:block; margin-left:auto; margin-right:auto"}


If your first thought on this is *“Urrggh, no not Emacs. Not for me..It's ancient, bloated, complicated, full of features I don't need..just give me a simple plain text editor“*. Well that was me too. I was very much a Vim user because I'm a bit of minimilist, enjoy terminal based applications and like a lean setup. Actually - I still Vim all the time, especially for quick edits. This tribal mentality that you must be on one team or the other seems massively dumb to me. So what turned me the way of Emacs? The short answer is Org-mode but I think that's going to have to wait for another post..

So, I'm not a coder or programmer and all I know about Elisp is it's got a lot of bloody semicolons. I hack on a few Linux config files but I'm coming at Emacs from the perspective of a note taker. I mostly use Emacs for writing, reading, digital notetaking and task organization.

Because Emacs is such a huge topic I'll probably just give an *‘as brief as I can overview’** of some of the reasons and features I use in it. There’s a lot of info out there if it peeks your interest. This first post will be a total beginners guide and link to some resources at the end if you want to go further down the rabbit hole. I'll talk more about the juicy specifics in future posts. I'm going to make the presumption that you, dear reader know a few things already. Like what Vim and the terminal is and what Emacs is. There is an internet if you need to get up to speed.

It started for me with Vim motions. I use Vim motions everywhere possible, any editor or browser must have them for me. If I hadn't learnt Vim motions prior, I probably wouldn't have got into Emacs at all. Doom Emacs uses the evil key bindings from Vim. I tried installing vanilla Emacs and was totally lost, it felt like an alien world. Doom makes a lot of sense to me because it's Vimcentric. Doom is essentially a framework with a ton of configuration on top of base Emacs. They have done so much work and optimization for you it's actually quite simple to get started with.

Another app on my road to Emacs that I previously thought was 'the one' is Obsidian. I still think it’s super great actually and could easily go back to it one day. I'm very much into the idea of keeping all your files and projects in plain text or markdown, offline, without using some kind of paid syncing or subscription service. With Emacs you are in control of your files, it's free software and your life in text feels safe and future proof. Obsidian has a lot of cool features for linking ideas together in your vault. I also liked that you can just edit the notes with any other text editor that can handle the markdown format. I would use Vim a lot to take my quick notes and Obsidian would be the master vault where I organize them into some kind of a system. Through learning Obsidian I learnt about the Zettlekasten method, PKM and 'Building a Second Brain'. This in turn led to learning that Emacs can do all this stuff and much, much more..


## How to install Doom Emacs

Be sure to have Vanilla Emacs installed first and then git clone Doom Emacs;


**git clone --depth 1 https://github.com/doomemacs/doomemacs ~/.emacs.d ~/.emacs.d/bin/doom install**


You may want to set up an alias, keyboard shortcut or startup script for launching Emacs with the emacsclient. It's the best and fastest way to use Emacs trust me..

Start the daemon for the emacsclient from your terminal with;


**/usr/bin/emacs --daemon &**


Run the Emacs client;


**emacsclient -c -a 'emacs'**


If you’re not on Linux you can find alternate install and setup instructions for Mac & Windows [here](https://github.com/doomemacs/doomemacs/blob/master/docs/getting_started.org).


## Basic configuration

![Image 2](/assets/images/terminal-dir-doom-emacs-pigmentandpixels-2.png){:height="400px" width="600px"}{:style="display:block; margin-left:auto; margin-right:auto"}

### config.el

Most of your configuration will be taking place in **~/.doom.d/config.el** You can run **‘doom sync’** after any changes for them to take effect with **(Space-h-r-r)**. That's a keybind you'll use a lot. I remember it as *"Hey, Reload, Reload!"*. You don't need to exit Doom when you make changes to this file but you will if you add any new packages. If you’ve added new packages to Doom you'll want to exit and kill the daemon and run **‘doom sync’** at the terminal.

### init.el


![Image 3](/assets/images/init-doom-emacs-pigmentandpixels-3.png){:height="700px" width="400px"}{:style="display:block; margin-left:auto; margin-right:auto"}

This file lists a bunch of modules/packages that are Doom ready just comment out those ;; things with **x** to delete the character. Restart, sync as mentioned above.

[codeblock]

Those are the most important ones for emulating my set up that I have activated. You may want to activate programming languages you often use for nice coloured syntax here.


### package.el

![Image 4](/assets/images/packages-doom-emacs-pigmentandpixels-4.png){:height="400px" width="500px"}{:style="display:block; margin-left:auto; margin-right:auto"}

Any other packages are installed in packages.el. You add a package with (package! example) then exit Doom and run ‘doom sync’ in the terminal.

Here's some packages I enable;

**Beacon** [link]()

**(beacon! focus)**

- This makes a cool little graphical pulse to show what line number you are on when you switch file or window.

**Focus** [link]()

**(package! focus)**

[image]

- **M-x focus-mode** - greys out text in a file apart from the few lines you are editing. [Obsidian]() and [limelight.vim]() do something similar. I will be refering to the key **META** from here as **M** which is also known as **ALT**. You can think of it as a leader key, **Space** is the other main leader key.

## Set your font

I use [Jet Brains Mono](). Your font of choice needs to be already installed on your system. You can set a larger version or different font to be used in different modes such as writeroom-mode.



**(setq doom-font (font-spec :family "JetBrains Mono" :size 13 :weight 'Medium)
      doom-big-font (font-spec :family "JetBrains Mono" :size 14 :weight 'Medium)
      doom-variable-pitch-font (font-spec :family "JetBrains Mono" :size 14))**
      
      
## Disable Line Numbers

I used to really like relative line numbers in Vim but because I'm doing more prose writing in Doom I disable them. It's very easy to reactivate them if needs be with **Space-t-l** or **M-x toggle-line-numbers**.


**(setq display-line-numbers-type nil)**


## Set a Theme

We’ll be needing a cool theme if we're going to use this thing regularly. I use an inbuilt doom-theme ‘wilmersdorf’. The default background for that is dark blue and I like it even darker than that so I add a few lines to make it a dark, dark grey.

Type **M-x** and then **load-theme**. You will see a list of availible themes in the buffer at the bottom of the screen. If you want to just change the background colour you can type **M-x set-background-color**. These changes won't be permanent until you add the commands to your config.el.


**(setq doom-theme 'doom-wilmersdorf)
(custom-set-faces
'(default ((t (:background "#1a1a1a" :foreground "#a9b1d6")))))**


## Modeline

[image]

You'll want to get that Doom modeline at the bottom of the screen looking sweet too. Here's the tweaks I use as there’s a bit too much going on down there by default for my taste..


**(after! doom-modeline
(remove-hook 'doom-modeline-mode-hook #'size-indication-mode) ; removes filesize from modeline
(remove-hook 'doom-modeline-mode-hook #'column-number-mode)   ; removes cursor column in modeline
(line-number-mode -1)
(setq doom-modeline-buffer-encoding nil))
(setq doom-modeline-enable-word-count t) ; show word count in md & txt
(setq display-time-default-load-average nil) ; remove load average
(setq doom-modeline-height 15) ; shorter bar height
(display-time-mode 1) ; show time and date
(setq display-time-format "%Y-%m-%d %H:%M") ; time and date format**


## Keybinds and basic navigation

Here’s some very basic beginner key binds to get you started. Thankfully Doom has which-key. This makes learning the key binds so much easier. Doom is based around having a leader key followed by a key chord. They are all quite literate for example;


**Space (the leader key) o-a** = Open Org-agenda - open (o)rg (a)genda.

**Space n-j** = (n)ew (j)ournal entry.


There are many more examples of this so when you know what you want to do these chords become memorable.

**Space .** will get you into the file explorer to open any file or directory on your system.

**Space Enter** will access bookmarks. You can set bookmarks with **M-x bookmark-set**.

**M-x** is very powerful. This is the best way to learn because a lot of commands will have a keyboard shortcut shown next to it in the buffer at the bottom of the screen..or you can set one for it in your config. You can go crazy here because the auto completion works really well.. that's how I picked up so much - try for example;

**M-x tetris**

[image]

Every thing you open is a buffer. Even if it's not on screen it's open in the background as a buffer. To navigate buffers you can;

**Space b-n** - think (b)uffer (n)ext

**Space b-p** - think (b)uffer (p)revious

**Space b-k** - b(uffer) (k)ill

or

**Space b-i** to list all your open buffers.


Start writing, editing, Using the Vim keys - **i and esc** to switch from INSERT mode to NORMAL mode. In normal mode you use **h,j,k,l** to navigate around.

**:w** - save

**:wa** - save all open buffers

**:wq** - to save and quit.


## Outro

That's probably enough word count for this first post about Doom Emacs as Substack is telling me it’s too long for an email and I don’t want to overload. This should get you started at least. I'll pick up where we left off in future posts because now we’re past the super basics I’m excited to talk about the killer feature that is **org-mode** and **org-agenda**. I'll try to show you how I set up my GTD task system and the quick capture templates to make note taking and writing a quick and easy process.

It's *quite the vast topic*.. If you've got any questions, I'll try my best to answer.

Whilst you're here did you know pigmentandpixels is also an art blog? I try to do one post art, one post tech to keep my life in balance. Here's the [most recent art post](https://pigmentandpixels.xyz/art/2023/01/17/lost-boys-painting-part-1.html).

[image]

### Resources

Find below resources I found useful and stole a lot of stuff from for my config. If you are ready to give up your soul to Emacs maybe bookmark this for later. Thanks for reading!


[Doom Emacs on Github](https://github.com/doomemacs/doomemacs)

[Emacs For Writing prose : A guide](https://discourse.doomemacs.org/t/emacs-for-writing-prose/515)

[Doom Emacs Discourse](https://discourse.doomemacs.org/c/guides/5)

[Tecosaur's Doom Emacs Config](https://tecosaur.github.io/emacs-config/config.html)

[Distrotube has many useful videos about Doom Emacs for beginners](https://piped.kavin.rocks/channel/UCVls1GmFKf6WlTraIb_IaJg)

[Zzamboni 'My Doom Emacs configuration with commentary'](https://zzamboni.org/post/my-doom-emacs-configuration-with-commentary/)

[Tasshin on Emacs and building a second brain](https://tasshin.com/blog/implementing-a-second-brain-in-emacs-and-org-mode)

[Jethro Kuan - 'How I Take Notes with Org-Roam'](https://jethrokuan.github.io/org-roam-guide/)

[A Comprehensive Org config](http://doc.norang.ca/org-mode.html)

[The Org-mode Manual](https://orgmode.org/org.html)

[Hugo Cisneros' Org config](https://hugocisneros.com/org-config)

[Rainer Koenig's Blog (Org-mode)](https://koenig-haunstetten.de/)

[Rainer Koenig's Videos on Org-mode](https://piped.kavin.rocks/playlist?list=PLVtKhBrRV_ZkPnBtt_TD1Cs9PJlU0IIdE)

_(This post is a slightly re-edited version of one that first appeared on [Substack](https://pigmentandpixels.substack.com/p/a-beginners-guide-getting-started) Until I get comments setup on this blog if you want to leave one it's best to do it there or via the email or socials below_)
