---
layout: distill
title:  The fragments of PX4 documentation
date: 2023-09-02 23:50:00
description: The desperate search through a vast open-source project
tags: research, px4, pixhawk
categories: hardware
# thumbnail: assets/img/9.jpg
related_posts: false

authors:

- name: Parakh M. Gupta
  # url: "https://en.wikipedia.org/wiki/Albert_Einstein"
  affiliations:
   name: MRS, CTU-Prague

---


I have been working on the PX4 platform since 2016, and through this many things have changed and I have seen plenty of things that should be common knowledge but they are not. More can be found on [MRS Website](https://ctu-mrs.github.io/). Here are my collections as I learnt:

## Reading the logs

### Vehicle flight mode

`vehicle_status/nav_state`:\
\
flight_modes_table = {\
0: ('Manual'), # red\
1: ('Altitude'), # yellow\
2: ('Position'), # green\
10: ('Acro'), # olive\
14: ('Offboard'), # light blue\
15: ('Stabilized'), # dark blue\
16: ('Rattitude'), # orange # all AUTO-modes use the same color\
3: ('Mission'), # purple\
4: ('Loiter'), # purple\
5: ('Return to Land'), # purple\
6: ('RC Recovery'), # purple\
7: ('Return to groundstation'), # purple\
8: ('Land (engine fail)'), # purple\
9: ('Land (GPS fail)'), # purple\
12: ('Descend'), # purple\
13: ('Terminate'), # purple\
17: ('Takeoff'), # purple\
18: ('Land'), # purple\
19: ('Follow Target'), # purple\
20: ('Precision Land'), # purple\
21: ('Orbit'), # purple\
}

### RC Inputs

`input_rc/values.00` : Roll\
`input_rc/values.01` : Throttle\
`input_rc/values.02` : Pitch\
`input_rc/values.03` : Yaw\
`input_rc/values.04` : Offboard\
`input_rc/values.05` : Flight Mode\
`manual_control_switches/*` : Switches

## Motor Mixing Strategies

---

### Airmode : 0 : Disabled

- Mix RPT  
- Desaturate using thrust if needed (only reduction allowed)  
- Desaturate using roll if needed  
- Desaturate using pitch if needed  
- Mix Yaw  

### Airmode : 1 : RP

- Mix RPT  
- Desaturate using thrust if needed (both reduction and increase allowed)  
- Mix Yaw  

### Airmode 2 : RPY

- Mix RPTY  
- Desaturate using thrust if needed (both reduction and increase allowed)  
- Desaturate using yaw if needed  
