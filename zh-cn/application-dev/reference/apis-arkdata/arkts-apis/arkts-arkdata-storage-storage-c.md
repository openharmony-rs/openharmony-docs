# Storage

**起始版本：** 3

**废弃版本：** 6

<!--Device-unnamed-export default class Storage--><!--Device-unnamed-export default class Storage-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

## clear

```TypeScript
static clear(options?: ClearStorageOptions): void
```

清空缓存中存储的键值对。

**起始版本：** 3

**废弃版本：** 6

**替代接口：** clear

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Storage-static clear(options?: ClearStorageOptions): void--><!--Device-Storage-static clear(options?: ClearStorageOptions): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ClearStorageOptions](arkts-arkdata-storage-clearstorageoptions-i.md) | 否 | Indicates the target options. |

## delete

```TypeScript
static delete(options: DeleteStorageOptions): void
```

删除缓存中索引对应的键值对。

**起始版本：** 3

**废弃版本：** 6

**替代接口：** delete

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Storage-static delete(options: DeleteStorageOptions): void--><!--Device-Storage-static delete(options: DeleteStorageOptions): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DeleteStorageOptions](arkts-arkdata-storage-deletestorageoptions-i.md) | 是 | Indicates the target options. |

## get

```TypeScript
static get(options: GetStorageOptions): void
```

通过索引读取缓存中存储的值。

**起始版本：** 3

**废弃版本：** 6

**替代接口：** get

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Storage-static get(options: GetStorageOptions): void--><!--Device-Storage-static get(options: GetStorageOptions): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [GetStorageOptions](arkts-arkdata-storage-getstorageoptions-i.md) | 是 | Indicates the target options. |

## set

```TypeScript
static set(options: SetStorageOptions): void
```

修改缓存中索引对应的值。

**起始版本：** 3

**废弃版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-Storage-static set(options: SetStorageOptions): void--><!--Device-Storage-static set(options: SetStorageOptions): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SetStorageOptions](arkts-arkdata-storage-setstorageoptions-i.md) | 是 | Indicates the target options. |

