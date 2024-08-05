---
layout: page
title: Stimuli functions
nav_order: 3
---

# Stimuli functions

The following funtions are used to generate different kinds of stimuli located in ["moduels/stimuli.py"].

Example Syntax:

1. field_flash

```python
def field_flash (exp_Info,bg_ls,fg_ls,stim_texture,noise_arr,stimdict,   epoch, window, global_clock, duration_clock,outFile,out, stim_obj,dlpOK, viewpos, data,taskHandle = None, lastDataFrame = 0, lastDataFrameStartTime = 0):
```                

Description:

This stimulus function draws a stim_obj (circle or a rectangle) of a given size.
Usually, the the stimulus covers the whole screen, eliciting a full-field flash

    bg_ls: defines the level of luminance of the screen per epoch 

    fg_ls:  defines the level of luminance of the stim_obj per epoch

    pos: defines the posisitonb of the stim_obj. ["0,0"] is the center of the screen

    tau: duration in seconds for fg presentation

    duration: entire duration in seconds (bg + fg)
    
    framerate: is the refresh rate of the monitor 
