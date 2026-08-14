# edgeColors

## edgeColors

```TypeScript
export declare function edgeColors(all: int): NodeEdges<int>
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function edgeColors(all: int): NodeEdges<int>--><!--Device-unnamed-export declare function edgeColors(all: int): NodeEdges<int>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| all | int | 是 | 边框颜色，ARGB格式，示例：0xffff00ff。&lt;br/&gt;取值范围：[0, 0xffffffff] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NodeEdges](arkts-na-graphics-nodeedges-i.md)&lt;int&gt; | 边框颜色均设置为传入值的边框颜色对象。 |

