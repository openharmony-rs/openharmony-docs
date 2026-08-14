# getRdbStore

## getRdbStore

```TypeScript
function getRdbStore(context: Context, config: StoreConfig, callback: AsyncCallback<RdbStore>): void
```

创建或打开已有的关系型数据库，开发者可以根据自己的需求配置config参数，然后通过RdbStore调用相关接口执行数据操作。使用callback异步回调。 对应沙箱路径下无数据库文件时，将创建数据库文件，文件创建位置详见[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md#StoreConfig)。对应路径下已有数据库文件时，将打开已有数据库文件。 开发者在创建数据库时，应谨慎配置是否进行数据库加密的参数[encrypt](arkts-arkdata-relationalstore-storeconfig-i.md#StoreConfig)，数据库创建后，禁止对该参数进行修改。 | 当前打开数据库时配置的加密类型 | 本设备上创建该数据库时的加密类型 | 结果 | | ------- | -------------------------------- | ---- | | 非加密 | 加密 | 使用加密配置（encrypt=true）打开数据库。 | | 加密 | 非加密 | 使用非加密配置（encrypt=false）打开数据库。 | getRdbStore支持多线程并发操作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-relationalStore-function getRdbStore(context: Context, config: StoreConfig, callback: AsyncCallback<RdbStore>): void--><!--Device-relationalStore-function getRdbStore(context: Context, config: StoreConfig, callback: AsyncCallback<RdbStore>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用的上下文。 &lt;br&gt;FA模型的应用Context定义见Context。 &lt;br&gt;Stage模型的应用Context定义见Context。 |
| config | StoreConfig | 是 | 与此RDB存储相关的数据库配置。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;RdbStore&gt; | 是 | 回调函数。当获取RdbStore成功，err为undefined，data为RdbStore对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14801001](../errorcode-data-rdb.md#14801001-上下文环境非stage模型) | The operation is supported in the stage model only.<br>**适用版本：** 10+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800010](../errorcode-data-rdb.md#14800010-数据库路径不合法) | Failed to open or delete the database by an invalid database path. |
| [14801002](../errorcode-data-rdb.md#14801002-storeconfig中传入的datagroupid参数非法) | Invalid data group ID.<br>**适用版本：** 10+ |
| [14800017](../errorcode-data-rdb.md#14800017-关键配置已被更改) | StoreConfig is changed.<br>**适用版本：** 12+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.<br>**适用版本：** 12+ |
| [14800020](../errorcode-data-rdb.md#14800020-密钥损坏或丢失) | The secret key is corrupted or lost.<br>**适用版本：** 14+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |

## 示例

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

创建或打开已有的关系型数据库，开发者可以根据自己的需求配置config参数，然后通过RdbStore调用相关接口执行数据操作。使用Promise异步回调。 对应沙箱路径下无数据库文件时，将创建数据库文件，文件创建位置详见[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md#StoreConfig)。对应路径下已有数据库文件时，将打开已有数据库文件。 开发者在创建数据库时，应谨慎配置是否进行数据库加密的参数[encrypt](arkts-arkdata-relationalstore-storeconfig-i.md#StoreConfig)，数据库创建后，禁止对该参数进行修改。 | 当前打开数据库时配置的加密类型 | 本设备上创建该数据库时的加密类型 | 结果 | | ------- | -------------------------------- | ---- | | 非加密 | 加密 | 使用加密配置（encrypt=true）打开数据库。 | | 加密 | 非加密 | 使用非加密配置（encrypt=false）打开数据库。 | getRdbStore支持多线程并发操作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-relationalStore-function getRdbStore(context: Context, config: StoreConfig): Promise<RdbStore>--><!--Device-relationalStore-function getRdbStore(context: Context, config: StoreConfig): Promise<RdbStore>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用的上下文。 &lt;br&gt;FA模型的应用Context定义见Context。 &lt;br&gt;Stage模型的应用Context定义见Context。 |
| config | StoreConfig | 是 | 与此RDB存储相关的数据库配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RdbStore&gt; | Promise对象。返回RdbStore对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14801001](../errorcode-data-rdb.md#14801001-上下文环境非stage模型) | The operation is supported in the stage model only.<br>**适用版本：** 10+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800010](../errorcode-data-rdb.md#14800010-数据库路径不合法) | Failed to open or delete the database by an invalid database path. |
| [14801002](../errorcode-data-rdb.md#14801002-storeconfig中传入的datagroupid参数非法) | Invalid data group ID.<br>**适用版本：** 10+ |
| [14800017](../errorcode-data-rdb.md#14800017-关键配置已被更改) | StoreConfig is changed.<br>**适用版本：** 12+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.<br>**适用版本：** 12+ |
| [14800020](../errorcode-data-rdb.md#14800020-密钥损坏或丢失) | The secret key is corrupted or lost.<br>**适用版本：** 14+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.<br>**适用版本：** 14+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.<br>**适用版本：** 14+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.<br>**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.<br>**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.<br>**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.<br>**适用版本：** 12+ |

## 示例

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

