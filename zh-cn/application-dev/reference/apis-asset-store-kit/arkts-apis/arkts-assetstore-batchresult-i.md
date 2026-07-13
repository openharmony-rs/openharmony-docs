# BatchResult

[batchAdd](arkts-assetstore-batchadd-f.md#batchadd-1)、[batchUpdate](arkts-assetstore-batchupdate-f.md#batchupdate-1)和[batchRemove](arkts-assetstore-batchremove-f.md#batchremove-1)批量操作的
结果。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Security.Asset

## failedCount

```TypeScript
failedCount: number
```

批量操作的失败数量，0表示全部成功。

**类型：** number

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Security.Asset

## failedErrorInfos

```TypeScript
failedErrorInfos: Array<BatchErrInfo>
```

批量操作中失败的关键资产的错误信息数组，全部成功时为空数组。

**类型：** Array<BatchErrInfo>

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Security.Asset

