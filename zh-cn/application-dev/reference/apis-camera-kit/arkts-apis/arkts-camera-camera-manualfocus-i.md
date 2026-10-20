# ManualFocus

```TypeScript
interface ManualFocus extends ManualFocusQuery
```

手动对焦对象。

**继承/实现关系：** ManualFocus extends [ManualFocusQuery](arkts-camera-camera-manualfocusquery-i.md)

**起始版本：** 24

<!--Device-camera-interface ManualFocus extends ManualFocusQuery--><!--Device-camera-interface ManualFocus extends ManualFocusQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getFocusDistance

```TypeScript
getFocusDistance(): number
```

获取当前对焦距离，取值范围为0.0到1.0，0.0表示镜头可对焦的最近距离，1.0表示最远距离。默认值为1.0。

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

<!--Device-ManualFocus-getFocusDistance(): double--><!--Device-ManualFocus-getFocusDistance(): double-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前的对焦距离。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal.<br>**适用版本：** 24+ |

## setFocusDistance

```TypeScript
setFocusDistance(distance: number): void
```

设置对焦距离。取值范围为0.0到1.0，0.0表示镜头可对焦的最近距离，1.0表示最远距离。默认值为1.0。

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

<!--Device-ManualFocus-setFocusDistance(distance: double): void--><!--Device-ManualFocus-setFocusDistance(distance: double): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| distance | number | 是 | 对焦距离。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal.<br>**适用版本：** 24+ |
