# getRdbStore

## getRdbStore

```TypeScript
function getRdbStore(context: Context, config: StoreConfig, callback: AsyncCallback<RdbStore>): void
```

创建或打开已有的关系型数据库，开发者可以根据自己的需求配置config参数，然后通过RdbStore调用相关接口执行数据操作。使用callback异步回调。 对应沙箱路径下无数据库文件时，将创建数据库文件，文件创建位置详见[StoreConfig]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。对应路径下已有数据库文件时，将打开已有数据库文件。 开发者在创建数据库时，应谨慎配置是否进行数据库加密的参数[encrypt]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_，数据库创建后，禁止对该参数进行修改。 | 当前打开数据库时配置的加密类型 | 本设备上创建该数据库时的加密类型 | 结果 | | ------- | -------------------------------- | ---- | | 非加密 | 加密 | 使用加密配置（encrypt=true）打开数据库。 | | 加密 | 非加密 | 使用非加密配置（encrypt=false）打开数据库。 | getRdbStore支持多线程并发操作。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-relationalStore-function getRdbStore(context: Context, config: StoreConfig, callback: AsyncCallback<RdbStore>): void--><!--Device-relationalStore-function getRdbStore(context: Context, config: StoreConfig, callback: AsyncCallback<RdbStore>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 应用的上下文。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_FA模型的应用Context定义见[Context]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Stage模型的应用Context定义见[Context]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| config | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 与此RDB存储相关的数据库配置。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;RdbStore&gt; | 是 | 回调函数。当获取RdbStore成功，err为undefined，data为RdbStore对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error. |
| [14800010](../../apis-basic-services-kit/errorcode-settings.md#14800010-上下文参数不是uiability类型) | Failed to open or delete the database by an invalid database path. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14801001](../errorcode-data-rdb.md#14801001-上下文环境非stage模型) | The operation is supported in the stage model only.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 10+ |
| [14801002](../errorcode-data-rdb.md#14801002-storeconfig中传入的datagroupid参数非法) | Invalid data group ID.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 10+ |
| [14800017](../errorcode-data-rdb.md#14800017-关键配置已被更改) | StoreConfig is changed.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800020](../errorcode-data-rdb.md#14800020-密钥损坏或丢失) | The secret key is corrupted or lost.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 14+ |

**示例：**

FA模型示例：

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let store: relationalStore.RdbStore | undefined = undefined;
let context = featureAbility.getContext();

const STORE_CONFIG: relationalStore.StoreConfig = {
  name: "RdbTest.db",
  securityLevel: relationalStore.SecurityLevel.S3
};

relationalStore.getRdbStore(context, STORE_CONFIG, (err, rdbStore) => {
  if (err) {
    console.error(`Get RdbStore failed, code is ${err.code},message is ${err.message}`);
    return;
  }
  console.info('Get RdbStore successfully.');
  store = rdbStore;
  // 成功获取到 rdbStore 后执行后续操作
});
```

Stage模型示例：

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let store: relationalStore.RdbStore | undefined = undefined;

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    const STORE_CONFIG: relationalStore.StoreConfig = {
      name: "RdbTest.db",
      securityLevel: relationalStore.SecurityLevel.S3
    };

    relationalStore.getRdbStore(this.context, STORE_CONFIG, (err, rdbStore) => {
      if (err) {
        console.error(`Get RdbStore failed, code is ${err.code},message is ${err.message}`);
        return;
      }
      console.info('Get RdbStore successfully.');
      store = rdbStore;
      // 成功获取到 rdbStore 后执行后续操作
    });
  }
}
```


## getRdbStore

```TypeScript
function getRdbStore(context: Context, config: StoreConfig): Promise<RdbStore>
```

创建或打开已有的关系型数据库，开发者可以根据自己的需求配置config参数，然后通过RdbStore调用相关接口执行数据操作。使用Promise异步回调。 对应沙箱路径下无数据库文件时，将创建数据库文件，文件创建位置详见[StoreConfig]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。对应路径下已有数据库文件时，将打开已有数据库文件。 开发者在创建数据库时，应谨慎配置是否进行数据库加密的参数[encrypt]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_，数据库创建后，禁止对该参数进行修改。 | 当前打开数据库时配置的加密类型 | 本设备上创建该数据库时的加密类型 | 结果 | | ------- | -------------------------------- | ---- | | 非加密 | 加密 | 使用加密配置（encrypt=true）打开数据库。 | | 加密 | 非加密 | 使用非加密配置（encrypt=false）打开数据库。 | getRdbStore支持多线程并发操作。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-relationalStore-function getRdbStore(context: Context, config: StoreConfig): Promise<RdbStore>--><!--Device-relationalStore-function getRdbStore(context: Context, config: StoreConfig): Promise<RdbStore>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 应用的上下文。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_FA模型的应用Context定义见[Context]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Stage模型的应用Context定义见[Context]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| config | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 与此RDB存储相关的数据库配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RdbStore&gt; | Promise对象。返回RdbStore对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error. |
| [14800010](../../apis-basic-services-kit/errorcode-settings.md#14800010-上下文参数不是uiability类型) | Failed to open or delete the database by an invalid database path. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14801001](../errorcode-data-rdb.md#14801001-上下文环境非stage模型) | The operation is supported in the stage model only.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 10+ |
| [14801002](../errorcode-data-rdb.md#14801002-storeconfig中传入的datagroupid参数非法) | Invalid data group ID.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 10+ |
| [14800017](../errorcode-data-rdb.md#14800017-关键配置已被更改) | StoreConfig is changed.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800020](../errorcode-data-rdb.md#14800020-密钥损坏或丢失) | The secret key is corrupted or lost.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 14+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 14+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 14+ |

**示例：**

FA模型示例：

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let store: relationalStore.RdbStore | undefined = undefined;
let context = featureAbility.getContext();

const STORE_CONFIG: relationalStore.StoreConfig = {
  name: "RdbTest.db",
  securityLevel: relationalStore.SecurityLevel.S3
};

relationalStore.getRdbStore(context, STORE_CONFIG).then(async (rdbStore: relationalStore.RdbStore) => {
  store = rdbStore;
  console.info('Get RdbStore successfully.');
}).catch((err: Error) => {
  let businessError = err as BusinessError;
  console.error(`Get RdbStore failed, code is ${businessError.code},message is ${businessError.message}`);
});
```

Stage模型示例：

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let store: relationalStore.RdbStore | undefined = undefined;

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    const STORE_CONFIG: relationalStore.StoreConfig = {
      name: "RdbTest.db",
      securityLevel: relationalStore.SecurityLevel.S3
    };

    relationalStore.getRdbStore(this.context, STORE_CONFIG).then(async (rdbStore: relationalStore.RdbStore) => {
      store = rdbStore;
      console.info('Get RdbStore successfully.');
    }).catch((err: Error) => {
      let businessError = err as BusinessError;
      console.error(`Get RdbStore failed, code is ${businessError.code},message is ${businessError.message}`);
    });
  }
}
```

