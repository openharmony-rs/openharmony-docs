# FocusQuery

提供了查询是否支持当前对焦模式的方法。 > **说明：** > > - 本Interface的起始版本为API version 12。接口在API version 12发生兼容变更，保留了内层元素的起始版本信息，会出现外层元素@since版本号大于内层元素的情况，不影响接口使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface FocusQuery--><!--Device-camera-interface FocusQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## isFocusModeSupported

```TypeScript
isFocusModeSupported(afMode: FocusMode): boolean
```

检测对焦模式是否支持。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-FocusQuery-isFocusModeSupported(afMode: FocusMode): boolean--><!--Device-FocusQuery-isFocusModeSupported(afMode: FocusMode): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| afMode | FocusMode | 是 | 指定的焦距模式。传参为null或者undefined，作为0处理，手动对焦模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检测对焦模式是否支持。true表示支持，false表示不支持。接口调用失败会抛出相应错误码并返回undefined，错误码类型 [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

## isLockFocusTrackingSupported

```TypeScript
isLockFocusTrackingSupported(): boolean
```

检查设备是否支持锁定焦点跟踪的功能。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-FocusQuery-isLockFocusTrackingSupported(): boolean--><!--Device-FocusQuery-isLockFocusTrackingSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查是否支持锁定焦点跟踪。true表示支持，false表示不支持。接口调用失败会抛出相应错误码并返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

