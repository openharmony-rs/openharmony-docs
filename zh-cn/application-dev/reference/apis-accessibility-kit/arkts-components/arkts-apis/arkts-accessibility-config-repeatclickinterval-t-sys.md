# RepeatClickInterval（系统接口）

```TypeScript
type RepeatClickInterval = 'Shortest' | 'Short' | 'Medium' | 'Long' | 'Longest'
```

用于不同时间间隔的忽略重复点击。

忽略重复点击功能启用时（[ignoreRepeatClick](arkts-accessibility-config-con-sys.md#ignorerepeatclick)设置为true）配置生效；忽略重复点击功能未启用时（[ignoreRepeatClick](arkts-accessibility-config-con-sys.md#ignorerepeatclick)设置为false）不生效。

**起始版本：** 11

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

| 类型 | 说明 |
| --- | --- |
| 'Shortest' | 表示最短。 |
| 'Short' | 表示短。 |
| 'Medium' | 表示中。 |
| 'Long' | 表示长。 |
| 'Longest' | 表示最长。 |
