# ManualExposureQuery

Provides APIs to obtain the manual exposure range supported.

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-camera-interface ManualExposureQuery--><!--Device-camera-interface ManualExposureQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## getExposureBiasStep

ArkTS-Dyn:
```TypeScript
getExposureBiasStep(): number
```

ArkTS-Sta:
```TypeScript
getExposureBiasStep(): double
```

Get exposure bias step.

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ManualExposureQuery-getExposureBiasStep(): double--><!--Device-ManualExposureQuery-getExposureBiasStep(): double-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | exposure bias step. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, session or inputdevice maybe abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getSupportedExposureDurationRange

ArkTS-Dyn:
```TypeScript
getSupportedExposureDurationRange(): Array<number>
```

ArkTS-Sta:
```TypeScript
getSupportedExposureDurationRange(): Array<int>
```

Gets the supported manual exposure duration range, units: microseconds.

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ManualExposureQuery-getSupportedExposureDurationRange(): Array<int>--><!--Device-ManualExposureQuery-getSupportedExposureDurationRange(): Array<int>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Array&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Array&lt;int&gt; | The array of manual exposure range. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, session or inputdevice maybe abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

## getSupportedExposureRange

ArkTS-Dyn:
```TypeScript
getSupportedExposureRange(): Array<number>
```

ArkTS-Sta:
```TypeScript
getSupportedExposureRange(): Array<int>
```

Obtains the supported manual exposure durations.

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-ManualExposureQuery-getSupportedExposureRange(): Array<int>--><!--Device-ManualExposureQuery-getSupportedExposureRange(): Array<int>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Array&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Array&lt;int&gt; | Array of manual exposure durations supported, in ms. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

**示例：**

```TypeScript
function getSupportedExposureRange(nightPhotoSession: camera.NightPhotoSession): Array<number> {
  let exposureRange: Array<number> = nightPhotoSession.getSupportedExposureRange();
  return exposureRange;
}
```

