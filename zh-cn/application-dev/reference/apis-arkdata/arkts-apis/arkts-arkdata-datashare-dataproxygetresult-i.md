# DataProxyGetResult

配置共享批量获取操作结果的数据结构。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-dataShare-interface DataProxyGetResult--><!--Device-dataShare-interface DataProxyGetResult-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## allowList

```TypeScript
allowList: string[] | undefined
```

如果获取操作成功，则为共享配置的允许列表；如果获取操作失败，则未定义。只有发布者才能获取允许列表，其他应用只能获取值。

**类型：** string[] \| undefined

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataProxyGetResult-allowList: string[] | undefined--><!--Device-DataProxyGetResult-allowList: string[] | undefined-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## result

```TypeScript
result: DataProxyErrorCode
```

操作结果的错误码。

**类型：** DataProxyErrorCode

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataProxyGetResult-result: DataProxyErrorCode--><!--Device-DataProxyGetResult-result: DataProxyErrorCode-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## uri

```TypeScript
uri: string
```

被操作的URI。固定格式为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_，其中bundleName为配置发布方应用的bundleName，path可随意填写，但同一应用内不允许重复，字符串长度 不超过256个字节。

**类型：** string

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataProxyGetResult-uri: string--><!--Device-DataProxyGetResult-uri: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## value

```TypeScript
value: ValueType | undefined
```

如果获取操作成功，则为共享配置的值；如果获取操作失败，则未定义。

**类型：** ValueType \| undefined

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataProxyGetResult-value: ValueType | undefined--><!--Device-DataProxyGetResult-value: ValueType | undefined-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

