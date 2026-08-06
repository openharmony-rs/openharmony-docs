# SystemDefinedRecord

SystemDefinedRecord是[UnifiedRecord]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的子类，也是OpenHarmony系统特有数据类型的基类，用于描述仅在 OpenHarmony系统范围内流通的特有数据类型，推荐开发者优先使用SystemDefinedRecord的子类描述数据，如 [SystemDefinedForm]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_、 [SystemDefinedAppItem]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_、 [SystemDefinedPixelMap]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_等具体子类。

**继承/实现关系：** SystemDefinedRecord extends [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md)

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-unifiedDataChannel-class SystemDefinedRecord extends UnifiedRecord--><!--Device-unifiedDataChannel-class SystemDefinedRecord extends UnifiedRecord-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## details

```TypeScript
details?: Record<string, int | long | double | string | Uint8Array>
```

是一个字典类型对象，key是string类型，value可以写入number（数值类型）、string（字符串类型）、Uint8Array（二进制字节数组）类型数据。非必填字段，默认值为空字典对象。

**类型：** Record&lt;string, int \| long \| double \| string \| Uint8Array&gt;

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SystemDefinedRecord-details?: Record<string, int | long | double | string | Uint8Array>--><!--Device-SystemDefinedRecord-details?: Record<string, int | long | double | string | Uint8Array>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

