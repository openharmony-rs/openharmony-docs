# PersistentStorage

PersistentStorage具体UI使用说明，详见[PersistentStorage(持久化存储UI状态)](../../../../ui/state-management/arkts-persiststorage.md)

> **说明：**

> 从API version 12开始，PersistentStorage支持null、undefined。

**起始版本：** 7

<!--Device-unnamed-declare class PersistentStorage--><!--Device-unnamed-declare class PersistentStorage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(appStorage: AppStorage, storage: Storage)
```

构造函数参数。

**起始版本：** 7

<!--Device-PersistentStorage-constructor(appStorage: AppStorage, storage: Storage)--><!--Device-PersistentStorage-constructor(appStorage: AppStorage, storage: Storage)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appStorage | [AppStorage](arkts-arkui-common-ts-ets-api-appstorage-c.md) | 是 | 应用存储。 |
| storage | [Storage](../../apis-arkdata/arkts-apis/arkts-arkdata-storage-storage-c.md) | 是 | 存储。 |

