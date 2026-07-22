# ColumnSplit属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。

**继承/实现关系：** ColumnSplitAttribute extends [CommonMethod<ColumnSplitAttribute>](CommonMethod<ColumnSplitAttribute>)

**起始版本：** 7

<!--Device-unnamed-declare class ColumnSplitAttribute extends CommonMethod<ColumnSplitAttribute>--><!--Device-unnamed-declare class ColumnSplitAttribute extends CommonMethod<ColumnSplitAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## divider

```TypeScript
divider(value: ColumnSplitDividerStyle | null)
```

设置分割线的margin。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ColumnSplitAttribute-divider(value: ColumnSplitDividerStyle | null): ColumnSplitAttribute--><!--Device-ColumnSplitAttribute-divider(value: ColumnSplitDividerStyle | null): ColumnSplitAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ColumnSplitDividerStyle](arkts-arkui-columnsplitdividerstyle-i.md) \| null | 是 | 分割线的margin，即设置分割线与子组件的距离。<br/>默认值：null。当设置为null时，分割线与子组件的距离为0vp。<br />非法值：按默认值处理。 |

## resizeable

```TypeScript
resizeable(value: boolean)
```

设置分割线是否可拖拽。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ColumnSplitAttribute-resizeable(value: boolean): ColumnSplitAttribute--><!--Device-ColumnSplitAttribute-resizeable(value: boolean): ColumnSplitAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 分割线是否可拖拽。设置为true时表示分割线可拖拽，设置为false时表示分割线不可拖拽。<br/>默认值：false <br />非法值：按默认值处理。 |

