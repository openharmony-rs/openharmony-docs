# CursorInfo

光标信息。

**起始版本：** 10

<!--Device-inputMethod-export interface CursorInfo--><!--Device-inputMethod-export interface CursorInfo-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## displayId

```TypeScript
displayId?: number
```

光标所在显示器的ID。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CursorInfo-displayId?: long--><!--Device-CursorInfo-displayId?: long-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## height

```TypeScript
height: number
```

光标的高度，单位为px。该参数应为整数，最小值为0，最大值为当前屏幕的高度。

**类型：** number

**起始版本：** 10

<!--Device-CursorInfo-height: double--><!--Device-CursorInfo-height: double-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## left

```TypeScript
left: number
```

光标的横坐标，单位为px。该参数应为整数，最小值为0，最大值为当前屏幕的宽度。

**类型：** number

**起始版本：** 10

<!--Device-CursorInfo-left: double--><!--Device-CursorInfo-left: double-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## top

```TypeScript
top: number
```

光标的纵坐标，单位为px。该参数应为整数，最小值为0，最大值为当前屏幕的高度。

**类型：** number

**起始版本：** 10

<!--Device-CursorInfo-top: double--><!--Device-CursorInfo-top: double-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## width

```TypeScript
width: number
```

光标的宽度，单位为px。该参数应为整数，最小值为0，最大值为当前屏幕的宽度。

**类型：** number

**起始版本：** 10

<!--Device-CursorInfo-width: double--><!--Device-CursorInfo-width: double-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

