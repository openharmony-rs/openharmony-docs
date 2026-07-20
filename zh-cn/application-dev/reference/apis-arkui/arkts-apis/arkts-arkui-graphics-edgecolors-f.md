# edgeColors

<a id="edgecolors"></a>
## edgeColors

```TypeScript
export function edgeColors(all: number): Edges<number>
```

用于生成边框颜色均设置为传入值的边框颜色对象。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export function edgeColors(all: number): Edges<number>--><!--Device-unnamed-export function edgeColors(all: number): Edges<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| all | number | 是 | 边框颜色，ARGB格式，示例：0xffff00ff。<br/>取值范围：[0, 0xffffffff] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Edges](arkts-arkui-graphics-edges-i.md)&lt;number&gt; | 边框颜色均设置为传入值的边框颜色对象。 |

