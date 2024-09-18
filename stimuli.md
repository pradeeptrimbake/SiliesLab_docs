---
layout: page
title: Stimuli functions
nav_order: 3
---

# Stimulus File

Each stimulus file is designed to be easily created by any user. It is a CSV file with a specific structure and content that depends on the intended stimulus. Typically, one stimulus file contains only one type of stimulus object (e.g., just circles or just bars), but it can also be used to mix different stimulus types (stimulus objects), which can be individually referenced by specific stimulus functions.

All stimulus files consist of two sections. One section contains general stimulus parameters, which apply to all stimulus epochs, while the other section is epoch-specific, applying to each epoch individually and varying based on the type of stimulus (e.g., circles, bars, gratings, etc.). Below, the general parameters are explained. For explanations of the epoch-specific parameters, refer to the specific stimulus functions.

## General Parameters:

- **EPOCHS**: Total number of epochs.
- **MAXRUNTIME**: Defines a "search" vs. a "normal" stimulus file to be used during a recording. (For search, set this to `0`; for the recording file, set it to any reasonable number of seconds, e.g., `3600`, that the recording would take at maximum. It does not need to be exact.)
- **STIMULUSDATA**: If the stimulus type needs extra data to be plotted, otherwise set to `NULL`.
- **PERSPECTIVE_CORRECTION**: If perspective correction is applied, set to `1`; otherwise `0`.
- **RANDOMIZATION_MODE**: If the epochs’ presentation order is pseudorandomized, set to `1` or `2`; otherwise set to `0`. The randomization option `1` randomizes the epoch presentation, defining the first epoch of the file as an interstimulus epoch. The randomization option `2` shuffles the order of all epochs.

---

# Stimuli Functions

The following functions are used to generate different types of stimuli, located in `modules/stimuli.py` of our **pyVStim** custom package. PyVStim was created as a collaborative project, encouraging users to contribute new functions for additional stimulus types. The list of available stimuli is expected to grow and will need regular updates to include new contributions.

## 1. Full-field Flash

### Brief Description:
This stimulus function creates a circle (a PsychoPy stimulus object, `stim_obj`) with a specified size, contrast, position, and duration. Typically, the circle is centered in the middle of the projected rectangular window (the virtual screen, as defined by the function inputs) and is large, resulting in a full-field flash. However, this function can also be used to draw smaller circles on the screen and position them wherever desired.

### General Parameters:

- **EPOCHS**: Total number of epochs. E.g., `2` for ON-OFF full-field flashes.
- **MAXRUNTIME**: Same as defined in general parameters.
- **STIMULUSDATA**: Set to `NULL` as no extra data is needed for a circle object.
- **PERSPECTIVE_CORRECTION**: `1` if applied, otherwise `0`.
- **RANDOMIZATION_MODE**: Same as defined in general parameters.

### Epoch-specific Parameters:

| Stimulus.stimtype  | circle | circle |
|--------------------|--------|--------|
| Stimulus.bg        | 0      | 1      |
| Stimulus.fg        | 0      | 1      |
| Stimulus.duration  | 2      | 2      |
| Stimulus.radius    | 120    | 120    |
| Stimulus.tau       | 0      | 0      |
| Stimulus.x_center  | 0      | 0      |
| Stimulus.y_center  | 0      | 0      |

### List of Acronyms:

- **stimtype**: The type to choose is `circle`.
- **bg**: Background level of luminance.
- **fg**: Foreground level of luminance.
- **duration**: Total duration (in seconds) of the epoch.
- **radius**: Circle radius in degrees of visual angle.
- **tau**: Time (in seconds) that an epoch shows the foreground luminance during the total duration.
- **x_center**: Position of the center of the stimulus along the x-axis.
- **y_center**: Position of the center of the stimulus along the y-axis.

### Current Stimulus Function:
```python
def field_flash(exp_Info, bg_ls, fg_ls, stim_texture, noise_arr, stimdict, epoch, window, global_clock, duration_clock, outFile, out, stim_obj, dlpOK, viewpos, data, taskHandle=None, lastDataFrame=0, lastDataFrameStartTime=0):
    # Function implementation here

