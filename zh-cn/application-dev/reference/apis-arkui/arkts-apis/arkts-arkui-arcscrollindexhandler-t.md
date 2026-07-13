# ArcScrollIndexHandler

```TypeScript
declare type ArcScrollIndexHandler = (start: number, end: number, center: number) => void
```

有子组件划入或划出ArcList显示区域时触发的回调。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 是 | ArcList显示区域内第一个子组件的索引值。 |
| end | number | 是 | ArcList显示区域内最后一个子组件的索引值。 |
| center | number | 是 | ArcList显示区域内中间位置子组件的索引值。 |

