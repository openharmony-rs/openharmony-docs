# ManualExposure

ManualExposure extends [ManualExposureQuery]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ Provides APIs to obtain and set the exposure duration.

**继承/实现关系：** ManualExposure extends [ManualExposureQuery](arkts-camera-camera-manualexposurequery-i.md)

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-camera-interface ManualExposure extends ManualExposureQuery--><!--Device-camera-interface ManualExposure extends ManualExposureQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## getExposure

ArkTS-Dyn:
```TypeScript
getExposure(): number
```

ArkTS-Sta:
```TypeScript
getExposure(): int
```

Obtains the manual exposure duration in use.

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-ManualExposure-getExposure(): int--><!--Device-ManualExposure-getExposure(): int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | The current exposure value, in units of ms |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

**示例：**

```TypeScript
function getExposure(nightPhotoSession: camera.NightPhotoSession): number | undefined {
  let exposureRange: Array<number> = nightPhotoSession.getSupportedExposureRange();
  if (exposureRange === undefined || exposureRange.length <= 0) {
    return undefined;
  }
  let exposure: number = nightPhotoSession.getExposure();
  return exposure;
}
```

## getExposureDuration

ArkTS-Dyn:
```TypeScript
getExposureDuration(): number
```

ArkTS-Sta:
```TypeScript
getExposureDuration(): int
```

Gets current exposure value.

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ManualExposure-getExposureDuration(): int--><!--Device-ManualExposure-getExposureDuration(): int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | The current exposure value, in units of microsecond |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, session or inputdevice maybe abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setExposure

ArkTS-Dyn:
```TypeScript
setExposure(exposure: number): void
```

ArkTS-Sta:
```TypeScript
setExposure(exposure: int): void
```

Sets the manual exposure duration. Before using this API, call [getSupportedExposureRange]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ to obtain the supported manual exposure durations, in ms.

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-ManualExposure-setExposure(exposure: int): void--><!--Device-ManualExposure-setExposure(exposure: int): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| exposure | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | Manual exposure duration, which must be one of the supported durations obtained by running [getSupportedExposureRange]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

## setExposureDuration

ArkTS-Dyn:
```TypeScript
setExposureDuration(exposureDuration: number): void
```

ArkTS-Sta:
```TypeScript
setExposureDuration(exposureDuration: int): void
```

Sets Exposure duration value, units: microseconds.This control is only effective if ExposureMode is set to EXPOSURE\_MODE\_MANUAL.

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ManualExposure-setExposureDuration(exposureDuration: int): void--><!--Device-ManualExposure-setExposureDuration(exposureDuration: int): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| exposureDuration | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | Exposure duration value |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

