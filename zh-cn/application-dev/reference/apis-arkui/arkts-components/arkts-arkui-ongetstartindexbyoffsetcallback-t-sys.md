# OnGetStartIndexByOffsetCallback（系统接口）

```TypeScript
declare type OnGetStartIndexByOffsetCallback = (totalOffset: number) => StartLineInfo
```

根据Grid的总偏移量，计算当前页面起始行的位置，用于快速滑动或反向滑动场景。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| totalOffset | double | 是 | 总滚动偏移量，即Grid当中第一个GridItem的顶部与Grid顶部之间的偏移量。<br/>单位：vp |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| StartLineInfo | 用于记录Grid页面内起始行的位置信息。@systemapi@stagemodelonly |

