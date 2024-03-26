---
layout: posts
title:  "Custom Heatsink-less 3D Printer Stepper Motor Drivers"
date:   2024-02-10 16:16:42 -0400
categories: projects
---
![Stepper Driver](/pictures/stepper.jpg)

## Introduction:
3D printer stepper motor drivers often appear in the form of socketed PCBs, commonly referred to as "StepSticks," and they almost alwyas inlcude a small aluminum heatsink stuck to the motor driver integrated circuit (IC). While this solution does work (and is likely still found in throusands of 3D printers in operation), it is far from optimal. This project explores a solution with potentially better thermal performance that does not even have a heatisnk!

## Design
This is a carrier board for the Allegro A5984 stepper motor driver IC that is compliant with the commonly used StepStick PCBs. It is identical in functionality to a standard StepStick, but offers more optimzed heat dissipation.

### Features
- 6 layers (allows the PCB to both dissipate and soak up more heat)
- no silkscreen over ground poors (less thermal resistance betwwen PCB and air)
- no heatsinks (poorly implemnted heatsinks can actually hurt rather than help- if you are curiuous as to why, keep reading)

## Detailed Information
### Background
I am not the first to realize that there is room for improvement in 3D printer motor drivers. Waterott went against the grain when they released their SilentStepSticks (based on Trinamic's silent stepper driver ICs). Instead of placing the IC on the top of the PCB, as was foung in earlier designes, they placed it on the bottom and placed the heatsink on the otherwires bare top of the PCB. At first, this may seem counter-intuitive: why would we place the source of heat generation further away from the heatsink? The answer is **thermal resistance**. Most ICs are encased in plastic a relatively poor thermal conductor. Higher power ICs (such as 3D printer stepper drivers) have some sort of thermal enhancement - almost always in the form of a large ground pad at the bottom of the IC. The intent is that this pad, when soldered to the PCB, can offer a lower resistance thermal path to the environment. This is exaclty what Waterott took advantage of; they placed several vias under this ground pad, createing a thermal path from the bottom of the PCB (where the IC is) to the top. However, this is still suboptimal.
### Design Decisions
The design of this stepper motor driver is very similar to that of Waterott's SilentStepSticks. The motor driver IC is on the bottom, and the top is completely bare. In fact, I did not add anything to their designs. Rather, I removed two things: the silkscreen on the top of the PCB and the heatsink. Removing the silkscreen is a fairly obvious improvement. It only acts to increase the thermal resistance between the copper on the PCB and the environment, but what about the heatsink? why would getting rid of that help? Heatsinks can be very effective at dissipating heat **if they have good thermal contact with the heat source**, and the ones we see on 3D printers... don't. The most common heatsink StepSticks ship with is a 13mm x 13mm aluminum heatsink with an unkown double sided thermally conductive adhesive tape. The problem is that, despite the name, this adhesive tape is actaully a pretty poor thermal conductor. For example, 3M's Thermally Conductive Adhesive Transfer Tape 9882  has a thermal conductiviy of 0.6 W/m-k. For reference, Arctic MX-4 thermal paste, which is often used inside computers, has a thermal conductivity of 8.5 W/m-k, almost 15 times higher. The problem is that this tape can act as a thermal barrier, trapping the heat in the PCB and IC. In other words, a poorly attached heatsink can be worse than no heatsink at all. Ideally we would attack heatinks with mounting screws and thermal paste or heck, even solder it direclty the PCB, but that requires time and/or money. With this design, I am simply verifying that we can forego the heatsink and get better thermal performance.


I hope you like it!