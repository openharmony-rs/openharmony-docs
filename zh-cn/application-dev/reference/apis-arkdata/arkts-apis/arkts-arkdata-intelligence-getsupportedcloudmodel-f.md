# getSupportedCloudModel

## 导入模块

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## getSupportedCloudModel

```TypeScript
function getSupportedCloudModel(): Promise<Array<CloudModelInfo>>
```

获取支持的云侧模型信息。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-intelligence-function getSupportedCloudModel(): Promise<Array<CloudModelInfo>>--><!--Device-intelligence-function getSupportedCloudModel(): Promise<Array<CloudModelInfo>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[CloudModelInfo](arkts-arkdata-intelligence-cloudmodelinfo-i.md)&gt;&gt; | Promise对象，返回支持的云侧模型信息。 |

**示例**

```TypeScript
intelligence.getSupportedCloudModel()
  .then((info: Array<intelligence.CloudModelInfo>) => {
    console.info("Succeeded in getting CloudModelInfo");
  })
  .catch((err: BusinessError) => {
    console.error(`Failed to get CloudModelInfo. Code: ${err.code}, message: ${err.message}`);
  });
```

