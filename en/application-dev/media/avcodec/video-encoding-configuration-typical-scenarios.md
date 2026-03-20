# Video Encoding Configurations for Typical Scenarios

<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @fanghuameng-->
<!--Designer: @dpy2650--->
<!--Tester: @cyakee-->
<!--Adviser: @w_Machine_cc-->

This topic provides recommended configuration parameters for AVCodec video encoding in various scenarios. It aims to help you configure video encoders according to your specific needs.

Video encoding is widely used in scenarios such as short-range screen casting (typically screen encoding and delivery among multiple devices within 10 meters), video calls, video conferences, live streaming, video editing, and video sharing. Based on user experience requirements, these scenarios can be categorized into three major types: low-latency, real-time streaming, and offline encoding.

This topic offers the recommended parameter settings for video encoding in these three categories. You can select the appropriate configurations based on service requirements.


## General Development Steps

**Linking Dynamic Libraries in the CMake Script**

```cmake
target_link_libraries(sample PUBLIC libnative_media_codecbase.so)
target_link_libraries(sample PUBLIC libnative_media_core.so)
target_link_libraries(sample PUBLIC libnative_media_venc.so)
```

> **NOTE**
>
> The word **sample** in the preceding code snippet is only an example. Use the actual project directory name.
>

**Adding Header Files**

```c++
#include <multimedia/player_framework/native_avcodec_videoencoder.h>
#include <multimedia/player_framework/native_avcapability.h>
#include <multimedia/player_framework/native_avcodec_base.h>
#include <multimedia/player_framework/native_avformat.h>
#include <fstream>
```

## Low-Latency Encoding Scenarios

Low-latency encoding scenarios include interactive applications with stringent end-to-end latency requirements, such as short-range screen casting, video calls, video conferences, and co-host live streaming.

**How to Develop**

This section describes only the steps involved in the encoder configuration phase. You can learn the basic encoding process in [Video Encoding](video-encoding.md).

1. Set encoder parameters.

   Configure parameters suitable for low-latency encoding scenarios.

   The following table lists the recommended encoding parameters for typical resolutions (using H.265 as an example) in low-latency short-range screen casting scenarios.  
   | Resolution (px)   | Frame Rate (fps)| Bit Rate (kbit/s)| Key Frame Interval (ms)| Bit Rate Control Mode|
   | ------------------| -------- | -------- | ------ | ------ |
   | 2560 × 1600 | 60       | 5000     | 5000 |  CBR  |
   | 1920 × 1080 | 60       | 3500     | 5000 |  CBR  |
   | 1280 × 720 | 60       | 2500     | 5000 |  CBR  |
   | 960 × 540 | 60       | 1500    | 5000 |  CBR  |

   The following table lists the recommended encoding parameters for typical resolutions (using H.265 as an example) in low-latency video call, video conferencing, and co-host live streaming scenarios.  
   | Resolution (px)   | Frame Rate (fps)| Bit Rate (kbit/s)| Key Frame Interval (ms)| Bit Rate Control Mode|
   | ------------------| -------- | -------- | ------ | ------ |
   | 1920 × 1080 | 30       | 1500     | -1 |  CBR  |
   | 1280 × 720 | 30       | 1000     | -1 |  CBR  |
   | 960 × 540 | 30       | 700    | -1 |  CBR  |
   | 640 × 360 | 30       | 550     | -1 |  CBR  |
   | 320 × 180 | 20       | 200     | -1 |  CBR  |

   > **NOTE**
   > 
   > A key frame interval of -1 indicates that only the first frame is a key frame. You can dynamically configure encoder parameters during runtime based on transmission conditions and image quality to insert new key frames (IDR).  

   Taking the low-latency video call scenario as an example, the variable description in the example is as follows:

   **videoEnc**: pointer to the video encoder instance For the creation method, refer to step 2 (creating an encoder instance) in [Surface Mode](video-encoding.md#surface-mode).

   ```c++
   // 1. Create an AVFormat parameter instance.
   OH_AVFormat *format = OH_AVFormat_Create(); 
   // 2. Fill in the encoding parameter key-value pair (using the 1080p@30 fps SDR input source as an example).
   OH_AVFormat_SetIntValue(format, OH_MD_KEY_WIDTH, 1920); // (Mandatory) Video width.
   OH_AVFormat_SetIntValue(format, OH_MD_KEY_HEIGHT, 1080); // (Mandatory) Video height.
   OH_AVFormat_SetIntValue(format, OH_MD_KEY_PIXEL_FORMAT, AV_PIXEL_FORMAT_NV12); // (Mandatory) Format of the video source data.
   OH_AVFormat_SetIntValue(format, OH_MD_KEY_RANGE_FLAG, 0); // Video usability information (VUI): YUV value range flag of the video, where 0 indicates limited range and 1 indicates full range.
   OH_AVFormat_SetIntValue(format, OH_MD_KEY_COLOR_PRIMARIES, OH_ColorPrimary::COLOR_PRIMARY_BT709); // VUI: video source color gamut.
   OH_AVFormat_SetIntValue(format, OH_MD_KEY_TRANSFER_CHARACTERISTICS, OH_TransferCharacteristic::TRANSFER_CHARACTERISTIC_BT709); // VUI: OETF/EOTF curve.
   OH_AVFormat_SetIntValue(format, OH_MD_KEY_MATRIX_COEFFICIENTS, OH_MatrixCoefficient:: MATRIX_COEFFICIENT_BT709); // VUI: YUV and RGB conversion matrix.
   OH_AVFormat_SetIntValue(format, OH_MD_KEY_PROFILE, OH_HEVCProfile::HEVC_PROFILE_MAIN); // Video encoder profile.
   OH_AVFormat_SetDoubleValue(format, OH_MD_KEY_FRAME_RATE, 30.0); // (Mandatory) Video frame rate.
   OH_AVFormat_SetIntValue(format, OH_MD_KEY_I_FRAME_INTERVAL, -1); // (Mandatory) Key frame interval.
   OH_AVFormat_SetIntValue(format, OH_MD_KEY_VIDEO_ENCODE_BITRATE_MODE, OH_BitrateMode::BITRATE_MODE_CBR); // (Mandatory) Set the bit rate control mode to CBR.
   OH_AVFormat_SetLongValue(format, OH_MD_KEY_BITRATE, 1500000); // (Mandatory). Bit rate, in bit/s.  
   // 3. Set the encoding parameters of the video encoder.
   int32_t ret = OH_VideoEncoder_Configure(videoEnc, format);
   if (ret != AV_ERR_OK) {
       // Handle exceptions.
   }
   // 4. Destroy the AVFormat instance after the configuration is complete.
   OH_AVFormat_Destroy(format);
   ```

2. (Optional) Dynamically configure encoder parameters during running.

   For details, see step 9 in [Video Encoding in Surface Mode](video-encoding.md#surface-mode).

   ```c++
   // 1. Create an AVFormat parameter instance.
   OH_AVFormat *format = OH_AVFormat_Create();
   // 2. Fill in the encoding parameter key-value pairs (dynamically requesting IDR frames).
   OH_AVFormat_SetIntValue(format, OH_MD_KEY_REQUEST_I_FRAME, 1);
   // 3. Make the encoder parameters take effect.
   ret = OH_VideoEncoder_SetParameter(videoEnc, format);
   if (ret != AV_ERR_OK) {
       // Handle exceptions.
   }
   // 4. Destroy the AVFormat instance after the configuration is complete.
   OH_AVFormat_Destroy(format);
   ```
   To adapt to network fluctuations, you are advised to use the [temporally scalable video encoding](video-encoding-temporal-scalability.md) configuration.


## Real-Time Streaming Encoding Scenarios

Real-time streaming encoding is used in scenarios like entertainment live streaming and gaming live streaming, where the latency requirements for video are relatively low.

**How to Develop**

This section describes how to configure encoder parameters for real-time streaming scenarios in the encoder configuration phase. You can learn the basic encoding process in [Video Encoding](video-encoding.md).

In entertainment live streaming scenarios, the recommended encoding parameters for typical resolution (using H.265 as an example) are as follows.

| Resolution (px)    | Frame Rate (fps)| Bit Rate (kbit/s)| Key Frame Interval (ms)| Bit Rate Control Mode|
| ------------------| -------- | -------- | ------ | ------ |
| 1920 × 1080 | 25       | 3000     | 2000 |  VBR  |
| 1080 × 720 | 25       | 1500     | 2000 |  VBR  |
| 960 × 544 | 25       | 1000    | 2000 |  VBR  |
| 864 × 480 | 25       | 800     | 2000 |  VBR  |

In gaming live streaming scenarios, the recommended encoding parameters for typical resolution (using H.265 as an example) are as follows.

| Resolution (px)    | Frame Rate (fps)| Bit Rate (kbit/s)| Key Frame Interval (ms)| Bit Rate Control Mode|
| ------------------| -------- | -------- | ------ | ------ |
| 1920 × 1080 | 60      | 6000     | 5000 |  VBR  |

```c++
// 1. Create an AVFormat parameter instance.
OH_AVFormat *format = OH_AVFormat_Create();
// 2. Fill in the encoding parameter key-value pair (using the 1080p@25 fps SDR input source as an example).
OH_AVFormat_SetIntValue(format, OH_MD_KEY_WIDTH, 1080); // (Mandatory) Video width.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_HEIGHT, 1920); // (Mandatory) Video height.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_PIXEL_FORMAT, AV_PIXEL_FORMAT_NV12); // (Mandatory) Format of the video source data.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_RANGE_FLAG, 0); // VUI: YUV value range flag of the video, where 0 indicates limited range and 1 indicates full range.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_COLOR_PRIMARIES, OH_ColorPrimary::COLOR_PRIMARY_BT709); // VUI: video source color gamut.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_TRANSFER_CHARACTERISTICS, OH_TransferCharacteristic::TRANSFER_CHARACTERISTIC_BT709); // VUI: OETF/EOTF curve.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_MATRIX_COEFFICIENTS, OH_MatrixCoefficient:: MATRIX_COEFFICIENT_BT709); // VUI: YUV and RGB conversion matrix.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_PROFILE, OH_HEVCProfile::HEVC_PROFILE_MAIN); // Video encoder profile.
OH_AVFormat_SetDoubleValue(format, OH_MD_KEY_FRAME_RATE, 25.0); // (Mandatory) Video frame rate.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_I_FRAME_INTERVAL, 2000); // (Mandatory) Key frame interval, in ms.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_VIDEO_ENCODE_BITRATE_MODE, OH_BitrateMode::BITRATE_MODE_VBR); // (Mandatory) Set the bit rate control mode to VBR.
OH_AVFormat_SetLongValue(format, OH_MD_KEY_BITRATE, 3000000); // (Mandatory). Bit rate, in bit/s.
// 3. Set the encoding parameters of the video encoder.
int32_t ret = OH_VideoEncoder_Configure(videoEnc, format);
if (ret != AV_ERR_OK) {
    // Handle exceptions.
}
// 4. Destroy the AVFormat instance after the configuration is complete.
OH_AVFormat_Destroy(format);
```

Starting from API version 20, stable quality rate control (SQR) is recommended on platforms that support SQR instead of the variable bit rate (VBR) mode.

In entertainment live streaming scenarios, the recommended encoding parameters for typical resolution (using H.265 as an example) are as follows.

| Resolution (px)   | Frame Rate (fps)| SQR Quality Factor| Peak Bit Rate (kbit/s)| Key Frame Interval (ms)| Bit Rate Control Mode|
| ------------------| -------- | -------- | ------ | ------ | -------- |
| 1920 × 1080 | 25 |  25    | 3000     | 2000 |  SQR  |
| 1080 × 720 | 25  |  25   | 1500     | 2000 |  SQR  |
| 960 × 544 | 25  |  25  | 1000    | 2000 |  SQR  |
| 864 × 480 | 25  |  25  | 800     | 2000 |  SQR  |

In gaming live streaming scenarios, the recommended encoding parameters for typical resolution (using H.265 as an example) are as follows.

| Resolution (px)   | Frame Rate (fps)| SQR Quality Factor| Peak Bit Rate (kbit/s)| Key Frame Interval (ms)| Bit Rate Control Mode|
| ------------------| -------- | -------- | ------ | ------ | -------- |
| 1920 × 1080 | 60   |  25   | 6000     | 5000 |  SQR  |

The configuration for SQR mode is as follows:

```c++
// 1. Create an AVFormat parameter instance.
OH_AVFormat *format = OH_AVFormat_Create();
// 2. Fill in the encoding parameter key-value pair (using the 1080p@25 fps SDR input source as an example).
OH_AVFormat_SetIntValue(format, OH_MD_KEY_WIDTH, 1080); // (Mandatory) Video width.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_HEIGHT, 1920); // (Mandatory) Video height.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_PIXEL_FORMAT, AV_PIXEL_FORMAT_NV12); // (Mandatory) Format of the video source data.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_RANGE_FLAG, 0); // VUI: YUV value range flag of the video, where 0 indicates limited range and 1 indicates full range.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_COLOR_PRIMARIES, OH_ColorPrimary::COLOR_PRIMARY_BT709); // VUI: video source color gamut.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_TRANSFER_CHARACTERISTICS, OH_TransferCharacteristic::TRANSFER_CHARACTERISTIC_BT709); // VUI: OETF/EOTF curve.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_MATRIX_COEFFICIENTS, OH_MatrixCoefficient:: MATRIX_COEFFICIENT_BT709); // VUI: YUV and RGB conversion matrix.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_PROFILE, OH_HEVCProfile::HEVC_PROFILE_MAIN); // Video encoder profile.
OH_AVFormat_SetDoubleValue(format, OH_MD_KEY_FRAME_RATE, 25.0); // (Mandatory) Video frame rate.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_I_FRAME_INTERVAL, 2000); // (Mandatory) Key frame interval, in ms.

// 3. Query the SQR support status and select a proper bit rate control mode.
OH_AVCapability *cap = OH_AVCodec_GetCapability(OH_AVCODEC_MIMETYPE_VIDEO_HEVC, true);
if (cap == nullptr || !OH_AVCapability_IsEncoderBitrateModeSupported(cap, OH_BitrateMode::BITRATE_MODE_SQR)) { 
    //SQR is not supported. Use VBR instead.
    OH_AVFormat_SetIntValue(format, OH_MD_KEY_VIDEO_ENCODE_BITRATE_MODE, OH_BitrateMode::BITRATE_MODE_VBR); // (Mandatory) Set the bit rate control mode to VBR.
    OH_AVFormat_SetLongValue(format, OH_MD_KEY_BITRATE, 3000000); // (Mandatory). Bit rate, in bit/s.
} else {
    //SQR is supported. Set SQR parameters.
    OH_AVFormat_SetIntValue(format, OH_MD_KEY_VIDEO_ENCODE_BITRATE_MODE, OH_BitrateMode::BITRATE_MODE_SQR); // (Mandatory) Set the bit rate control mode to SQR.
    OH_AVFormat_SetIntValue(format, OH_MD_KEY_SQR_FACTOR, 25); // (Mandatory) Set the SQR quality factor. The value range is [0, 51]. A smaller value indicates higher image quality.
    OH_AVFormat_SetLongValue(format, OH_MD_KEY_MAX_BITRATE, 3000000); // (Mandatory) Peak bit rate, in bit/s.
}

// 4. Set the encoding parameters of the video encoder.
int32_t ret = OH_VideoEncoder_Configure(videoEnc, format);
if (ret != AV_ERR_OK) {
    // Handle exceptions.
}
// 5. Destroy the AVFormat instance after the configuration is complete.
OH_AVFormat_Destroy(format);
```


## Offline Encoding Scenarios

Offline encoding is used in scenarios such as video editing and video sharing.


**How to Develop**

This section describes how to configure encoder parameters for offline editing scenarios in the encoder configuration phase. You can learn the basic encoding process in [Video Encoding](video-encoding.md).

In video editing scenarios, the recommended encoding parameters for typical resolution (using H.265 as an example) are as follows.

| Resolution (px) | Frame Rate (fps)| Bit Rate (kbit/s)| Key Frame Interval (ms)| Bit Rate Control Mode|
| ------------------| -------- | -------- | ------ | ------ |
| 3840 × 2160 | 30       | 25000     | 5000 |  VBR  |
| 2560 × 1440 | 30       | 15000     | 5000 |  VBR  |
| 1920 × 1080 | 30       | 10000    | 5000 |  VBR  |
| 1280 × 720 | 30       | 5000     | 5000 |  VBR  |
| 854 × 480 | 30       | 2000     | 5000 |  VBR  |

In video sharing scenarios, the recommended encoding parameters for typical resolution (using H.265 as an example) are as follows.

| Resolution (px)   | Frame Rate (fps)| Bit Rate (kbit/s)| Key Frame Interval (ms)| Bit Rate Control Mode|
| ------------------| -------- | -------- | ------ | ------ |
| 3840 × 2160 | 30       | 5600     | 5000 |  VBR  |
| 2560 × 1440 | 30       | 4900     | 5000 |  VBR  |
| 1920 × 1080 | 30       | 2100    | 5000 |  VBR  |
| 1280 × 720 | 30       | 1400     | 5000 |  VBR  |
| 854 × 480 | 30       | 400     | 5000 |  VBR  |

```c++
// 1. Create an AVFormat parameter instance.
OH_AVFormat *format = OH_AVFormat_Create();
// 2. Fill in the encoding parameter key-value pair (using the 1080p@30 fps SDR input source as an example).
OH_AVFormat_SetIntValue(format, OH_MD_KEY_WIDTH, 1920); // (Mandatory) Video width.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_HEIGHT, 1080); // (Mandatory) Video height.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_PIXEL_FORMAT, AV_PIXEL_FORMAT_NV12); // (Mandatory) Format of the video source data.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_RANGE_FLAG, 0); // VUI: YUV value range flag of the video, where 0 indicates limited range and 1 indicates full range.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_COLOR_PRIMARIES, OH_ColorPrimary::COLOR_PRIMARY_BT709); // VUI: video source color gamut.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_TRANSFER_CHARACTERISTICS, OH_TransferCharacteristic::TRANSFER_CHARACTERISTIC_BT709); // VUI: OETF/EOTF curve.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_MATRIX_COEFFICIENTS, OH_MatrixCoefficient:: MATRIX_COEFFICIENT_BT709); // VUI: YUV and RGB conversion matrix.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_PROFILE, OH_HEVCProfile::HEVC_PROFILE_MAIN); // Video encoder profile.
OH_AVFormat_SetDoubleValue(format, OH_MD_KEY_FRAME_RATE, 30.0); // (Mandatory) Video frame rate.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_I_FRAME_INTERVAL, 5000); // (Mandatory) Key frame interval, in ms.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_VIDEO_ENCODE_BITRATE_MODE, OH_BitrateMode::BITRATE_MODE_VBR); // (Mandatory) Set the bit rate control mode to VBR.
OH_AVFormat_SetLongValue(format, OH_MD_KEY_BITRATE, 2100000); // (Mandatory). Bit rate, in bit/s.
// 3. Set the encoding parameters of the video encoder.
int32_t ret = OH_VideoEncoder_Configure(videoEnc, format);
if (ret != AV_ERR_OK) {
    // Handle exceptions.
}
// 4. Destroy the AVFormat instance after the configuration is complete.
OH_AVFormat_Destroy(format);
```

Starting from API version 20, stable quality rate control (SQR) is recommended on platforms that support SQR instead of the variable bit rate (VBR) mode.

In video editing scenarios, the recommended encoding parameters for typical resolution (using H.265 as an example) are as follows.

| Resolution (px)   | Frame Rate (fps)| SQR Quality Factor| Peak Bit Rate (kbit/s)| Key Frame Interval (ms)| Bit Rate Control Mode|
| ------------------| -------- | -------- | ------ | ------ | ------ |
| 3840 × 2160 | 30   | 25    | 25000     | 5000 |  SQR  |
| 2560 × 1440 | 30   | 25    | 15000     | 5000 |  SQR  |
| 1920 × 1080 | 30   | 25    | 10000    | 5000 |  SQR  |
| 1280 × 720 | 30   | 25    | 5000     | 5000 |  SQR  |
| 854 × 480 | 30   | 25    | 2000     | 5000 |  SQR  |

In video sharing scenarios, the recommended encoding parameters for typical resolution (using H.265 as an example) are as follows.

| Resolution (px)   | Frame Rate (fps)| SQR Quality Factor| Peak Bit Rate (kbit/s)| Key Frame Interval (ms)| Bit Rate Control Mode|
| ------------------| -------- | -------- | ------ | ------ |-------- |
| 3840 × 2160 | 30   | 25    | 5600     | 5000 |  SQR  |
| 2560 × 1440 | 30   | 25    | 4900     | 5000 |  SQR  |
| 1920 × 1080 | 30   | 25    | 2100    | 5000 |  SQR  |
| 1280 × 720 | 30   | 25    | 1400     | 5000 |  SQR  |
| 854 × 480 | 30   | 25    | 400     | 5000 |  SQR  |

The configuration for SQR mode is as follows:

```c++
// 1. Create an AVFormat parameter instance.
OH_AVFormat *format = OH_AVFormat_Create();
// 2. Fill in the encoding parameter key-value pair (using the 1080p@30 fps SDR input source as an example).
OH_AVFormat_SetIntValue(format, OH_MD_KEY_WIDTH, 1920); // (Mandatory) Video width.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_HEIGHT, 1080); // (Mandatory) Video height.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_PIXEL_FORMAT, AV_PIXEL_FORMAT_NV12); // (Mandatory) Format of the video source data.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_RANGE_FLAG, 0); // VUI: YUV value range flag of the video, where 0 indicates limited range and 1 indicates full range.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_COLOR_PRIMARIES, OH_ColorPrimary::COLOR_PRIMARY_BT709); // VUI: video source color gamut.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_TRANSFER_CHARACTERISTICS, OH_TransferCharacteristic::TRANSFER_CHARACTERISTIC_BT709); // VUI: OETF/EOTF curve.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_MATRIX_COEFFICIENTS, OH_MatrixCoefficient:: MATRIX_COEFFICIENT_BT709); // VUI: YUV and RGB conversion matrix.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_PROFILE, OH_HEVCProfile::HEVC_PROFILE_MAIN); // Video encoder profile.
OH_AVFormat_SetDoubleValue(format, OH_MD_KEY_FRAME_RATE, 30.0); // (Mandatory) Video frame rate.
OH_AVFormat_SetIntValue(format, OH_MD_KEY_I_FRAME_INTERVAL, 5000); // (Mandatory) Key frame interval, in ms.

// 3. Query the SQR support status and select a proper bit rate control mode.
OH_AVCapability *cap = OH_AVCodec_GetCapability(OH_AVCODEC_MIMETYPE_VIDEO_HEVC, true);
if (cap == nullptr || !OH_AVCapability_IsEncoderBitrateModeSupported(cap, OH_BitrateMode::BITRATE_MODE_SQR)) { 
    //SQR is not supported. Use VBR instead.
    OH_AVFormat_SetIntValue(format, OH_MD_KEY_VIDEO_ENCODE_BITRATE_MODE, OH_BitrateMode::BITRATE_MODE_VBR); // (Mandatory) Set the bit rate control mode to VBR.
    OH_AVFormat_SetLongValue(format, OH_MD_KEY_BITRATE, 2100000); // (Mandatory). Bit rate, in bit/s.
} else {
    //SQR is supported. Set SQR parameters.
    OH_AVFormat_SetIntValue(format, OH_MD_KEY_VIDEO_ENCODE_BITRATE_MODE, OH_BitrateMode::BITRATE_MODE_SQR); // (Mandatory) Set the bit rate control mode to SQR.
    OH_AVFormat_SetIntValue(format, OH_MD_KEY_SQR_FACTOR, 25); // (Mandatory) Set the SQR quality factor. The value range is [0, 51]. A smaller value indicates higher image quality.
    OH_AVFormat_SetLongValue(format, OH_MD_KEY_MAX_BITRATE, 2100000); // (Mandatory) Peak bit rate, in bit/s.
}

// 4. Set the encoding parameters of the video encoder.
int32_t ret = OH_VideoEncoder_Configure(videoEnc, format);
if (ret != AV_ERR_OK) {
    // Handle exceptions.
}
// 5. Destroy the AVFormat instance after the configuration is complete.
OH_AVFormat_Destroy(format);
```

## Note

The encoding suggestions in this section need to be optimized based on the actual service requirements. At a fixed bit rate, the image quality of video encoding varies significantly depending on the spatiotemporal complexity of the encoded video content. Typically, video content with complex motion and rich picture textures tends to appear blurry or pixelated when the bit rate is insufficient, and a higher bit rate needs to be configured in such cases.
 
