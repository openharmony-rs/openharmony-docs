# ZoomQuery

提供了与设备的缩放相关的查询功能，包括获取支持的缩放比例范围。 > **说明：** > > - 本Interface的起始版本为API version 12。接口在API version 12发生兼容变更，保留了内层元素的起始版本信息，会出现外层元素@since版本号大于内层元素的情况，不影响接口使用。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-camera-interface ZoomQuery--><!--Device-camera-interface ZoomQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## getRAWCaptureZoomRatioRange

ArkTS-Dyn:
```TypeScript
getRAWCaptureZoomRatioRange(): Array<number>
```

ArkTS-Sta:
```TypeScript
getRAWCaptureZoomRatioRange(): Array<double>
```

获取RAW拍摄期间支持的变焦比例范围。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ZoomQuery-getRAWCaptureZoomRatioRange(): Array<double>--><!--Device-ZoomQuery-getRAWCaptureZoomRatioRange(): Array<double>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Array&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Array&lt;double&gt; | 变焦比例范围。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getZoomPointInfos

```TypeScript
getZoomPointInfos(): Array<ZoomPointInfo>
```

获取当前模式的等效焦距信息列表。

**起始版本：** 26.0.0

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ZoomQuery-getZoomPointInfos(): Array<ZoomPointInfo>--><!--Device-ZoomQuery-getZoomPointInfos(): Array<ZoomPointInfo>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;ZoomPointInfo&gt; | 获取当前模式的等效焦距信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12 - 24 |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

## getZoomRatioRange

ArkTS-Dyn:
```TypeScript
getZoomRatioRange(): Array<number>
```

ArkTS-Sta:
```TypeScript
getZoomRatioRange(): Array<double>
```

获取支持的变焦范围。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-ZoomQuery-getZoomRatioRange(): Array<double>--><!--Device-ZoomQuery-getZoomRatioRange(): Array<double>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Array&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Array&lt;double&gt; | 用于获取可变焦距比范围，返回的数组包括其最小值和最大值。接口调用失败会抛出相应错误码并返回undefined，错误码类型 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

