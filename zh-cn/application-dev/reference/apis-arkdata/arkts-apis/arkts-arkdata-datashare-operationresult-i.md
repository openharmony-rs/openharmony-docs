# OperationResult

订阅/取消订阅数据变更和发布数据的操作结果。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-dataShare-interface OperationResult--><!--Device-dataShare-interface OperationResult-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## key

```TypeScript
key: string
```

指定运算结果的键。

**类型：** string

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OperationResult-key: string--><!--Device-OperationResult-key: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## result

```TypeScript
result: int
```

指定运算结果。正常情况下返回0，异常情况下返回错误码。

**类型：** int

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OperationResult-result: int--><!--Device-OperationResult-result: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

