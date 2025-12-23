# NativeBuffer Development (C/C++)
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Felix-fangyang; @BruceXu; @dingpy-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
## Overview

The NativeBuffer module provides the **shared memory** feature, supporting memory application, use, query, and release.

Common development scenarios of NativeBuffer: Apply for **OH_NativeBuffer** instances through Native APIs, obtain memory properties, and map the ION memory to the process space.

## Available APIs

| API| Description| 
| -------- | -------- |
| OH_NativeBuffer_Alloc (const OH_NativeBuffer_Config \*config) | Creates an **OH_NativeBuffer** instance based on an **OH_NativeBuffer_Config** struct. A new **OH_NativeBuffer** instance is created each time this function is called. This function must be used in pair with **OH_NativeBuffer_Unreference**. Otherwise, memory leak occurs.|
| OH_NativeBuffer_Reference (OH_NativeBuffer \*buffer) | Increases the reference count of an **OH_NativeBuffer** instance by 1.| 
| OH_NativeBuffer_Unreference (OH_NativeBuffer \*buffer) | Decreases the reference count of an **OH_NativeBuffer** instance by 1 and, when the reference count reaches 0, destroys the instance.| 
| OH_NativeBuffer_GetConfig (OH_NativeBuffer \*buffer, OH_NativeBuffer_Config \*config) | Obtains the properties of an **OH_NativeBuffer** instance.| 
| OH_NativeBuffer_Map (OH_NativeBuffer \*buffer, void \*\*virAddr) | Maps the ION memory allocated to an **OH_NativeBuffer** instance to the process address space.| 
| OH_NativeBuffer_Unmap (OH_NativeBuffer \*buffer) | Unmaps the ION memory allocated to an **OH_NativeBuffer** instance from the process address space.| 
| OH_NativeBuffer_GetSeqNum (OH_NativeBuffer \*buffer) | Obtains the sequence number of an **OH_NativeBuffer** instance.| 

For details about the APIs, see [native_buffer](../reference/apis-arkgraphics2d/capi-oh-nativebuffer.md).

## How to Develop

The following describes how to use the aforementioned APIs to create an **OH_NativeBuffer** instance, obtain memory properties, and map the ION memory to the process address space.

**Adding Dynamic Link Libraries**

Add the following library to **CMakeLists.txt**:
```txt
libnative_buffer.so
```

**Including Header Files**
```c++
#include <native_buffer/native_buffer.h>
```

1. Create an **OH_NativeBuffer** instance.
    <!-- @[nativebuffer_alloc](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NdkNativeWindow/entry/src/main/cpp/NativeRender.cpp) -->

    ``` C++
    OH_NativeBuffer_Config config {
        .width = 0x100,
        .height = 0x100,
        .format = NATIVEBUFFER_PIXEL_FMT_RGBA_8888,
        .usage = NATIVEBUFFER_USAGE_CPU_READ | NATIVEBUFFER_USAGE_CPU_WRITE | NATIVEBUFFER_USAGE_MEM_DMA,
    };

    OH_NativeBuffer *nativeBuffer = OH_NativeBuffer_Alloc(&config);
    if (nativeBuffer == nullptr) {
        LOGE("OH_NativeBuffer_Alloc fail, nativeBuffer is null");
    }
    ```

2. Map the ION memory allocated to an **OH_NativeBuffer** instance to the process address space.
    Call **OH_NativeBuffer_Map** if the application needs to access the memory space of the buffer.
    <!-- @[nativebuffer_map](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NdkNativeWindow/entry/src/main/cpp/NativeRender.cpp) -->

    ``` C++
    void* virAddr = nullptr;
    int32_t ret = OH_NativeBuffer_Map(nativeBuffer, &virAddr);
    if (ret != 0) {
        LOGE("OH_NativeBuffer_Map Failed");
    }
    // ···
    ret = OH_NativeBuffer_Unmap(nativeBuffer);
    if (ret != 0) {
        LOGE("OH_NativeBuffer_Unmap Failed");
    }
    ```

3. Obtain the memory properties.
    <!-- @[nativebuffer_getconfig](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NdkNativeWindow/entry/src/main/cpp/NativeRender.cpp) -->

    ``` C++
    OH_NativeBuffer_Config config2 = {};
    OH_NativeBuffer_GetConfig(nativeBuffer, &config2);
    uint32_t hwBufferID = OH_NativeBuffer_GetSeqNum(nativeBuffer);
    ```

4. Destroy the **OH_NativeBuffer** instance.
    <!-- @[nativebuffer_unreference](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NdkNativeWindow/entry/src/main/cpp/NativeRender.cpp) -->

    ``` C++
    OH_NativeBuffer_Unreference(nativeBuffer);
    nativeBuffer = nullptr;
    ```
