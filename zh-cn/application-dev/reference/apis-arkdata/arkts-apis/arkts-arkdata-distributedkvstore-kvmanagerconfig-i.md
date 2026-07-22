# KVManagerConfig

提供KVManager实例的配置信息，包括调用方的包名和应用的上下文。

**起始版本：** 9

<!--Device-distributedKVStore-interface KVManagerConfig--><!--Device-distributedKVStore-interface KVManagerConfig-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## 导入模块

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

## bundleName

```TypeScript
bundleName: string
```

调用方的包名，不可为空且长度范围为1-256字节。

**类型：** string

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVManagerConfig-bundleName: string--><!--Device-KVManagerConfig-bundleName: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## context

```TypeScript
context: BaseContext
```

应用的上下文。

FA模型的应用Context定义见[Context](arkts-arkdata-distributedkvstore-kvmanagerconfig-i.md#context)。

Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md)。

从API version 10开始，context的参数类型为[BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md)。

**类型：** BaseContext

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVManagerConfig-context: BaseContext--><!--Device-KVManagerConfig-context: BaseContext-End-->

**系统能力：** 
- API版本10+：SystemCapability.DistributedDataManager.KVStore.Core if swap the area, you should close all the KV store and use the new BaseContext to create the KVManager
- API版本9：SystemCapability.DistributedDataManager.KVStore.Core if swap the area, you should close all the KV store and use the new Context to create the KVManager

