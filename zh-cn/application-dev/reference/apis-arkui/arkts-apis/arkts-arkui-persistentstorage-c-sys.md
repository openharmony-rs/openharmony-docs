# PersistentStorage(System API)

PersistentStorage提供了UI状态的持久化存储能力，将选定的AppStorage属性持久化到文件中，在应用重启时从文件中恢复这些属性值并写入到AppStorage。具体UI使用说明，详见 [PersistentStorage：持久化存储UI状态](../../../ui/state-management/arkts-persiststorage.md)。 > **说明：** > > 从API version 12开始，PersistentStorage支持null、undefined。

**起始版本：** 7

<!--Device-unnamed-declare class PersistentStorage--><!--Device-unnamed-declare class PersistentStorage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(appStorage: AppStorage, storage: Storage)
```

构造函数。

**起始版本：** 7

<!--Device-PersistentStorage-constructor(appStorage: AppStorage, storage: Storage)--><!--Device-PersistentStorage-constructor(appStorage: AppStorage, storage: Storage)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appStorage | [AppStorage](arkts-arkui-appstorage-c.md) | 是 | 应用级存储对象，PersistentStorage将基于此对象进行持久化管理 |
| storage | Storage | 是 | 持久化存储对象，用于实际读写持久化数据。 |

