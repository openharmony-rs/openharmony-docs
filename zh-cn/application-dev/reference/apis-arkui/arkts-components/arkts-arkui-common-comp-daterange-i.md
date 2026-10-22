# DateRange

```TypeScript
declare interface DateRange
```

日期区间，用于描述起止日期区间。

**起始版本：** 19

<!--Device-unnamed-declare interface DateRange--><!--Device-unnamed-declare interface DateRange-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: Date
```

设置日期区间的结束日期。不传入、日期格式错误、日期超出系统支持范围或end早于start时，该日期区间无效。

**类型：** Date

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务中使用。

<!--Device-DateRange-end?: Date--><!--Device-DateRange-end?: Date-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: Date
```

设置日期区间的开始日期，应不晚于结束日期。不传入、日期格式错误、日期超出系统支持范围或start晚于end时，该日期区间无效。

**类型：** Date

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务中使用。

<!--Device-DateRange-start?: Date--><!--Device-DateRange-start?: Date-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
