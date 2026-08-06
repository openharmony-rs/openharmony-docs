# SystemDefinedPixelMap

与系统侧定义的[PixelMap]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_数据类型对应的图片数据类型，是 [SystemDefinedRecord]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_的子类，仅保存PixelMap的二进制数据。

**继承/实现关系：** SystemDefinedPixelMap extends [SystemDefinedRecord](arkts-arkdata-unifieddatachannel-systemdefinedrecord-c.md)

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-unifiedDataChannel-class SystemDefinedPixelMap extends SystemDefinedRecord--><!--Device-unifiedDataChannel-class SystemDefinedPixelMap extends SystemDefinedRecord-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## rawData

```TypeScript
set rawData(value: Uint8Array)
```

PixelMap对象的二进制数据。

**类型：** Uint8Array

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SystemDefinedPixelMap-set rawData(value: Uint8Array)--><!--Device-SystemDefinedPixelMap-set rawData(value: Uint8Array)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

