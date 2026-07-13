# DateStyleOptions

DateStyleOptions定义日期内联型Counter的属性和事件。

继承于[CommonOptions](arkts-arkui-commonoptions-c.md)。

**继承/实现关系：** DateStyleOptions extends [CommonOptions](arkts-arkui-commonoptions-c.md)

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## day

```TypeScript
day?: number
```

设置日期内联型初始日。

默认值：1

取值范围：[1, 31]

超出取值范围按默认值处理。

**类型：** number

**默认值：** 1

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## month

```TypeScript
month?: number
```

设置日期内联型初始月份。

默认值：1

取值范围：[1, 12]

超出取值范围按默认值处理。

**类型：** number

**默认值：** 1

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDateChange

```TypeScript
onDateChange?: (date: DateData) => void
```

当日期改变时，返回当前日期。

date：当前显示的日期值。

值为undefined时，不显示当前的日期值。

**类型：** (date: DateData) => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## year

```TypeScript
year?: number
```

设置日期内联型初始年份。

默认值：1

取值范围：[1, 5000]

超出取值范围按默认值处理。

**类型：** number

**默认值：** 1

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

