# TouchEvent

触屏输入事件。

**继承/实现关系：** TouchEvent extends [InputEvent](arkts-input-multimodalinput-inputevent-inputevent-i.md)

**起始版本：** 9

<!--Device-unnamed-export declare interface TouchEvent extends InputEvent--><!--Device-unnamed-export declare interface TouchEvent extends InputEvent-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## 导入模块

```TypeScript
import { SourceType, ToolType, TouchEvent, FixedMode, KeyAction, Touch } from '@kit.InputKit';
```

## fixedMode

```TypeScript
fixedMode?: FixedMode
```

修正坐标的模式。

**类型：** FixedMode

**起始版本：** 19

<!--Device-TouchEvent-fixedMode?: FixedMode--><!--Device-TouchEvent-fixedMode?: FixedMode-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。

## isInject

```TypeScript
isInject?: boolean
```

表示该触屏输入事件是否为注入事件。注入事件详细介绍可参考[@ohos.multimodalInput.inputEventClient](arkts-multimodalinput-inputeventclient.md)。

**类型：** boolean

**起始版本：** 20

<!--Device-TouchEvent-isInject?: boolean--><!--Device-TouchEvent-isInject?: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。

