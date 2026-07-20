# VisibleListContentInfo

用于表示List可见内容区子组件的详细信息。

**起始版本：** 12

<!--Device-unnamed-declare interface VisibleListContentInfo--><!--Device-unnamed-declare interface VisibleListContentInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

Index of the list item or list item group in the list display area.

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-VisibleListContentInfo-index: number--><!--Device-VisibleListContentInfo-index: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemGroupArea

```TypeScript
itemGroupArea?: ListItemGroupArea
```

Position of the top or bottom edge of the viewport in the list item group to which the edge is located, if applicable.

**类型：** ListItemGroupArea

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-VisibleListContentInfo-itemGroupArea?: ListItemGroupArea--><!--Device-VisibleListContentInfo-itemGroupArea?: ListItemGroupArea-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## itemIndexInGroup

```TypeScript
itemIndexInGroup?: number
```

Index of the starting or ending list item in the list item group to which the top or bottom edge of the viewport is located.

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-VisibleListContentInfo-itemIndexInGroup?: number--><!--Device-VisibleListContentInfo-itemIndexInGroup?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

