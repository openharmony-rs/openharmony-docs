# WhiteBalanceQuery（系统接口）

提供了查询设备对指定的白平衡模式是否支持，以及获取设备支持的白平衡模式范围的方法。

**起始版本：** 23

<!--Device-camera-interface WhiteBalanceQuery--><!--Device-camera-interface WhiteBalanceQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## getColorTintRange

```TypeScript
getColorTintRange(): Array<int>
```

获取支持配置的白平衡色调调节范围。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-WhiteBalanceQuery-getColorTintRange(): Array<int>--><!--Device-WhiteBalanceQuery-getColorTintRange(): Array<int>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;int&gt; | 用于获取色调调节值的可调范围。若接口调用失败，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

