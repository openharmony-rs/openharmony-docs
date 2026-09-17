# Image

## Overview

Enumerates the event types supported by the NativeNode component.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_IMAGE_ON_COMPLETE

```c
NODE_IMAGE_ON_COMPLETE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE
```

**Description**

Defines the image loading success event.<br> This event is triggered when an image is successfully loaded or decoded. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains nine parameters:**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32: loading status. The value <b>0</b> indicates that the image is<br>loaded successfully, and the value <b>1</b> indicates that the image is decoded successfully.</li><br><li>ArkUI_NodeComponentEvent.data[1].f32: width of the image, in px.</li><br><li>ArkUI_NodeComponentEvent.data[2].f32: height of the image, in px.</li><br><li>ArkUI_NodeComponentEvent.data[3].f32: width of the component, in px.</li><br><li>ArkUI_NodeComponentEvent.data[4].f32: height of the component, in px.</li><br><li>ArkUI_NodeComponentEvent.data[5].f32: offset of the rendered content relative to the component on the<br>x-axis, in px.</li><br><li>ArkUI_NodeComponentEvent.data[6].f32: offset of the rendered content relative to the component on the<br>y-axis, in px.</li><br><li>ArkUI_NodeComponentEvent.data[7].f32: actual rendered width of the image, in px.</li><br><li>ArkUI_NodeComponentEvent.data[8].f32: actual rendered height of the image, in px.</li> </ul>

**Since**: 12

### NODE_IMAGE_ON_ERROR

```c
NODE_IMAGE_ON_ERROR
```

**Description**

Defines the image loading failure event.<br> This event is triggered when an error occurs during image loading. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32: error code.<br><b>401</b>: The image could not be obtained because the image path is invalid.<br><b>103101</b>: The image format is not supported.</li> </ul>

**Since**: 12

### NODE_IMAGE_ON_SVG_PLAY_FINISH

```c
NODE_IMAGE_ON_SVG_PLAY_FINISH
```

**Description**

Defines the SVG animation playback completion event.<br> This event is triggered when the animation playback in the loaded SVG image is complete. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) does not contain parameters.

**Since**: 12

### NODE_IMAGE_ON_DOWNLOAD_PROGRESS

```c
NODE_IMAGE_ON_DOWNLOAD_PROGRESS
```

**Description**

Defines the image download progress event.<br> This event is triggered when downloading webpage images from page components. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].u32: number of bytes downloaded.</li><br><li>ArkUI_NodeComponentEvent.data[1].u32: total number of bytes to download.</li> </ul>

**Since**: 12


