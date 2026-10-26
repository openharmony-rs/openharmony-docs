# OH_PixelmapNative

```c
struct OH_PixelmapNative
```

## Overview

OH_PixelmapNative is an uncompressed pixel map format struct encapsulated at the native layer after image decoding. It supports operations such as pixel data read/write, opacity setting, scaling, translation, rotation, flipping, and cropping. It is suitable for scenarios where pixel-level processing and transformation of PixelMaps are required at the native layer.<br>To create an OH_PixelmapNative object, you need to use the OH_PixelmapNative_CreatePixelmap series of functions. If the source pixel format is not specified, these functions parse the source pixel data in the BGRA_8888 format by default. After use, you must call the OH_PixelmapNative_Release function to release the resources. These two operations must be paired; otherwise, memory leaks may occur.<br>The table below describes some functions and operation modes of the OH_PixelmapNative struct.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [drawable_descriptor.h](capi-drawable-descriptor-h.md)

