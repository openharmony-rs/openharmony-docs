# InputWindowInfo

输入法软键盘的窗口信息。

**起始版本：** 10

<!--Device-inputMethod-export interface InputWindowInfo--><!--Device-inputMethod-export interface InputWindowInfo-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## displayId

```TypeScript
displayId?: number
```

输入法软键盘窗口所在的屏幕ID。

**模型约束：** 该参数仅可在Stage模型下使用。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputWindowInfo-displayId?: long--><!--Device-InputWindowInfo-displayId?: long-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## height

```TypeScript
height: number
```

输入法窗口的高度，单位为px。该参数应为整数，最小值为0，最大值为当前屏幕的高度。

**类型：** number

**起始版本：** 10

<!--Device-InputWindowInfo-height: long--><!--Device-InputWindowInfo-height: long-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## left

```TypeScript
left: number
```

输入法窗口左上顶点的横坐标，单位为px。该参数应为整数，最小值为0，最大值为当前屏幕的宽度。

**类型：** number

**起始版本：** 10

<!--Device-InputWindowInfo-left: int--><!--Device-InputWindowInfo-left: int-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## name

```TypeScript
name: string
```

输入法窗口的名称。

**类型：** string

**起始版本：** 10

<!--Device-InputWindowInfo-name: string--><!--Device-InputWindowInfo-name: string-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## top

```TypeScript
top: number
```

输入法窗口左上顶点的纵坐标，单位为px。该参数应为整数，最小值为0，最大值为当前屏幕的高度。

**类型：** number

**起始版本：** 10

<!--Device-InputWindowInfo-top: int--><!--Device-InputWindowInfo-top: int-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## width

```TypeScript
width: number
```

输入法窗口的宽度，单位为px。该参数应为整数，最小值为0，最大值为当前屏幕的宽度。

**类型：** number

**起始版本：** 10

<!--Device-InputWindowInfo-width: long--><!--Device-InputWindowInfo-width: long-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

