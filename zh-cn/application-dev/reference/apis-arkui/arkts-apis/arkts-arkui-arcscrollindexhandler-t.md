# ArcScrollIndexHandler

```TypeScript
export type ArcScrollIndexHandler = (start: int, end: int, center: int) => void
```

有子组件划入或划出ArcList显示区域时触发的回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export type ArcScrollIndexHandler = (start: int, end: int, center: int) => void--><!--Device-unnamed-export type ArcScrollIndexHandler = (start: int, end: int, center: int) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | int | 是 | ArcList显示区域内第一个子组件的索引值。 <br>取值限定为整数。 |
| end | int | 是 | ArcList显示区域内最后一个子组件的索引值。 <br>取值限定为整数。 |
| center | int | 是 | ArcList显示区域内中间位置子组件的索引值。 <br>取值限定为整数。 |

