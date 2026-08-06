# BatchResult

[batchAdd]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_、[batchUpdate]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_和[batchRemove]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_批量操作的 结果。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

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

<!--Device-BatchResult-failedCount: number--><!--Device-BatchResult-failedCount: number-End-->

**系统能力：** SystemCapability.Security.Asset

## failedErrorInfos

```TypeScript
failedErrorInfos: Array<BatchErrInfo>
```

批量操作中失败的关键资产的错误信息数组，全部成功时为空数组。

**类型：** Array&lt;BatchErrInfo&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

<!--Device-BatchResult-failedErrorInfos: Array<BatchErrInfo>--><!--Device-BatchResult-failedErrorInfos: Array<BatchErrInfo>-End-->

**系统能力：** SystemCapability.Security.Asset

