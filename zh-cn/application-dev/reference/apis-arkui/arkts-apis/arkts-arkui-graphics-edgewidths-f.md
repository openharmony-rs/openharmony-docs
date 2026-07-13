# edgeWidths

## edgeWidths

```TypeScript
export function edgeWidths(all: number): Edges<number>
```

用于生成边框宽度均设置为传入值的边框宽度对象。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| all | number | 是 | 边框宽度，单位为vp。<br/>取值范围：[0, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Edges&lt;number&gt; | 边框宽度均设置为传入值的边框宽度对象。 |

