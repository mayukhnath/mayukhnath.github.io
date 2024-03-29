---
layout: posts
title:  "EnderStrain: A Custom Bed Probe for the Creality Ender 3"
date:   2024-03-25 16:16:42 -0400
categories: projects
header: 
  teaser: "/pictures/enderstrain.jpg"
---
![TABL](/pictures/enderstrain.jpg)

## Introduction
This is a cheap strain gauge based bed probe for the Creality Ender 3 3D printer. This can be used by the printer to measue the height of the bed at various x,y coordinates to compensate for variations. This strain gauge based approach has advantages over other bed height sensors because it uses the nozzle of the printer itself to probe the bed instead of a separately sensor. Therefore, there is no x,y offset or height offset tuning required.

## Objectives
- Support stock Ender 3 (or similar machines)
- Directly use the nozzle as the probing mechanism
- Cost less than $10 per probe
- Require minimal modifications to the stock printer
- Electrically compatible with the stock Ender 3 mainboard

## Outcomes
- Successfully use this probe on personal printer
- Repeatability testing results in range of about 0.02mm with standard deviation of 0.00675mm

## Design
- The PCB replaces the stock X carriage of the Ender 3
- Uses 4 BF350 strain guages in a wheatsone bridge configuration to detect bed
- HX717 ADC to measure the strain gauges
- STM32F103 Microcontroller reads ADC and generated trigger output

## Operation
{% include video id="1kl02DYJahtWyJAvuk9KwCKr-GpyGDPR6" provider="google-drive" %}

## Accuracy Testing
{% include video id="1tG7MMcx7201XCugWZ_a1MBBVAP9XqQyo" provider="google-drive" %}