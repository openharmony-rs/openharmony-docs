# ControlCenter

ControlCenter继承自[ControlCenterQuery](arkts-camera-camera-controlcenterquery-i.md)。 控制中心类，用于使能相机控制器。

**继承/实现关系：** ControlCenter extends [ControlCenterQuery](arkts-camera-camera-controlcenterquery-i.md)

**起始版本：** 23

<!--Device-camera-interface ControlCenter--><!--Device-camera-interface ControlCenter-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## enableControlCenter

```TypeScript
enableControlCenter(enabled: boolean): void
```

使能相机控制器。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ControlCenter-enableControlCenter(enabled: boolean): void--><!--Device-ControlCenter-enableControlCenter(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 开启或关闭相机控制器。true表示开启，false表示关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

