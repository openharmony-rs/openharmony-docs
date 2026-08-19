# InputEvent(输入事件)

输入事件。

**起始版本：** 23

<!--Device-unnamed-export declare interface InputEvent--><!--Device-unnamed-export declare interface InputEvent-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## 导入模块

```TypeScript
import { InputEvent } from '@kit.InputKit';
import { inputEventClient } from '@kit.InputKit';
```

## actionTime

```TypeScript
actionTime: long
```

上报输入事件的时间，表示系统启动运行至今逝去的微秒数，单位为微秒（μs）。

**类型：** long

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InputEvent-actionTime: long--><!--Device-InputEvent-actionTime: long-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## deviceId

```TypeScript
deviceId: int
```

输入设备的唯一标识，同一个物理设备反复插拔或重启，设备ID可能会发生变化。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InputEvent-deviceId: int--><!--Device-InputEvent-deviceId: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## id

```TypeScript
id: int
```

事件ID。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InputEvent-id: int--><!--Device-InputEvent-id: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## screenId

```TypeScript
screenId: int
```

目标屏幕ID。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InputEvent-screenId: int--><!--Device-InputEvent-screenId: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## windowId

```TypeScript
windowId: int
```

目标窗口ID。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InputEvent-windowId: int--><!--Device-InputEvent-windowId: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

