---
title: Steam Guides
date: 2022-07-29 15:30:00 +0200
categories: [Steam, Information]
tags: [steam, artwork, information]
---
# Steam Guides

This little guide will hold different information in regards to Steam.  
All from how to generate a artwork on your profile, to generating a cfg file for CS: GO.  

## Artwork guide


## CS: GO

### Autoexec.cfg and Options
This guides holds the configuration for generating a good CFG file for CS: GO.  
Lanch Options:  
```
+exec autoexec.cfg -novid -console
```

Autoexec.cfg File generation. example location: 'E:\SteamLibrary\steamapps\common\Counter-Strike Global Offensive\csgo\cfg':  
```
//weapon viewmodel 
viewmodel_fov "65"
viewmodel_offset_x "2"
viewmodel_offset_y "2"
viewmodel_offset_z "-2"
viewmodel_presetpos "3"
cl_bob_lower_amt "5"
cl_bobamt_lat "0.1"
cl_bobamt_vert "0.1"
cl_bobcycle "0.98"
cl_viewmodel_shift_left_amt "0.5"
cl_viewmodel_shift_right_amt "0.25"

// Rates
rate "128000"
cl_cmdrate "128"
cl_updaterate "128"
cl_interp "0.0"
cl_interp_ratio "1"
cl_lagcompensation "1"

// Video
fps_max "350"
fps_max_menu "200"
mat_monitorgamma "1.8"
mat_queue_mode "-1" // auto detect multi-core rendering
mat_vsync "0"
r_dynamic "0"
r_drawtracers_firstperson "0"
mat_savechanges // write video settings to registry
cl_disablefreezecam “1”
cl_disablehtmlmotd “1”
mat_savechanges

// Binds
alias +fastswitch slot3; alias -fastswitch lastinv;
bind "q" "+fastswitch"
 
bind "MWHEELUP" "+jump"                  ;Use scroll to jump
bind "MWHEELDOWN" "+jump"                ;Use scroll to jump
 
alias "+jumpthrow" "+jump;-attack;-attack2"
alias "-jumpthrow" "-jump"
bind "h" "+jumpthrow"                    ;Jumpthrow bind for both left- and rightclick
bind "e" "+use; r_cleardecals"

// Removed
// ;bind "MOUSE1" "+attack; r_cleardecals"
```