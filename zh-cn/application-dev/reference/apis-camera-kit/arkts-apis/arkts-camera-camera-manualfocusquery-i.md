# ManualFocusQuery

Manual Focus Query object.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

<!--Device-camera-interface ManualFocusQuery--><!--Device-camera-interface ManualFocusQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## isFocusDistanceSupported

```TypeScript
isFocusDistanceSupported(): boolean
```

Checks whether a focus distance is supported.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ManualFocusQuery-isFocusDistanceSupported(): boolean--><!--Device-ManualFocusQuery-isFocusDistanceSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Is focus distance supported. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

