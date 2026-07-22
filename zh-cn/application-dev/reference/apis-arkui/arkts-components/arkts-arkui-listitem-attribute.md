# ListItem属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

**继承/实现关系：** ListItemAttribute extends [CommonMethod<ListItemAttribute>](CommonMethod<ListItemAttribute>)

**起始版本：** 7

<!--Device-unnamed-declare class ListItemAttribute extends CommonMethod<ListItemAttribute>--><!--Device-unnamed-declare class ListItemAttribute extends CommonMethod<ListItemAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## editable

```TypeScript
editable(value: boolean | EditMode)
```

设置当前ListItem元素是否可编辑，进入编辑模式后可删除或移动列表项。

**起始版本：** 7

**废弃版本：** 9

<!--Device-ListItemAttribute-editable(value: boolean | EditMode): ListItemAttribute--><!--Device-ListItemAttribute-editable(value: boolean | EditMode): ListItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| EditMode | 是 |  |

## onSelect

```TypeScript
onSelect(event: (isSelected: boolean) => void)
```

ListItem元素被鼠标框选的状态改变时触发回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ListItemAttribute-onSelect(event: (isSelected: boolean) => void): ListItemAttribute--><!--Device-ListItemAttribute-onSelect(event: (isSelected: boolean) => void): ListItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (isSelected: boolean) =&gt; void | 是 |  |

## selectable

```TypeScript
selectable(value: boolean)
```

设置当前ListItem元素是否可以被鼠标框选。外层List容器的鼠标框选开启时，ListItem的框选才生效。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ListItemAttribute-selectable(value: boolean): ListItemAttribute--><!--Device-ListItemAttribute-selectable(value: boolean): ListItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 |  |

## selected

```TypeScript
selected(value: boolean)
```

设置当前ListItem选中状态。该属性支持$$双向绑定变量。该属性需要在设置多态样式前使用才能生效选中态样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-ListItemAttribute-selected(value: boolean): ListItemAttribute--><!--Device-ListItemAttribute-selected(value: boolean): ListItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 当前ListItem选中状态。设置为true时为选中状态，设置为false时为默认状态。默认值：false |

## sticky

```TypeScript
sticky(value: Sticky)
```

设置ListItem吸顶效果。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** sticky

<!--Device-ListItemAttribute-sticky(value: Sticky): ListItemAttribute--><!--Device-ListItemAttribute-sticky(value: Sticky): ListItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Sticky](arkts-arkui-sticky-e.md) | 是 |  |

## swipeAction

```TypeScript
swipeAction(value: SwipeActionOptions)
```

用于设置ListItem的划出组件。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ListItemAttribute-swipeAction(value: SwipeActionOptions): ListItemAttribute--><!--Device-ListItemAttribute-swipeAction(value: SwipeActionOptions): ListItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SwipeActionOptions](arkts-arkui-swipeactionoptions-i.md) | 是 | ListItem的划出组件。 |

