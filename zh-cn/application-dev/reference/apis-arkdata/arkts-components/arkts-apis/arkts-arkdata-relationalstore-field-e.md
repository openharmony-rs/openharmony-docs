# Field

用于谓词查询条件的特殊字段。请使用枚举名称而非枚举值。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

## CURSOR_FIELD

```TypeScript
CURSOR_FIELD = '#_cursor'
```

用于cursor查找的字段名。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

## ORIGIN_FIELD

```TypeScript
ORIGIN_FIELD = '#_origin'
```

用于cursor查找时指定数据来源的字段名。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

## DELETED_FLAG_FIELD

```TypeScript
DELETED_FLAG_FIELD = '#_deleted_flag'
```

用于cursor查找的结果集返回时填充的字段，表示云端删除的数据同步到本地后数据是否清理。

返回的结果集中，该字段对应的value为false表示数据未清理，true表示数据已清理。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

## DATA_STATUS_FIELD

```TypeScript
DATA_STATUS_FIELD = '#_data_status'
```

用于cursor查找的结果集返回时填充的字段，返回的结果集中，该字段对应的0表示正常数据，1表示退出账号保留数据，2表示云侧同步删除，3表示退出账户删除数据。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

## OWNER_FIELD

```TypeScript
OWNER_FIELD = '#_cloud_owner'
```

用于共享表中查找owner时，返回的结果集中填充的字段，表示当前共享记录的共享发起者。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

## PRIVILEGE_FIELD

```TypeScript
PRIVILEGE_FIELD = '#_cloud_privilege'
```

用于共享表中查找共享数据权限时，返回的结果集中填充的字段，表示当前共享记录的允许的操作权限。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

## SHARING_RESOURCE_FIELD

```TypeScript
SHARING_RESOURCE_FIELD = '#_sharing_resource_field'
```

用于数据共享查找共享数据的共享资源时，返回的结果集中填充的字段，表示共享数据的共享资源标识。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client
