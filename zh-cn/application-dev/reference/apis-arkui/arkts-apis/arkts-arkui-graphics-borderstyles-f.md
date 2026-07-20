# borderStyles

<a id="borderstyles"></a>
## borderStyles

```TypeScript
export function borderStyles(all: BorderStyle): Edges<BorderStyle>
```

用于生成边框样式均设置为传入值的边框样式对象。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export function borderStyles(all: BorderStyle): Edges<BorderStyle>--><!--Device-unnamed-export function borderStyles(all: BorderStyle): Edges<BorderStyle>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| all | [BorderStyle](arkts-arkui-borderstyle-e.md) | 是 | 边框样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Edges](arkts-arkui-graphics-edges-i.md)&lt;BorderStyle&gt; | 边框样式均设置为传入值的边框样式对象。 |

