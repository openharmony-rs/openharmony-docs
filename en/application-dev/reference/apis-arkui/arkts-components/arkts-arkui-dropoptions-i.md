# DropOptions

Sets parameters for the drop process.

**Since:** 15

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## disableDataPrefetch

```TypeScript
disableDataPrefetch?: boolean
```

Whether to disable data prefetching for the drag-and-drop operation. The value **true** means to disable data prefetching for the drag-and-drop operation, and **false** means the opposite. Default value: **false**.

**NOTE:** 

Set this parameter to **true** when using [startDataLoading](arkts-arkui-dragevent-i.md#startdataloading) to enable data prefetching.

**Type:** boolean

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
