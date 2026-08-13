# ManualExposure（系统接口）

ManualExposure extends [ManualExposureQuery](arkts-camera-camera-manualexposurequery-i.md#ManualExposureQuery（系统接口）) Provides APIs to obtain and set the exposure duration.

**继承/实现关系：** ManualExposure extends [ManualExposureQuery](arkts-camera-camera-manualexposurequery-i.md#ManualExposureQuery（系统接口）)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface ManualExposure--><!--Device-camera-interface ManualExposure-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## getExposure

```TypeScript
getExposure(): int
```

Obtains the manual exposure duration in use.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ManualExposure-getExposure(): int--><!--Device-ManualExposure-getExposure(): int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | The current exposure value, in units of ms |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect.<br>**适用版本：** 12+ |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

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

## setExposure

```TypeScript
setExposure(exposure: int): void
```

Sets the manual exposure duration. Before using this API, call [getSupportedExposureRange](arkts-camera-camera-manualexposurequery-i-sys.md#getSupportedExposureRange) to obtain the supported manual exposure durations, in ms.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ManualExposure-setExposure(exposure: int): void--><!--Device-ManualExposure-setExposure(exposure: int): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| exposure | int | 是 | Manual exposure duration, which must be one of the supported durations obtained by running [getSupportedExposureRange](arkts-camera-camera-manualexposurequery-i-sys.md#getSupportedExposureRange). |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed.<br>**适用版本：** 12+ |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

