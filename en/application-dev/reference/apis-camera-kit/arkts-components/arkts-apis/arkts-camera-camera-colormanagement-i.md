# ColorManagement

**ColorManagement** inherits from [ColorManagementQuery](arkts-camera-camera-colormanagementquery-i.md).

It provides the APIs for color space settings.

**Inheritance/Implementation:** ColorManagement extends [ColorManagementQuery](arkts-camera-camera-colormanagementquery-i.md)

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getActiveColorSpace

```TypeScript
getActiveColorSpace(): colorSpaceManager.ColorSpace
```

Obtains the color space in use.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| [colorSpaceManager.ColorSpace](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-colorspacemanager-colorspace-e.md) | Color space. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## setColorSpace

```TypeScript
setColorSpace(colorSpace: colorSpaceManager.ColorSpace): void
```

Sets a color space.

Before the setting, call [getSupportedColorSpaces](arkts-camera-camera-colormanagementquery-i.md#getsupportedcolorspaces) to obtain the supported color spaces. You are advised to call this API after [addOutput](arkts-camera-camera-session-i.md#addoutput) and before [commitConfig](arkts-camera-camera-session-i.md#commitconfig). If this API is called after [commitConfig](arkts-camera-camera-session-i.md#commitconfig), the camera session configuration will take a longer time.

P3 wide color gamut and HDR imaging:

An application can deliver different color space parameters to declare its support for P3 and HDR. If an application does not proactively set the color space, SDR is used by default in photo and video recording modes.

For different modes, enabling HDR, setting the color space, and configuring [CameraFormat](arkts-camera-camera-cameraformat-e.md) in the camera output stream [profile](arkts-camera-camera-profile-i.md) should match. For details, see the table below. For example, to enable HDR in video recording mode, set [CameraFormat](arkts-camera-camera-cameraformat-e.md) in the camera preview and video output stream [profiles](arkts-camera-camera-profile-i.md) to **CAMERA_FORMAT_YCRCB_P010** and the color space to **BT2020_HLG_LIMIT**.

To obtain HDR images in photo mode, set the color space to **DISPLAY_P3** or **BT2020_HLG**. **BT2020_HLG** provides a wider color gamut, and should be used together with the **CameraFormat**, including **CAMERA_FORMAT_YCRCB_P010** and **CAMERA_FORMAT_YCBCR_P010**, to improve the image quality.

Since API version 23, you can call the [getSupportedFullOutputCapability](arkts-camera-camera-cameramanager-i.md#getsupportedfulloutputcapability) API to check whether the preview format P010 is supported in photo mode.

- If the application does not set the color space, the default color space in photo mode is SRGB when the  
**CameraFormat** is **CAMERA_FORMAT_YUV_420_SP**, and the default color space is **BT2020_HLG** when the **CameraFormat** is **CAMERA_FORMAT_YCRCB_P010** or **CAMERA_FORMAT_YCBCR_P010**.  
- If the application sets the color space, in photo mode, the **CameraFormat** and **ColorSpace** must be  
configured according to the following mapping table. Otherwise, an error code will be returned in [setColorSpace](#setcolorspace) or [commitConfig](arkts-camera-camera-session-i.md#commitconfig).

Photo mode:

| SDR/HDR Photo Capture | CameraFormat| ColorSpace|  
|--------------------|------------| ------------|  
| SDR(Default) | [CAMERA_FORMAT_YUV_420_SP](arkts-camera-camera-cameraformat-e.md) | SRGB |
| HDR P3 | [CAMERA_FORMAT_YUV_420_SP](arkts-camera-camera-cameraformat-e.md) | DISPLAY_P3 |
| HDR BT.2020 | CAMERA_FORMAT_YCRCB_P010,<br>CAMERA_FORMAT_YCBCR_P010 | [BT2020_HLG](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-colorspacemanager-colorspace-e.md) |

In video recording mode, if SDR or HDR VIVID is enabled, the camera format and color space must be configured according to the relationships specified in the table below. Configurations that do not match the table will cause issues such as preview exceptions.

Recording mode:

| SDR/HDR Photo Capture | CameraFormat | ColorSpace |  
|--------------------|--------------------------|------------------|  
| SDR(Default) | [CAMERA_FORMAT_YUV_420_SP](arkts-camera-camera-cameraformat-e.md) | [BT709_LIMIT](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-colorspacemanager-colorspace-e.md) |
| HDR_VIVID | [CAMERA_FORMAT_YCRCB_P010](arkts-camera-camera-cameraformat-e.md) | BT2020_HLG_LIMIT,<br>BT2020_HLG |

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colorSpace | [colorSpaceManager.ColorSpace](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-colorspacemanager-colorspace-e.md) | Yes | The type of color space. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | The colorSpace does not match the format. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |
