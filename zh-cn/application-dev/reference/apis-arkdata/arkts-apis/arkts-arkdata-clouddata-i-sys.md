# CloudData（系统接口）

云数据。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## hasMore

```TypeScript
hasMore: boolean
```

服务器是否存在更多数据可供查询。true表示服务器上还有数据等待查询，false表示服务器上不存在可查询的数据。

**类型：** boolean

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## nextCursor

```TypeScript
nextCursor: string
```

查询游标。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## values

```TypeScript
values: Array<Record<string, CloudType>>
```

需要查询数据的数组，包括数据记录的实际值和ExtensionValue（扩展值）。

**类型：** Array<Record<string, CloudType>>

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

