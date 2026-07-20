# Options

Preferences实例配置选项。

**起始版本：** 10

<!--Device-preferences-interface Options--><!--Device-preferences-interface Options-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

## 导入模块

```TypeScript
import { preferences } from '@kit.ArkData';
```

## dataGroupId

```TypeScript
dataGroupId?: string | null | undefined
```

应用组ID，<!--RP1-->暂不支持指定dataGroupId在对应共享沙箱路径下创建Preferences实例。<!--RP1End-->

为可选参数。指定在此dataGroupId对应的沙箱路径下创建Preferences实例。当此参数不填时，默认在本应用沙箱目录下创建Preferences实例。

**模型约束：** 此属性仅在Stage模型下可用。

**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。

**类型：** string \| null \| undefined

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Options-dataGroupId?: string | null | undefined--><!--Device-Options-dataGroupId?: string | null | undefined-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

## name

```TypeScript
name: string
```

Preferences实例的名称。名称长度需大于零且小于等于255字节，名称中不能包含'/'且不能以'/'结尾。

**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Options-name: string--><!--Device-Options-name: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

## storageType

```TypeScript
storageType?: StorageType | null | undefined
```

存储模式，为可选参数。表示当前Preferences实例需要使用的存储模式。当此参数不填时，默认使用XML存储模式。当选择某种存储模式创建Preferences后，不支持中途切换存储模式。

**原子化服务API：** 从API version 18开始，该参数支持在原子化服务中使用。

**类型：** StorageType \| null \| undefined

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Options-storageType?: StorageType | null | undefined--><!--Device-Options-storageType?: StorageType | null | undefined-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

