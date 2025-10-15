# Capturing the Specified Area on a Screen

<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun-->
<!--Designer: @yxc2-->
<!--Tester: @zengxi_3007-->
<!--Adviser: @w_Machine_cc-->

## Basic Concepts

Starting from API version 20, you can capture a specified rectangular area of the screen during recording. This feature enhances the existing screen capture capability by allowing you to select a specific area to record. You can define this area by providing a screen capture ID (**displayId**) and the target capture area (**area**).
Before implementing this feature, familiarize yourself with the following concepts:
- Screen capture ID (**displayId**): ID of the screen where rectangular area capture will be performed.
- Target capture area (**area**): coordinates and dimensions of the region to be captured, including the starting point (x, y) and the width and height of the rectangular area.

## When to Use

This feature is particularly useful in scenarios such as:
- **Online education**: When teachers present various materials on a large screen, selectively capturing a specific rectangular area helps minimize distractions, allowing students to focus better on the core content.
- **Game streaming**: Players can capture only the game window during live streams or recordings, keeping the audience focused purely on the gameplay.

## How to Develop

**Linking Dynamic Libraries in the CMake Script**

```cmake
target_link_libraries(sample PUBLIC libnative_avscreen_capture.so)
```

> **NOTE**
>
> The word **sample** in the preceding code snippet is only an example. Use the actual project directory name.
>

**Adding Header Files**

```c++
#include "napi/native_api.h"
#include <multimedia/player_framework/native_avscreen_capture.h>
#include <multimedia/player_framework/native_avscreen_capture_base.h>
#include <multimedia/player_framework/native_avscreen_capture_errors.h>
#include <fcntl.h>
#include <string>
```

Call [OH_AVScreenCapture_SetCaptureArea()](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_setcapturearea) to specify the rectangular area you want to capture.

In the code snippet below, the following variables are used:

- **capture**: pointer to an [OH_AVScreenCapture](../../reference/apis-media-kit/capi-avscreencapture-oh-avscreencapture.md) instance.
- **displayId**: ID of the screen where the capture area is located.
- **area**: coordinates and width and height of the capture area. The type is OH_Rect, including member variables **x**, **y**, **width**, and **height**.
  - **x** and **y** indicate the horizontal and vertical coordinates of the start point of the rectangular area, respectively.
  - **width** and **height** indicate the width and height of the rectangular area, respectively.
  - Multiple parameters are separated by semicolons (;). All parameters are integers.
  - Before using, ensure that the input parameters are valid and avoid negative coordinates, width, and height.

> **NOTE**
> 
> **Capture area restrictions**:
> - Security layers cannot be captured.
> - Capturing across multiple screens is not supported.
> 
> **Changing the capture area**: The capture area can be updated while recording is in progress.
> 
> **Error handling**: If setting a new area fails, the system continues using the previous valid area. Implement proper error handling to ensure the expected area is used.
> 
> **Parameter requirements**: Coordinates, width, and height must be non-negative integers, and the capture area must remain within a single screen.

```c++
struct OH_AVScreenCapture *capture = OH_AVScreenCapture_Create();
// Initialize the screen capture parameters and pass in an OH_AVScreenRecorderConfig struct.
OH_AudioCaptureInfo miccapinfo = {.audioSampleRate = 16000, .audioChannels = 2, .audioSource = OH_MIC};
OH_VideoCaptureInfo videocapinfo = {
    .videoFrameWidth = 768, .videoFrameHeight = 1280, .videoSource = OH_VIDEO_SOURCE_SURFACE_RGBA};
OH_AudioInfo audioinfo = {
    .micCapInfo = miccapinfo,
};
OH_VideoInfo videoinfo = {.videoCapInfo = videocapinfo};
OH_AVScreenCaptureConfig config = {.captureMode = OH_CAPTURE_HOME_SCREEN,
                                    .dataType = OH_ORIGINAL_STREAM,
                                    .audioInfo = audioinfo,
                                    .videoInfo = videoinfo};
OH_AVScreenCapture_Init(capture, config);
// 1. (Optional) Set the coordinates and dimensions of the capture area. For example, the following creates a 100*100 rectangular area starting at (0, 0).
OH_Rect* region = new OH_Rect;
region->x = 0;
region->y = 0;
region->width = 100;
region->height = 100;
// 2. Set the ID of the display where the rectangular area is located.
uint64_t regionDisplayId = 0;
OH_AVScreenCapture_SetCaptureArea(capture, regionDisplayId, region);

// Start screen capture.
OH_AVScreenCapture_StartScreenCapture(capture);
```
