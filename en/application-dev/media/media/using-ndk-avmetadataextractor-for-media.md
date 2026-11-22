---
kits: ["Media Kit / Media Services"]
description: "Describes using AVMetadataExtractor C/C++ APIs to extract metadata from media resources for native media information queries."
keywords: [AVMetadataExtractor, C/C++, Native API, metadata extraction, OH_AVMetadataExtractor, SetFDSource, FetchMetadata, NDK, media information query]
doctype: guide
status: active
---
# Using AVMetadataExtractor to Obtain Metadata (C/C++)
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=51e3345abdb25c275cac855fb1b85ab66aa4eaa1 translatedAt=2026-11-02T02:33:31.187Z pushedAt=2026-11-02T02:33:31.187Z nl=1 -->

You can use the AVMetadataExtractor to obtain metadata from a raw media asset. This topic walks you through on how to obtain the metadata of a media asset.

The full process of obtaining the metadata of a media asset includes creating an AVMetadataExtractor instance, setting resources, obtaining the metadata, and releasing the instance.

## How to Develop
Link the dynamic libraries in the CMake script.
```C++
target_link_libraries(entry PUBLIC libavmetadata_extractor.so libace_napi.z.so )
```

Include the following header file to use [native_avformat.h](../../reference/apis-avcodec-kit/capi-native-avformat-h.md) APIs.
```C++
#include <multimedia/player_framework/native_avformat.h>
```

In addition, link the following dynamic library in the CMake script:
```C++
target_link_libraries(entry PUBLIC libnative_media_core.so)
```

To use [OH_PixelmapNative_ConvertPixelmapNativeToNapi()](../../reference/apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_convertpixelmapnativetonapi) to convert a nativePixelMap object into a PixelMapnapi object and use [OH_PixelmapNative_Release()](../../reference/apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_release) to release the OH_PixelmapNative object, include the following header file:
```C++
#include <multimedia/image_framework/image/pixelmap_native.h>
```

In addition, link the following dynamic library in the CMake script:
```C++
target_link_libraries(entry PUBLIC libpixelmap.so libpixelmap_ndk.z.so)
```

To use system logging, include the following header file:
```C++
#include <hilog/log.h>
```

In addition, link the following dynamic library in the CMake script:
```C++
target_link_libraries(entry PUBLIC libhilog_ndk.z.so)
```

You can use the APIs related to metadata retrieval by including the header files [avmetadata_extractor.h](../../reference/apis-media-kit/capi-avmetadata-extractor-h.md), [avmetadata_extractor_base.h](../../reference/apis-media-kit/capi-avmetadata-extractor-base-h.md), and [native_averrors.h](../../reference/apis-avcodec-kit/capi-native-averrors-h.md).

Read [AVMetadataExtractor](../../reference/apis-media-kit/capi-avmetadataextractor.md) for the API reference.

1. Call [OH_AVMetadataExtractor_Create()](../../reference/apis-media-kit/capi-avmetadata-extractor-h.md#oh_avmetadataextractor_create) to create an instance.
    ```c
    #include <multimedia/player_framework/avmetadata_extractor.h>
    // Create an OH_AVMetadataExtractor instance.
    OH_AVMetadataExtractor* mainExtractor = OH_AVMetadataExtractor_Create();
    ```

2. Call [OH_AVMetadataExtractor_SetFDSource()](../../reference/apis-media-kit/capi-avmetadata-extractor-h.md#oh_avmetadataextractor_setfdsource) to set the file descriptor of a media resource.

   If different AVMetadataExtractor or [AVImageGenerator](../../reference/apis-media-kit/capi-avimagegenerator.md) instances need to operate the same resource, the file descriptor needs to be opened for multiple times. Therefore, do not share a file descriptor.
    ```c
    #include "napi/native_api.h"
    #include <multimedia/player_framework/avmetadata_extractor.h>
    int64_t offset = 0; // Offset of the media source in the file descriptor.
    int32_t fileDescribe = -1; // File descriptor of the media file.
    int32_t fileSize = 0; // Size of the media file.
    
    // GetInputParams is a helper function used to obtain the input parameters of FetchAlbumCover and FetchMetadata. For details, see the complete example.
    if (!GetInputParams(env, info, offset, fileDescribe, fileSize)) {
        return nullptr;
    }
     // Set the file descriptor of the media resource.
    OH_AVErrCode avErrCode = OH_AVMetadataExtractor_SetFDSource(mainExtractor, fileDescribe, offset, fileSize);
    // Handle exceptions.
    if (avErrCode != AV_ERR_OK) {
        OH_AVMetadataExtractor_Release(mainExtractor);
        napi_throw_error(env, "EFAILED", "SetFDSource for metadata extractor failed");
        return nullptr;
    }
    ```

3. Call [OH_AVMetadataExtractor_FetchMetadata()](../../reference/apis-media-kit/capi-avmetadata-extractor-h.md#oh_avmetadataextractor_fetchmetadata) to obtain metadata.

   Call OH_AVFormat_Create() to create an OH_AVFormat object and access its key-value pairs to obtain metadata. After use, call OH_AVFormat_Destroy to destroy the object and prevent memory leaks. For details, see [native_avformat.h](../../reference/apis-avcodec-kit/capi-native-avformat-h.md).
   ```c
   // Obtain the metadata.
   avErrCode = OH_AVMetadataExtractor_FetchMetadata(mainExtractor, avMetadata);
   ```

4. For a video resource, you can use **OH_AVMetadataExtractor_FetchMetadata** to obtain the metadata such as width and height from the OH_AVFormat object, using functions like **OH_AVFormat_GetIntValue** and **GetStringValueFromAVFormat**.
    ```c
    // Parse the width and height of the video resource from the OH_AVFormat object as int32_t.
    int32_t width = 0;
    int32_t height = 0;
    OH_AVFormat_GetIntValue(avMetadata, OH_AVMETADATA_EXTRACTOR_VIDEO_WIDTH, &width);
    OH_AVFormat_GetIntValue(avMetadata, OH_AVMETADATA_EXTRACTOR_VIDEO_HEIGHT, &height);
    ```

5. For an audio resource, in addition to obtaining metadata such as the title and duration of the audio resource through the OH_AVFormat object, you can retrieve the album cover by calling [OH_AVMetadataExtractor_FetchAlbumCover()](../../reference/apis-media-kit/capi-avmetadata-extractor-h.md#oh_avmetadataextractor_fetchalbumcover).

   After use, call OH_PixelmapNative_Release to release the OH_PixelmapNative object. For details, see [OH_PixelmapNative_Release()](../../reference/apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_release).
    ```c
    #include <multimedia/image_framework/image/pixelmap_native.h>
    #include <multimedia/player_framework/avmetadata_extractor.h>

    #include <hilog/log.h>
    // Obtain the album cover.
    OH_PixelmapNative* pixelMap = nullptr;
    avErrCode = OH_AVMetadataExtractor_FetchAlbumCover(mainExtractor, &pixelMap);
    ```

6. Call [OH_AVMetadataExtractor_Release()](../../reference/apis-media-kit/capi-avmetadata-extractor-h.md#oh_avmetadataextractor_release) to destroy the instance and release resources.
    ```c
    // Release the OH_AVMetadataExtractor resource.
    OH_AVMetadataExtractor_Release(mainExtractor);
    ```


## Running the Sample Project

Refer to the sample project to obtain audio metadata and album cover.

1. Create a project, download the [sample project](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVMetadataExtractor/AVMetadataExtractorNDK), and copy its resources to the corresponding directories.
    ```txt
    AVMetadataExtractorNDK
    entry/src/main/ets/
    └── pages
        └── Index.ets (metadata retrieval UI)
    entry/src/main/
    ├── cpp
    │   ├── types
    │   │   └── libentry
    │   │       └── Index.d.ts (JavaScript mapping of NDK functions)
    │   ├── CMakeLists.txt (CMake script)
    │   └── napi_init.cpp (NDK functions)
    └── resources
        ├── base
        │   ├── element
        │   │   ├── color.json
        │   │   ├── float.json
        │   │   └── string.json
        │   └── media
        │
        └── rawfile
            └── test.mp3 (audio resource)
    ```
2. Compile and run the project.