# ZoomQuery

提供了与设备的缩放相关的查询功能，包括获取支持的缩放比例范围。 > **说明：** > > - 本Interface的起始版本为API version 12。接口在API version 12发生兼容变更，保留了内层元素的起始版本信息，会出现外层元素@since版本号大于内层元素的情况，不影响接口使用。

**起始版本：** 23

<!--Device-camera-interface ZoomQuery--><!--Device-camera-interface ZoomQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## getRAWCaptureZoomRatioRange

```TypeScript
getRAWCaptureZoomRatioRange(): Array<double>
```

获取RAW拍摄期间支持的变焦比例范围。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ZoomQuery-getRAWCaptureZoomRatioRange(): Array<double>--><!--Device-ZoomQuery-getRAWCaptureZoomRatioRange(): Array<double>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;double&gt; | 变焦比例范围。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getZoomRatioRange

```TypeScript
getZoomRatioRange(): Array<double>
```

获取支持的变焦范围。

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-ZoomQuery-getZoomRatioRange(): Array<double>--><!--Device-ZoomQuery-getZoomRatioRange(): Array<double>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;double&gt; | 用于获取可变焦距比范围，返回的数组包括其最小值和最大值。接口调用失败会抛出相应错误码并返回undefined，错误码类型 [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

