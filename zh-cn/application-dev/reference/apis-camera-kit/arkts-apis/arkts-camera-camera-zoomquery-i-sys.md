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

## getZoomPointInfos

```TypeScript
getZoomPointInfos(): Array<ZoomPointInfo>
```

获取当前模式的等效焦距信息列表。

**起始版本：** 23

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ZoomQuery-getZoomPointInfos(): Array<ZoomPointInfo>--><!--Device-ZoomQuery-getZoomPointInfos(): Array<ZoomPointInfo>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[ZoomPointInfo](arkts-camera-camera-zoompointinfo-i-sys.md)&gt; | 获取当前模式的等效焦距信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 12 - 24 |

## isZoomCenterPointSupported

```TypeScript
isZoomCenterPointSupported(): boolean
```

Checks whether zoom center point is supported.

**起始版本：** 23

<!--Device-ZoomQuery-isZoomCenterPointSupported(): boolean--><!--Device-ZoomQuery-isZoomCenterPointSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Is the zoom center point supported. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

