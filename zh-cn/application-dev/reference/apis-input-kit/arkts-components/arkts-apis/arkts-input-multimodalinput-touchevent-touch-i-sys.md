# Touch

触屏点信息。

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## 导入模块

```TypeScript
import { Action as KeyAction, SourceType, ToolType, Touch, TouchEvent, FixedMode } from '@kit.InputKit';
```

## blobId

```TypeScript
blobId?: number
```

触摸点属性标识。当前仅支持单指触摸：左手触摸为1，右手触摸为2。默认值为系统自动识别。默认情况下不设置此属性。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。

## fixedDisplayX

```TypeScript
fixedDisplayX?: number
```

适配单手模式下screenX坐标的修正值，单位为像素（px）。默认值为0。

**类型：** number

**起始版本：** 19

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。

## fixedDisplayY

```TypeScript
fixedDisplayY?: number
```

适配单手模式下screenY坐标的修正值，单位为像素（px）。默认值为0。

**类型：** number

**起始版本：** 19

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。
