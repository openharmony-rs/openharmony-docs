# ColorManagement

ColorManagement继承自[ColorManagementQuery]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。 色彩管理类，用于设置色彩空间参数。

**继承/实现关系：** ColorManagement extends [ColorManagementQuery](arkts-camera-camera-colormanagementquery-i.md)

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-camera-interface ColorManagement extends ColorManagementQuery--><!--Device-camera-interface ColorManagement extends ColorManagementQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## getActiveColorSpace

```TypeScript
getActiveColorSpace(): colorSpaceManager.ColorSpace
```

获取当前设置的色彩空间。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-ColorManagement-getActiveColorSpace(): colorSpaceManager.ColorSpace--><!--Device-ColorManagement-getActiveColorSpace(): colorSpaceManager.ColorSpace-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| colorSpaceManager.ColorSpace | 当前设置的色彩空间。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setColorSpace

```TypeScript
setColorSpace(colorSpace: colorSpaceManager.ColorSpace): void
```

设置色彩空间。 使用该接口前，必须先通过[getSupportedColorSpaces]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_获取当前设备所支持的 ColorSpaces。该接口建议在[addOutput]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_之后、 [commitConfig]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_之前调用，如果在[commitConfig]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_之后调 用该接口，会导致相机会话配置耗时增加。 P3广色域与HDR高动态范围成像： 应用可以下发不同的色彩空间（ColorSpace）参数来支持P3广色域以及HDR的功能。若应用不主动设置色彩空间，拍照、录像模式均默认为SDR拍摄。 应用针对不同模式使能HDR效果、设置的色彩空间以及设置相机输出流[Profile]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_中的[CameraFormat]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_一一对应关系可 参考下表。例如，在录像模式下若需要选择HDR拍摄，相机预览输出流和录像输出流[Profile]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_中的[CameraFormat]\_\_\_JSDOC\_LINK\_DESC\_USD\_7\_\_\_可 选择CAMERA\_FORMAT\_YCRCB\_P010，色彩空间ColorSpace可选择设置BT2020\_HLG\_LIMIT。 在拍照模式下，若需要获取HDR高显效果的图片，可通过设置色彩空间（ColorSpace）为DISPLAY\_P3或BT2020\_HLG实现。其中BT2020\_HLG能够表示更广的色域，需要搭配使用预览输出格式（ Profile.format）P010（CAMERA\_FORMAT\_YCRCB\_P010/CAMERA\_FORMAT\_YCBCR\_P010）来提升图像质感。 在录像模式下，通过设置色彩空间为H\_LOG, 可以录制LOG视频（不支持前置与微距）。 从API version 23开始，可以通过接口 [getSupportedFullOutputCapability]\_\_\_JSDOC\_LINK\_DESC\_USD\_8\_\_\_查询是否支持拍照模式下的预览P010 格式。 - 若应用不主动设置色彩空间，在拍照模式下，当预览输出格式为CAMERA\_FORMAT\_YUV\_420\_SP时，色彩空间默认为SRGB；当预览输出格式为CAMERA\_FORMAT\_YCRCB\_P010/ CAMERA\_FORMAT\_YCBCR\_P010时，色彩空间默认为BT2020\_HLG。 - 若应用主动设置色彩空间，在拍照模式下，预览输出格式与色彩空间必须按照下列表格中的对应关系配置，若不满足则会在 [setColorSpace]\_\_\_JSDOC\_LINK\_DESC\_USD\_9\_\_\_或[commitConfig]\_\_\_JSDOC\_LINK\_DESC\_USD\_10\_\_\_时返 回错误码。 拍照模式： | SDR/HDR拍摄 | 预览输出格式 | 色彩空间 | |--------------------|------------| ------------| | SDR(Default) | CAMERA\_FORMAT\_YUV\_420\_SP | SRGB | | HDR P3 | CAMERA\_FORMAT\_YUV\_420\_SP | DISPLAY\_P3 | | HDR BT.2020 | CAMERA\_FORMAT\_YCRCB\_P010,\_\_\_HTML\_TAG\_DESC\_USD\_11\_\_\_CAMERA\_FORMAT\_YCBCR\_P010 | BT2020\_HLG | 在录像模式下，使能SDR或HDR\_VIVID拍摄效果时，CameraFormat与ColorSpace必须按照下列表格中的对应关系配置，若不满足表格中CameraFormat与ColorSpace配置，会导致预览异常等问题。 录像模式： | SDR/HDR拍摄 | CameraFormat | ColorSpace | |--------------------|--------------------------|------------------| | SDR(Default) | CAMERA\_FORMAT\_YUV\_420\_SP | BT709\_LIMIT | | HDR\_VIVID | CAMERA\_FORMAT\_YCRCB\_P010 | BT2020\_HLG\_LIMIT,\_\_\_HTML\_TAG\_DESC\_USD\_12\_\_\_BT2020\_HLG |

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-ColorManagement-setColorSpace(colorSpace: colorSpaceManager.ColorSpace): void--><!--Device-ColorManagement-setColorSpace(colorSpace: colorSpaceManager.ColorSpace): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorSpace | colorSpaceManager.ColorSpace | 是 | The type of color space. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | The colorSpace does not match the format. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

