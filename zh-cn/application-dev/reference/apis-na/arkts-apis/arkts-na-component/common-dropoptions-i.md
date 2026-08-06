# DropOptions

Defines the options for the drop handling.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface DropOptions--><!--Device-unnamed-export declare interface DropOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## disableDataPrefetch

```TypeScript
disableDataPrefetch?: boolean
```

Indicating to disable the UDMF data prefetch action by system or not. The system will try to fetch data before calling user's onDrop for some situation, it will retry to get data until the max time limit (2.4s for now) reaches, this's useful for the cross device draging operation, as the system helps to eliminate the communication instability, but it's redundant for startDataLoading method, as this method will take care the data fetching with asynchronous mechanism, so must set this field to true if using startDataLoading in onDrop to avoid the data is fetched before onDrop executing unexpectedly.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DropOptions-disableDataPrefetch?: boolean--><!--Device-DropOptions-disableDataPrefetch?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

