# Touch

触屏点信息。

**起始版本：** 9

<!--Device-unnamed-export declare interface Touch--><!--Device-unnamed-export declare interface Touch-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## 导入模块

```TypeScript
import { SourceType, ToolType, TouchEvent, FixedMode, KeyAction, Touch } from '@kit.InputKit';
```

## blobId

```TypeScript
blobId?: number
```

触摸点属性标识。当前仅支持单指触摸：左手触摸为1，右手触摸为2。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Touch-blobId?: int--><!--Device-Touch-blobId?: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。

## fixedDisplayX

```TypeScript
fixedDisplayX?: number
```

适配单手模式下screenX坐标的修正值，单位为像素（px）。

**类型：** number

**起始版本：** 19

<!--Device-Touch-fixedDisplayX?: int--><!--Device-Touch-fixedDisplayX?: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。

## fixedDisplayY

```TypeScript
fixedDisplayY?: number
```

适配单手模式下screenY坐标的修正值，单位为像素（px）。

**类型：** number

**起始版本：** 19

<!--Device-Touch-fixedDisplayY?: int--><!--Device-Touch-fixedDisplayY?: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。

