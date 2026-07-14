# Options

Preferences实例配置选项。

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

## dataGroupId

```TypeScript
dataGroupId?: string | null
```

应用组ID，<!--RP1-->暂不支持指定dataGroupId在对应共享沙箱路径下创建Preferences实例。<!--RP1End-->

为可选参数。指定在此dataGroupId对应的沙箱路径下创建Preferences实例。当此参数不填时，默认在本应用沙箱目录下创建Preferences实例。

**模型约束：** 此属性仅在Stage模型下可用。

**类型：** string | null

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

## name

```TypeScript
name: string
```

Preferences实例的名称。名称长度需大于零且小于等于255字节，名称中不能包含'/'且不能以'/'结尾。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

