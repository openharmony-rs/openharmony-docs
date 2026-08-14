# ManualIsoQuery（系统接口）

Provides APIs to check whether a camera device supports manual ISO setting and obtain the ISO range supported by the device.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface ManualIsoQuery--><!--Device-camera-interface ManualIsoQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## getSupportedIsoRange

```TypeScript
getSupportedIsoRange(): int[]
```

Get a array of supported standard ISO sensitivity values, as defined in ISO 12232:2006.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ManualIsoQuery-getSupportedIsoRange(): int[]--><!--Device-ManualIsoQuery-getSupportedIsoRange(): int[]-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int[] | The array of ISO sensitivity values. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

