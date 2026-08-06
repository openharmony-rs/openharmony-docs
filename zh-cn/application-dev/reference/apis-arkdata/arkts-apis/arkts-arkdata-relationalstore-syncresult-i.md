# SyncResult

表示设备同步结果。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-relationalStore-interface SyncResult--><!--Device-relationalStore-interface SyncResult-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## code

```TypeScript
readonly code:SyncResultCode
```

表示同步结果的状态码。

**类型：** SyncResultCode

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SyncResult-readonly code:SyncResultCode--><!--Device-SyncResult-readonly code:SyncResultCode-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## device

```TypeScript
readonly device:string
```

表示同步的设备ID，可通过 [getAvailableDeviceListSync]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 等接口获取所有可信设备ID列表。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SyncResult-readonly device:string--><!--Device-SyncResult-readonly device:string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## message

```TypeScript
readonly message:string
```

表示同步结果的信息。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SyncResult-readonly message:string--><!--Device-SyncResult-readonly message:string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

