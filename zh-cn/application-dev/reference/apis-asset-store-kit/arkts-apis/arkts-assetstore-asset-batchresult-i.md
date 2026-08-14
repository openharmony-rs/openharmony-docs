# BatchResult

[batchAdd](arkts-assetstore-asset-batchadd-f.md#batchAdd)、[batchUpdate](arkts-assetstore-asset-batchupdate-f.md#batchUpdate)和[batchRemove](arkts-assetstore-asset-batchremove-f.md#batchRemove)批量操作的 结果。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-asset-interface BatchResult--><!--Device-asset-interface BatchResult-End-->

**系统能力：** SystemCapability.Security.Asset

## failedCount

```TypeScript
failedCount: number
```

批量操作的失败数量，0表示全部成功。

**类型：** number

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-BatchResult-failedCount: number--><!--Device-BatchResult-failedCount: number-End-->

**系统能力：** SystemCapability.Security.Asset

## failedErrorInfos

```TypeScript
failedErrorInfos: Array<BatchErrInfo>
```

批量操作中失败的关键资产的错误信息数组，全部成功时为空数组。

**类型：** Array&lt;[BatchErrInfo](arkts-assetstore-asset-batcherrinfo-i.md)&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-BatchResult-failedErrorInfos: Array<BatchErrInfo>--><!--Device-BatchResult-failedErrorInfos: Array<BatchErrInfo>-End-->

**系统能力：** SystemCapability.Security.Asset

