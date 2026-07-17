# ContactSyncMode

同步模式的类型。

**起始版本：** 26.0.0

<!--Device-contact-enum ContactSyncMode--><!--Device-contact-enum ContactSyncMode-End-->

**系统能力：** SystemCapability.Applications.ContactsData

## MODE_INCREMENTAL

```TypeScript
MODE_INCREMENTAL = 1
```

表示将在数据库中插入或更新云端和本地之间不同的联系人。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContactSyncMode-MODE_INCREMENTAL = 1--><!--Device-ContactSyncMode-MODE_INCREMENTAL = 1-End-->

**系统能力：** SystemCapability.Applications.ContactsData

## MODE_CLOUD_BASED

```TypeScript
MODE_CLOUD_BASED = 2
```

表示所有本地联系人将被云联系人替换。

当使用云覆盖本地模式进行批量同步时，在第一次批量同步期间会删除所有本地联系人（第三方联系人除外）。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContactSyncMode-MODE_CLOUD_BASED = 2--><!--Device-ContactSyncMode-MODE_CLOUD_BASED = 2-End-->

**系统能力：** SystemCapability.Applications.ContactsData

