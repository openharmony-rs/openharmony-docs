# DataSetSize

```TypeScript
enum DataSetSize
```

枚举隐私协议支持的数据集大小。数据集大小定义单个结果密文可以包含的比较次数。的总数生成的结果密文由elements.size/dataSetSize决定。选择一个根据隐私搜索中元素的数量和可接受的每个结果密文的大小。

**起始版本：** 26.0.1

<!--Device-privacyComputation-enum DataSetSize--><!--Device-privacyComputation-enum DataSetSize-End-->

**系统能力：** SystemCapability.Security.Asset

## SIZE_128

```TypeScript
SIZE_128 = 0
```

单个结果密文可以包含128次比较。

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-DataSetSize-SIZE_128 = 0--><!--Device-DataSetSize-SIZE_128 = 0-End-->

**系统能力：** SystemCapability.Security.Asset

## SIZE_256

```TypeScript
SIZE_256 = 1
```

单个结果密文可以包含256次比较。

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-DataSetSize-SIZE_256 = 1--><!--Device-DataSetSize-SIZE_256 = 1-End-->

**系统能力：** SystemCapability.Security.Asset

## SIZE_512

```TypeScript
SIZE_512 = 2
```

单个结果密文可以包含512次比较。

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-DataSetSize-SIZE_512 = 2--><!--Device-DataSetSize-SIZE_512 = 2-End-->

**系统能力：** SystemCapability.Security.Asset
