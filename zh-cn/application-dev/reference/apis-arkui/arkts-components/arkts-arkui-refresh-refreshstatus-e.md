# RefreshStatus

RefreshStatus刷新状态枚举。

**起始版本：** 8

<!--Device-unnamed-declare enum RefreshStatus--><!--Device-unnamed-declare enum RefreshStatus-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Inactive

```TypeScript
Inactive
```

默认未下拉状态。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RefreshStatus-Inactive--><!--Device-RefreshStatus-Inactive-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Drag

```TypeScript
Drag
```

下拉中，下拉距离小于刷新距离。

若此时松手，组件进入Inactive状态；若此时继续下拉使下拉距离超过刷新距离，组件进入OverDrag状态。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RefreshStatus-Drag--><!--Device-RefreshStatus-Drag-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## OverDrag

```TypeScript
OverDrag
```

下拉中，下拉距离超过刷新距离。

若此时松手，组件进入Refresh状态；若此时上滑使下拉距离小于刷新距离，组件进入Drag状态。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RefreshStatus-OverDrag--><!--Device-RefreshStatus-OverDrag-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Refresh

```TypeScript
Refresh
```

After the pull-down, it rebounds to the refresh distance and enters the refresh state.

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RefreshStatus-Refresh--><!--Device-RefreshStatus-Refresh-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Done

```TypeScript
Done
```

刷新结束，返回初始状态（顶部）。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RefreshStatus-Done--><!--Device-RefreshStatus-Done-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

