---
title: "IOS Security Research : Assembling the tamarin-c by stacksmashing"
date: 2026-08-30 00:00:00 
categories: [ios-security]
tags: [guide, jtag, usb-c-hw-debug]
---


## Introduction

While reading about all usbliter8 related stuff i did a deep dive into the whole ios security scene and discovered the work of Thomas Roth aka stacksmashing, he developed a cheap version of the infamous Kanzi cable which gives uart and jtag/swd access to iphones(if you can demote them via jailbreak).

As his tamarin cable for lightning and the successor tamarin-c are not up for sale we have to assemble them ourselves. 

This post serves as a guide to assemble your tamarin-c.

![plugin](/assets/tamarin-c-hw/tamarin.jpg)
*tamarins have fking aura btw*


## Preparation & orders


1. git clone https://github.com/stacksmashing/tamarin-c-hw

2. Install KiCad: 
    (this is obv for windows if you have winget, if you have mac or linux go look up the respective downloads)

    winget install --id KiCad.KiCad -e

3. We need gerber files, drill files, bom.csv, cpl.csv to place our order at jlcpcb.


<details>
  <summary>What are Gerber, drill, BOM and CPL files? (click to expand)</summary>

  <p><strong>Gerber files</strong> — the "blueprint" of the PCB. Each file describes one layer (copper traces, solder mask, silkscreen, board outline). Together they tell the fab how to etch and print your board. Usually bundled in a single <code>.zip</code>.</p>

  <p><strong>Drill files</strong> — tell the machine where to drill every hole and how big it should be (vias, mounting holes, through-hole pads). Sometimes included in the Gerber zip, sometimes separate (<code>.drl</code> / Excellon).</p>

  <p><strong>BOM (Bill of Materials)</strong> — the list of every component: what it is, how many, and the exact part number (LCSC for JLCPCB). The "shopping list".</p>

  <p><strong>CPL (Component Placement List)</strong> — a.k.a. Pick-and-Place. Tells the assembly robot <em>where</em> each part goes and in which orientation (X/Y, rotation, top/bottom). BOM says <em>what</em>, CPL says <em>where</em>.</p>
</details>

For this we can use a plugin that generates all the files in the exact way the manufacturer needs them to assemble our order.

Open KiCad -> Tools -> Plugin and Content Manager 

![plugin](/assets/tamarin-c-hw/kicadplug.png)
*https://github.com/bennymeg/Fabrication-Toolkit  <- if you want the source*


Open the pcb-editor and then export the files like this:

![plugin](/assets/tamarin-c-hw/pluginusage.png)



4. go to jlcpcb.com, click Order Now and go through the order process

    ![plugin](/assets/tamarin-c-hw/addgerb.png)
    *adding the gerber files*

    ![plugin](/assets/tamarin-c-hw/assem.png)
    *check the pcb assembly box and klick on next*




errors to correct:

c3,c4 r6,r7 have wrong lcsc numbers in the pcb files -> contact thomas 