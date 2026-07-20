# GridItem属性/事件

**继承/实现关系：** GridItemAttribute extends [CommonMethod<GridItemAttribute>](CommonMethod<GridItemAttribute>)

**起始版本：** 7

<!--Device-unnamed-declare class GridItemAttribute extends CommonMethod<GridItemAttribute>--><!--Device-unnamed-declare class GridItemAttribute extends CommonMethod<GridItemAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="columnend"></a>
## columnEnd

```TypeScript
columnEnd(value: number)
```

设置当前元素终点列号。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridItemAttribute-columnEnd(value: number): GridItemAttribute--><!--Device-GridItemAttribute-columnEnd(value: number): GridItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 当前元素终点列号。<br/>需要指定GridItem起始行列号和所占行列数的场景推荐使用Grid的[GridLayoutOptions](arkts-arkui-gridlayoutoptions-i.md)参数，详细可参考Grid的[示例1（固定行列Grid）](docroot://reference/apis-arkui/arkui-ts/ts-container-grid.md#示例1固定行列grid)和[示例3（可滚动Grid设置跨行跨列节点）](docroot://reference/apis-arkui/arkui-ts/ts-container-grid.md#示例3可滚动grid设置跨行跨列节点)。<br/>取值范围：[0, 总列数-1] |

<a id="columnstart"></a>
## columnStart

```TypeScript
columnStart(value: number)
```

设置当前元素起始列号。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridItemAttribute-columnStart(value: number): GridItemAttribute--><!--Device-GridItemAttribute-columnStart(value: number): GridItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 当前元素起始列号。<br/>需要指定GridItem起始行列号和所占行列数的场景推荐使用Grid的[GridLayoutOptions](arkts-arkui-gridlayoutoptions-i.md)参数，详细可参考Grid的[示例1（固定行列Grid）](docroot://reference/apis-arkui/arkui-ts/ts-container-grid.md#示例1固定行列grid)和[示例3（可滚动Grid设置跨行跨列节点）](docroot://reference/apis-arkui/arkui-ts/ts-container-grid.md#示例3可滚动grid设置跨行跨列节点)。<br/>取值范围：[0, 总列数-1] |

<a id="forcerebuild"></a>
## forceRebuild

```TypeScript
forceRebuild(value: boolean)
```

设置在触发组件build时是否重新创建此节点。

> **说明：**  
>  
> 从API version 7开始支持，从API version 9开始废弃。GridItem会根据自身属性和子组件变化自行决定是否需要重新创建，无需设置。

**起始版本：** 7

**废弃版本：** 9

<!--Device-GridItemAttribute-forceRebuild(value: boolean): GridItemAttribute--><!--Device-GridItemAttribute-forceRebuild(value: boolean): GridItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 在触发组件build时是否重新创建此节点。<br/>默认值：false |

<a id="onselect"></a>
## onSelect

```TypeScript
onSelect(event: (isSelected: boolean) => void)
```

GridItem元素被鼠标框选的状态改变时触发回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridItemAttribute-onSelect(event: (isSelected: boolean) => void): GridItemAttribute--><!--Device-GridItemAttribute-onSelect(event: (isSelected: boolean) => void): GridItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (isSelected: boolean) =&gt; void | 是 | 回调函数。进入鼠标框选范围即被选中返回true，移出鼠标框选范围即未被选中返回false。 |

<a id="rowend"></a>
## rowEnd

```TypeScript
rowEnd(value: number)
```

设置当前元素终点行号。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridItemAttribute-rowEnd(value: number): GridItemAttribute--><!--Device-GridItemAttribute-rowEnd(value: number): GridItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 当前元素终点行号。<br/>需要指定GridItem起始行列号和所占行列数的场景推荐使用Grid的[GridLayoutOptions](arkts-arkui-gridlayoutoptions-i.md)参数，详细可参考Grid的[示例1（固定行列Grid）](docroot://reference/apis-arkui/arkui-ts/ts-container-grid.md#示例1固定行列grid)和[示例3（可滚动Grid设置跨行跨列节点）](docroot://reference/apis-arkui/arkui-ts/ts-container-grid.md#示例3可滚动grid设置跨行跨列节点)。<br/>取值范围：[0, 总行数-1] |

<a id="rowstart"></a>
## rowStart

```TypeScript
rowStart(value: number)
```

设置当前元素起始行号。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridItemAttribute-rowStart(value: number): GridItemAttribute--><!--Device-GridItemAttribute-rowStart(value: number): GridItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 当前元素起始行号。<br/>需要指定GridItem起始行列号和所占行列数的场景推荐使用Grid的[GridLayoutOptions](arkts-arkui-gridlayoutoptions-i.md)参数，详细可参考Grid的[示例1（固定行列Grid）](docroot://reference/apis-arkui/arkui-ts/ts-container-grid.md#示例1固定行列grid)和[示例3（可滚动Grid设置跨行跨列节点）](docroot://reference/apis-arkui/arkui-ts/ts-container-grid.md#示例3可滚动grid设置跨行跨列节点)。<br/>取值范围：[0, 总行数-1] |

<a id="selectable"></a>
## selectable

```TypeScript
selectable(value: boolean)
```

设置当前GridItem元素是否可以被鼠标框选。外层Grid容器的鼠标框选开启时，GridItem的框选才生效。

该属性需要在设置[多态样式](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)前使用才能生效选中态样式。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridItemAttribute-selectable(value: boolean): GridItemAttribute--><!--Device-GridItemAttribute-selectable(value: boolean): GridItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 当前GridItem元素是否可以被鼠标框选。设置为true时可以被鼠标框选，设置为false时无法被鼠标框选。<br/>默认值：true |

<a id="selected"></a>
## selected

```TypeScript
selected(value: boolean)
```

设置当前GridItem选中状态。该属性支持[$$](docroot://ui/state-management/arkts-two-way-sync.md)双向绑定变量。

该属性需要在设置[多态样式](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)前使用才能生效选中态样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridItemAttribute-selected(value: boolean): GridItemAttribute--><!--Device-GridItemAttribute-selected(value: boolean): GridItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 当前GridItem选中状态。设置为true时为选中状态，设置为false时为默认状态。<br/>默认值：false |

