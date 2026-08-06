# DataProxyConfig

数据代理操作配置的数据结构。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-dataShare-interface DataProxyConfig--><!--Device-dataShare-interface DataProxyConfig-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## maxValueLength

```TypeScript
maxValueLength?: DataProxyMaxValueLength
```

设置共享配置的值允许的最大长度。如果未填写，默认为MAX\_LENGTH\_4K，即共享配置的值允许的最大长度为4096字节。

**类型：** DataProxyMaxValueLength

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataProxyConfig-maxValueLength?: DataProxyMaxValueLength--><!--Device-DataProxyConfig-maxValueLength?: DataProxyMaxValueLength-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## type

```TypeScript
type: DataProxyType
```

数据代理操作的类型。

**类型：** DataProxyType

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataProxyConfig-type: DataProxyType--><!--Device-DataProxyConfig-type: DataProxyType-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

