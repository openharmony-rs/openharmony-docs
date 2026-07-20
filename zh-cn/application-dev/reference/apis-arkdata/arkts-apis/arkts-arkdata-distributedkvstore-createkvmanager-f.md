# createKVManager

## 导入模块

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

<a id="createkvmanager"></a>
## createKVManager

```TypeScript
function createKVManager(config: KVManagerConfig): KVManager
```

创建一个KVManager对象实例，用于管理数据库对象。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-distributedKVStore-function createKVManager(config: KVManagerConfig): KVManager--><!--Device-distributedKVStore-function createKVManager(config: KVManagerConfig): KVManager-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [KVManagerConfig](arkts-arkdata-distributedkvstore-kvmanagerconfig-i.md) | 是 | 提供KVManager实例的配置信息，包括应用的上下文和调用方的包名（不能为空）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [KVManager](arkts-arkdata-distributeddata-kvmanager-i.md) | 返回创建的KVManager对象实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |

**示例：**

Stage模型下的示例：

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let kvManager: distributedKVStore.KVManager;
let appId: string = 'com.example.datamanagertest';

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbilityStage onCreate');
    let context = this.context;
    const kvManagerConfig: distributedKVStore.KVManagerConfig = {
      context: context,
      bundleName: appId
    }
    try {
      kvManager = distributedKVStore.createKVManager(kvManagerConfig);
      console.info('Succeeded in creating KVManager');
    } catch (err) {
      let error = err as BusinessError;
      console.error(`Failed to create KVManager. Code: ${error.code}, message: ${error.message}`);
    }
    if (kvManager !== undefined) {
      // 进行后续创建数据库等相关操作
      // ...
    }
  }
}

```

FA模型下的示例：

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let kvManager: distributedKVStore.KVManager;
let appId: string = 'com.example.datamanagertest';
let context = featureAbility.getContext();
const kvManagerConfig: distributedKVStore.KVManagerConfig = {
  context: context,
  bundleName: appId
}
try {
  kvManager = distributedKVStore.createKVManager(kvManagerConfig);
  console.info('Succeeded in creating KVManager');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to create KVManager. Code: ${error.code}, message: ${error.message}`);
}
if (kvManager !== undefined) {
  kvManager = kvManager as distributedKVStore.KVManager;
  // 进行后续创建数据库等相关操作
  // ...
}

```

