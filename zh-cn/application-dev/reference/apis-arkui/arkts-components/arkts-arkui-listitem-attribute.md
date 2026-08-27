# ListItem属性/事件

除支持通用属性外，还支持以下属性：

**继承/实现关系：** ListItemAttribute extends CommonMethod<ListItemAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## editable

```TypeScript
editable(value: boolean | EditMode)
```

设置当前ListItem元素是否可编辑，进入编辑模式后可删除或移动列表项。

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| [EditMode](arkts-arkui-editmode-e.md) | 是 |  |

## onSelect

```TypeScript
onSelect(event: (isSelected: boolean) => void)
```

ListItem元素被鼠标框选的状态改变时触发回调。外层List组件设置multiSelectable为true开启鼠标框选，且当前ListItem的 [selectable](#selectable)属性为true时，触发该回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (isSelected: boolean) = & gt; void | 是 |  |

## selectable

```TypeScript
selectable(value: boolean)
```

设置当前ListItem元素是否可以被鼠标框选。外层List组件设置multiSelectable为true开启鼠标框选 时，ListItem的框选才生效。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 |  |

## selected

```TypeScript
selected(value: boolean)
```

设置当前ListItem选中状态。该属性支持[\$\$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。该属性需要在设置 多态样式前使用才能生效选中态样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 当前ListItem选中状态。设置为true时为选中状态，设置为false时为默认状态。默认值：false   **说明：** 需要在设置多态样式前使用才能生效选 中态样式。 |

## sticky

```TypeScript
sticky(value: Sticky)
```

设置ListItem吸顶效果。

> **说明：**
> 
> 从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** sticky

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

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SwipeActionOptions](arkts-arkui-swipeactionoptions-i.md) | 是 | ListItem的划出组件配置，用于设置划出时显示的组件、滑动效果和滑动状态回调等。 |
