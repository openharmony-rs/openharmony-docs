# RepeatClickInterval（系统接口）

```TypeScript
type RepeatClickInterval = 'Shortest' | 'Short' | 'Medium' | 'Long' | 'Longest'
```

忽略重复点击功能开启时（[ignoreRepeatClick](arkts-accessibility-config-con-sys.md#ignorerepeatclick)设置为true)，忽略重复点击的配置(即设置的RepeatClickInterval的值)生效；忽略重复点击功能关闭时（[ignoreRepeatClick](arkts-accessibility-config-con-sys.md#ignorerepeatclick)设置为false)，显示为正常类型。

**起始版本：** 11

<!--Device-config-type RepeatClickInterval = 'Shortest' | 'Short' | 'Medium' | 'Long' | 'Longest'--><!--Device-config-type RepeatClickInterval = 'Shortest' | 'Short' | 'Medium' | 'Long' | 'Longest'-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

| 类型 | 说明 |
| --- | --- |
| 'Shortest' | 表示最短。 |
| 'Short' | 表示短。 |
| 'Medium' | 表示中。 |
| 'Long' | 表示长。 |
| 'Longest' | 表示最长。 |

