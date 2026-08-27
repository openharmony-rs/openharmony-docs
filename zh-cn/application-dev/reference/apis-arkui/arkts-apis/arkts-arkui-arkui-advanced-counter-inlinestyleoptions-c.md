# InlineStyleOptions

InlineStyleOptions定义了数值内联型Counter的属性和事件。继承于[CommonOptions](arkts-arkui-arkui-advanced-counter-commonoptions-c.md)。

> **说明：**
> 
> 1. min应小于等于max。若min大于max，则按max处理。

**继承/实现关系：** InlineStyleOptions extends [CommonOptions](arkts-arkui-arkui-advanced-counter-commonoptions-c.md)

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CounterComponent, CounterOptions, CounterType, DateData } from '@kit.ArkUI';
```

## onChange

```TypeScript
onChange?: (value: number) => void
```

数值改变时，返回当前值。使用场景：当需要在数值变化时执行自定义操作（如更新关联UI、记录日志、保存状态等）时传入此回调。value：当前显示的数值。默认值：数值改变时，不返回值。值为undefined时，按默认值处理。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 |  |

## max

```TypeScript
max?: number
```

设置Counter的最大值。默认值：999取值范围：[min, +∞)超出取值范围时（即设置值小于min），按min处理。值为undefined时，按默认值处理。

**类型：** number

**默认值：** 999

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## min

```TypeScript
min?: number
```

设置Counter的最小值。默认值：0取值范围：(-∞, max]超出取值范围时（即设置值大于max），按max处理。值为undefined时，按默认值处理。

**类型：** number

**默认值：** 0

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textWidth

```TypeScript
textWidth?: number
```

设置数值文本的宽度。默认值：自适应文本宽度。取值范围：[0, +∞)单位：vp超出取值范围时（即设置值小于0），按0处理。值为undefined时，按默认值处理。

**类型：** number

**默认值：** 0

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: number
```

设置Counter的初始值。默认值：0取值范围：[min, max]，其中min和max分别对应下述Counter的最小值和最大值（min默认为0，max默认为999）。超出取值范围时，如果值小于min，按min处理；如果值大于max，按max处理。

**类型：** number

**默认值：** 0

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
