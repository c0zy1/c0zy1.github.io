---
title: "Patch2POC : ImageIO integer overflow"
date: 2026-09-01 00:00:00 
categories: [OpenSecurityTraining2]
tags: [Reverse Engineering]
---


## Introduction

1. reading the patch
2. getting the stock firmware
3. binexport, bindiff, analysis
4. setting up the vm, enabling ssh, downloading tools, disabling sip(lldb)
5. 




5. 
setting up the vm:

brew install --cask utm

use the vulnerable version we downloaded via ipsw to set up the vm


enabling ssh:

System Settings → Privacy & Security → Full Disk Access → Terminal 

sudo systemsetup -setremotelogin on

getting some tools:

run the script


disabling sip:

sudo csrutil disable
sudo reboot

6. debugging

building the trigger:

clang -framework Foundation -framework ImageIO \
      -framework AppKit -framework CoreGraphics \
      -g -O0 \
      -o trigger trigger.m

loading the binary:

pwndbg-lldb ./trigger
command source imageio.lldb
run test.psd



breakpoint setting mini tutorial:

ghidra:

1. window-> memory map -> base 
2. look at the adress of your function

in lldb:

1. image list -o -f ImageIO -> offset
2. ghidra addr+ offset
3. image lookup -a 0x19d26e600 -> should return the function or exact offset into a function you are looking for
4. breakpoint set -a 0x19d26e600

















sources:

https://www.virusbulletin.com/uploads/pdf/conference/vb2022/papers/VB2022-Exploit-archaeology-a-forensic-history-of-in-the-wild-NSO-Group-exploits.pdf
