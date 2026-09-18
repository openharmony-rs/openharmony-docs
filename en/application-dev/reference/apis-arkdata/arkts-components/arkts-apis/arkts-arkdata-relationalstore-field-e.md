# Field

Enumerates predicates used as query conditions. Use the enum name rather than the enum value.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

## CURSOR_FIELD

```TypeScript
CURSOR_FIELD = '#_cursor'
```

Field name used for cursor-based search.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

## ORIGIN_FIELD

```TypeScript
ORIGIN_FIELD = '#_origin'
```

Field name used to specify the data source in cursor-based search.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

## DELETED_FLAG_FIELD

```TypeScript
DELETED_FLAG_FIELD = '#_deleted_flag'
```

Whether the dirty data (data deleted from the cloud) is cleared from the local device. It fills in the result set returned upon the cursor-based search.

The value **true** means the dirty data is cleared; the value **false** means the opposite.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

## DATA_STATUS_FIELD

```TypeScript
DATA_STATUS_FIELD = '#_data_status'
```

Data status in the cursor-based search result set. The value **0** indicates normal data status; **1** indicates that data is retained after the account is logged out; **2** indicates that data is deleted from the cloud; **3** indicates that data is deleted after the account is logged out.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

## OWNER_FIELD

```TypeScript
OWNER_FIELD = '#_cloud_owner'
```

Party who shares the data. It fills in the result set returned when the owner of the shared data is searched.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

## PRIVILEGE_FIELD

```TypeScript
PRIVILEGE_FIELD = '#_cloud_privilege'
```

Operation permission on the shared data. It fills in the result set returned when the permission on the shared data is searched.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

## SHARING_RESOURCE_FIELD

```TypeScript
SHARING_RESOURCE_FIELD = '#_sharing_resource_field'
```

Resource shared. It fills in the result set returned when the shared resource is searched.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client
