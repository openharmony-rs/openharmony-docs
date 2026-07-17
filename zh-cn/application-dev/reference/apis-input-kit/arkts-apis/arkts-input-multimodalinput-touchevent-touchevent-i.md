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

## action

```TypeScript
action: Action
```

触屏输入事件类型。

**类型：** Action

**起始版本：** 9

<!--Device-TouchEvent-action: Action--><!--Device-TouchEvent-action: Action-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## sourceType

```TypeScript
sourceType: SourceType
```

触屏来源的设备类型。

**类型：** SourceType

**起始版本：** 9

<!--Device-TouchEvent-sourceType: SourceType--><!--Device-TouchEvent-sourceType: SourceType-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## touch

```TypeScript
touch: Touch
```

当前触屏点信息。

**类型：** Touch

**起始版本：** 9

<!--Device-TouchEvent-touch: Touch--><!--Device-TouchEvent-touch: Touch-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## touches

```TypeScript
touches: Touch[]
```

所有触屏点。

**类型：** Touch[]

**起始版本：** 9

<!--Device-TouchEvent-touches: Touch[]--><!--Device-TouchEvent-touches: Touch[]-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

