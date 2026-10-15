# Value

```TypeScript
type Value = string | number | Decimal
```

表示用于构建Decimal的参数类型。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-type Value = string | double | Decimal--><!--Device-unnamed-type Value = string | double | Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

| 类型 | 说明 |
| --- | --- |
| string | 构造时可接受的数字格式字符串。 |
| double | 有限数字值。 |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | Decimal对象。 |
