# SyncResult

关键资产同步的结果。

**起始版本：** 20

**系统能力：** SystemCapability.Security.Asset

## failedCount

```TypeScript
readonly failedCount?: number
```

关键资产同步失败的数量。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Security.Asset

## resultCode

```TypeScript
readonly resultCode: number
```

关键资产同步的结果码。同步成功时结果码为0，同步失败时结果码参考[ErrorCode](arkts-assetstore-errorcode-e.md)。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Security.Asset

## totalCount

```TypeScript
readonly totalCount?: number
```

触发同步的关键资产总数。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Security.Asset

