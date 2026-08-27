# DateStyleOptions

DateStyleOptions定义了日期内联型Counter的属性和事件。继承于[CommonOptions](arkts-arkui-arkui-advanced-counter-commonoptions-c.md)。

**继承/实现关系：** DateStyleOptions extends [CommonOptions](arkts-arkui-arkui-advanced-counter-commonoptions-c.md)

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CounterComponent, CounterOptions, CounterType, DateData } from '@kit.ArkUI';
```

## onDateChange

```TypeScript
onDateChange?: (date: DateData) => void
```

当日期改变时，返回当前日期。使用场景：当需要在日期变化时执行自定义操作（如更新关联UI、记录日志、保存状态等）时传入此回调。date：当前显示的日期值。默认值：不触发回调。值为undefined时，按默认值处理。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | [DateData](arkts-arkui-arkui-advanced-counter-datedata-c.md) | 是 |  |

## day

```TypeScript
day?: number
```

设置日期内联型初始日。默认值：1取值范围：[1, 31]  
**说明：**每个月份天数的具体取值范围由该月份的实际天数决定。超出取值范围按默认值处理。值为undefined时，按默认值处理。

**类型：** number

**默认值：** 1

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## month

```TypeScript
month?: number
```

设置日期内联型初始月份。默认值：1取值范围：[1, 12]超出取值范围按默认值处理。值为undefined时，按默认值处理。

**类型：** number

**默认值：** 1

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## year

```TypeScript
year?: number
```

设置日期内联型初始年份。默认值：1取值范围：[1, 5000]超出取值范围按默认值处理。值为undefined时，按默认值处理。

**类型：** number

**默认值：** 1

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
