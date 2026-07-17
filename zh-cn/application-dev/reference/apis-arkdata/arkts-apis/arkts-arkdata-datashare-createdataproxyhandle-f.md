# createDataProxyHandle

## 导入模块

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## createDataProxyHandle

```TypeScript
function createDataProxyHandle(): Promise<DataProxyHandle>
```

创建DataProxyHandle实例。使用Promise异步回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-dataShare-function createDataProxyHandle(): Promise<DataProxyHandle>--><!--Device-dataShare-function createDataProxyHandle(): Promise<DataProxyHandle>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<DataProxyHandle> | Promise对象。返回DataProxyHandle实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15700000](../errorcode-datashare.md#15700000-内部错误) | Inner error. Possible causes: The service is not ready or is being restarted abnormally. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    dataShare.createDataProxyHandle().then((dataProxyHandle) => {
      console.info("createDataProxyHandle succeed");
    }).catch((err: BusinessError) => {
      console.error(`Failed to create DataProxyHandle. Code: ${err.code}, message: ${err.message}`);
    });
  }
}

```

