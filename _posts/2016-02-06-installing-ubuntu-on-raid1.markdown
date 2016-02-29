---
layout: post
title:  "installing ubuntu on server with raid1"
date:   2016-02-06 16:30:23 +0200
categories: deployment
---
when installign any os on out-of-box server you have to remember that raid is not configured. you have to go to your raid controller menu and create volumes, otherwise you will not see them when installing linux.

another issue that can be faced during installing ubuntu on servers is black screen after successful installation. the solution is setting in GRUB loader to NOMODESET.
press 'e' in your GRUB menu this will get you in editing mode.
fing 'quiet splash' part there and replace to 'nomodeset'. hit ctrl+x to boot.

more info here:
http://ubuntuforums.org/showthread.php?t=1613132