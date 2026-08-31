---
title: "usbliter8ing my iPhone 11"
date: 2026-08-30 00:00:00 +0800
categories: [ios-security]
tags: [guide]
---

## Introduction

This guide will walk you through my experience using the somewhat new usbliter8 exploit on my iPhone 11. 


Follow the guide on https://web.archive.org/web/20260618140950/https://github.com/prdgmshift/usbliter8 by the paradigm shift team.

I had serious issues completing the step of getting into DFU mode. The only thing that worked for me is using this software to get into recovery mode:

![myfone](/assets/usbliter8/myfone.png)
*https://www.imyfone.com/ios-system-recovery/?position=home_product*

After entering recovery mode we follow this guys advice closely and execute the steps to go into DFU mode.

![myfone](/assets/usbliter8/reddit.png)
*https://www.reddit.com/r/jailbreak/comments/dv0abl/help_iphone_x_wont_enter_dfu_mode/*


After successfully entering DFU mode(device recognized by iTunes but screen black), we follow the rest of the guide and finally confirm the USB serial number on Windows like this:

Device Manager -> Universal Serial Bus -> right click your Device -> Properties -> Details -> Select Device Instance Path from the dropdown menu

![myfone](/assets/usbliter8/confirm.png)


A literal checkm8 level jailbreak in 2026 is nuts, A12X/Z(iPad Pro) remain to be implemented..