# DropOptions

设置落入过程的参数。

**起始版本：** 15

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## disableDataPrefetch

```TypeScript
disableDataPrefetch?: boolean
```

设置拖拽是否提前获取数据。true表示不提前获取数据，false表示提前获取数据，默认值为false。

**说明：**

当使用[startDataLoading](arkts-arkui-dragevent-i.md#startdataloading-1)获取数据时需设置该参数为true，防止拖拽提前获取数据。

**类型：** boolean

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

