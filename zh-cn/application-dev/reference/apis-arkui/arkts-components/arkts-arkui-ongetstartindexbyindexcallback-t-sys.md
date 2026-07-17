# OnGetStartIndexByIndexCallback（系统接口）

```TypeScript
declare type OnGetStartIndexByIndexCallback = (targetIndex: number) => StartLineInfo
```

根据指定的目标索引，计算Grid滚动到该位置时页面内对应的起始行，用于支持[scrollToIndex](arkts-arkui-scroll-scroller-c.md#scrolltoindex-1)等操作。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare type OnGetStartIndexByIndexCallback = (targetIndex: int) => StartLineInfo--><!--Device-unnamed-declare type OnGetStartIndexByIndexCallback = (targetIndex: int) => StartLineInfo-End-->

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetIndex | int | 是 | 要滚动到的目标GridItem的索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| StartLineInfo | 用于记录Grid页面内起始行的位置信息。@systemapi@stagemodelonly |

