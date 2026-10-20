# ManualIso

```TypeScript
interface ManualIso extends ManualIsoQuery
```

手动ISO对象。

**继承/实现关系：** ManualIso extends [ManualIsoQuery](arkts-camera-camera-manualisoquery-i.md)

**起始版本：** 24

<!--Device-camera-interface ManualIso extends ManualIsoQuery--><!--Device-camera-interface ManualIso extends ManualIsoQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getIso

```TypeScript
getIso(): number
```

获取当前ISO值。

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

<!--Device-ManualIso-getIso(): int--><!--Device-ManualIso-getIso(): int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前的ISO值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal.<br>**适用版本：** 24+ |

## setIso

```TypeScript
setIso(iso: number): void
```

设置ISO感光度值，取值需在getSupportedIsoRange返回的范围内。如果曝光模式设置为EXPOSURE_MODE_LOCKED，此设置不生效。

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

<!--Device-ManualIso-setIso(iso: int): void--><!--Device-ManualIso-setIso(iso: int): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| iso | number | 是 | ISO感光度值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal.<br>**适用版本：** 24+ |
