# @ohos.data.rdb (关系型数据库)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @widecode; @htt1997-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

关系型数据库（Relational Database，RDB）是一种基于关系模型来管理数据的数据库。关系型数据库基于SQLite组件提供了一套完整的对本地数据库进行管理的机制，对外提供了一系列的增、删、改、查等接口，也可以直接运行用户输入的SQL语句来满足复杂的场景需要。不支持Worker线程。

该模块提供以下关系型数据库相关的常用功能：

- [RdbPredicates](#rdbpredicates)：数据库中用来代表数据实体的性质、特征或者数据实体之间关系的词项，主要用来定义数据库的操作条件。
- [RdbStore](#rdbstore)：提供管理关系数据库（RDB）方法的接口。

> **说明：**
>
> - 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 
> - 从API version 9开始，该接口不再维护，推荐使用新接口[@ohos.data.relationalStore](arkts-apis-data-relationalStore.md)。


## 导入模块

```ts
import data_rdb from '@ohos.data.rdb';
```
## data_rdb.getRdbStore

getRdbStore(context: Context, config: StoreConfig, version: number, callback: AsyncCallback&lt;RdbStore&gt;): void

获得一个相关的RdbStore，操作关系型数据库，用户可以根据自己的需求配置RdbStore的参数，然后通过RdbStore调用相关接口可以执行相关的数据操作，使用callback异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名   | 类型                                       | 必填 | 说明                                                         |
| -------- | ------------------------------------------ | ---- | ------------------------------------------------------------ |
| context  | Context                                    | 是   | 应用的上下文。<br>FA模型的应用Context定义见[Context](../apis-ability-kit/js-apis-inner-app-context.md)。<br>Stage模型的应用Context定义见[Context](../apis-ability-kit/js-apis-inner-app-context.md)。 |
| config   | [StoreConfig](#storeconfig)                | 是   | 与此RDB存储相关的数据库配置。                                |
| version  | number                                     | 是   | 数据库版本。<br>目前暂不支持通过version自动识别数据库升级降级操作，只能由开发者自行维护。                                                 |
| callback | AsyncCallback&lt;[RdbStore](#rdbstore)&gt; | 是   | 指定callback回调函数，返回RdbStore对象。                     |

**示例：**

FA模型示例：

```js
import featureAbility from '@ohos.ability.featureAbility';
import relationalStore from '@ohos.data.relationalStore';
import window from '@ohos.window';
import { BusinessError } from '@ohos.base';

const STORE_CONFIG: data_rdb.StoreConfig = { name: "RdbTest.db"}
data_rdb.getRdbStore(this.context, STORE_CONFIG, 1, (err, rdbStore) => {
  if (err) {
    console.info("Get RdbStore failed, err: " + err)
    return
  }
  console.log("Get RdbStore successfully.")
})
```

Stage模型示例：

```ts
import UIAbility from '@ohos.app.ability.UIAbility';
import { BusinessError } from "@ohos.base";
import window from '@ohos.window';

const STORE_CONFIG: data_rdb.StoreConfig = { name: "RdbTest.db"}
class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage){
    data_rdb.getRdbStore(this.context, STORE_CONFIG, 1, (err: BusinessError, rdbStore: data_rdb.RdbStore) => {
      if (err) {
        console.info("Get RdbStore failed, err: " + err)
        return
      }
      console.log("Get RdbStore successfully.")
    })
  }
}
```

## data_rdb.getRdbStore

getRdbStore(context: Context, config: StoreConfig, version: number): Promise&lt;RdbStore&gt;

获得一个相关的RdbStore，操作关系型数据库，用户可以根据自己的需求配置RdbStore的参数，然后通过RdbStore调用相关接口可以执行相关的数据操作，使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名  | 类型                        | 必填 | 说明                                                         |
| ------- | --------------------------- | ---- | ------------------------------------------------------------ |
| context | Context                     | 是   | 应用的上下文。<br>FA模型的应用Context定义见[Context](../apis-ability-kit/js-apis-inner-app-context.md)。<br>Stage模型的应用Context定义见[Context](../apis-ability-kit/js-apis-inner-app-context.md)。 |
| config  | [StoreConfig](#storeconfig) | 是   | 与此RDB存储相关的数据库配置。                                |
| version | number                      | 是   | 数据库版本。<br>目前暂不支持通过version自动识别数据库升级降级操作，只能由开发者自行维护。                                                 |

**返回值**：

| 类型                                 | 说明                            |
| ------------------------------------ | ------------------------------- |
| Promise&lt;[RdbStore](#rdbstore)&gt; | Promise对象。返回RdbStore对象。 |

**示例：**

FA模型示例：

```js
import featureAbility from '@ohos.ability.featureAbility';

const STORE_CONFIG: data_rdb.StoreConfig = { name: "RdbTest.db"}
let promise = data_rdb.getRdbStore(this.context, STORE_CONFIG, 1);
promise.then(async (rdbStore) => {
  console.log("Get RdbStore successfully.")
}).catch((err: BusinessError) => {
  console.log("Get RdbStore failed, err: " + err)
})
```

Stage模型示例：

```ts
import UIAbility from '@ohos.app.ability.UIAbility';
import { BusinessError } from "@ohos.base";
import window from '@ohos.window';

const STORE_CONFIG: data_rdb.StoreConfig = { name: "RdbTest.db"}
class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage){
    context = this.context
  }
}

// 获取context后调用getRdbStore
let promise = data_rdb.getRdbStore(this.context, STORE_CONFIG, 1);
promise.then(async (rdbStore: data_rdb.RdbStore) => {
  console.log("Get RdbStore successfully.")
}).catch((err: BusinessError) => {
  console.log("Get RdbStore failed, err: " + err)
})
```

## data_rdb.deleteRdbStore

deleteRdbStore(context: Context, name: string, callback: AsyncCallback&lt;void&gt;): void

删除数据库，使用callback异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名   | 类型                      | 必填 | 说明                                                         |
| -------- | ------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                   | 是   | 应用的上下文。<br>FA模型的应用Context定义见[Context](../apis-ability-kit/js-apis-inner-app-context.md)。<br>Stage模型的应用Context定义见[Context](../apis-ability-kit/js-apis-inner-app-context.md)。 |
| name     | string                    | 是   | 数据库名称。                                                 |
| callback | AsyncCallback&lt;void&gt; | 是   | 指定callback回调函数。                                       |

**示例：**

FA模型示例：

```js
import featureAbility from '@ohos.ability.featureAbility';

data_rdb.deleteRdbStore(this.context, "RdbTest.db", (err) => {
  if (err) {
    console.info("Delete RdbStore failed, err: " + err)
    return
  }
  console.log("Delete RdbStore successfully.")
})
```

Stage模型示例：

```ts
import UIAbility from '@ohos.app.ability.UIAbility';
import window from '@ohos.window';

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage){
    context = this.context
  }
}

// 获取context后调用deleteRdbStore
data_rdb.deleteRdbStore(this.context, "RdbTest.db", (err) => {
  if (err) {
    console.info("Delete RdbStore failed, err: " + err)
    return
  }
  console.log("Delete RdbStore successfully.")
})
```

## data_rdb.deleteRdbStore

deleteRdbStore(context: Context, name: string): Promise&lt;void&gt;

使用指定的数据库文件配置删除数据库，使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数**

| 参数名  | 类型    | 必填 | 说明                                                         |
| ------- | ------- | ---- | ------------------------------------------------------------ |
| context | Context | 是   | 应用的上下文。<br>FA模型的应用Context定义见[Context](../apis-ability-kit/js-apis-inner-app-context.md)。<br>Stage模型的应用Context定义见[Context](../apis-ability-kit/js-apis-inner-app-context.md)。 |
| name    | string  | 是   | 数据库名称。                                                 |

**返回值**：

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

FA模型示例：

```js
import featureAbility from '@ohos.ability.featureAbility';

let promise = data_rdb.deleteRdbStore(this.context, "RdbTest.db")
promise.then(() => {
  console.log("Delete RdbStore successfully.")
}).catch((err: BusinessError) => {
  console.info("Delete RdbStore failed, err: " + err)
})
```

Stage模型示例：

```ts
import UIAbility from '@ohos.app.ability.UIAbility';
import { BusinessError } from "@ohos.base";
import window from '@ohos.window';

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage){
    context = this.context
  }
}

// 获取context后调用deleteRdbStore
let promise = data_rdb.deleteRdbStore(this.context, "RdbTest.db")
promise.then(()=>{
  console.log("Delete RdbStore successfully.")
}).catch((err: BusinessError) => {
  console.info("Delete RdbStore failed, err: " + err)
})
```

## ValueType

type ValueType = number | string | boolean

用于表示允许的数据字段类型。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

| 类型    | 说明                 |
| ------- | -------------------- |
| number  | 表示值类型为数字。   |
| string  | 表示值类型为字符。   |
| boolean | 表示值类型为布尔值。 |


## ValuesBucket

type ValuesBucket = { [key: string]: ValueType | Uint8Array | null }

用于存储键值对的类型。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

| 键类型 | 值类型                                                      |
| ------ | ----------------------------------------------------------- |
| string | [ValueType](#valuetype)\|&nbsp;Uint8Array&nbsp;\|&nbsp;null |

## SyncMode<sup>8+</sup>

指数据库同步模式。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

| 名称           | 值   | 说明                               |
| -------------- | ---- | ---------------------------------- |
| SYNC_MODE_PUSH | 0    | 表示数据从本地设备推送到远程设备。 |
| SYNC_MODE_PULL | 1    | 表示数据从远程设备拉至本地设备。   |

## SubscribeType<sup>8+</sup>

描述订阅类型。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

| 名称                  | 值   | 说明               |
| --------------------- | ---- | ------------------ |
| SUBSCRIBE_TYPE_REMOTE | 0    | 订阅远程数据更改。 |

## StoreConfig

管理关系数据库配置。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| name | string | 是 | 数据库文件名。 |

## RdbPredicates

表示关系型数据库（RDB）的谓词。该类确定RDB中条件表达式的值是true还是false。

### constructor

constructor(name: string)

构造函数。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| name | string | 是 | 数据库表名。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
```

### inDevices<sup>8+</sup>

inDevices(devices: Array&lt;string&gt;): RdbPredicates

同步分布式数据库时连接到组网内指定的远程设备。

> **说明：**
>
> 其中devices通过调用<!--RP2-->[deviceManager.getTrustedDeviceListSync](../apis-distributedservice-kit/js-apis-device-manager-sys.md#gettrusteddevicelistsync)方法得到。<!--RP2End-->deviceManager模块的接口均为系统接口，仅系统应用可用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| devices | Array&lt;string&gt; | 是 | 指定的组网内的远程设备ID。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回与指定字段匹配的谓词。 |

**示例：**

```ts
import deviceManager from '@ohos.distributedHardware.deviceManager';

let dmInstance: deviceManager.DeviceManager;
let deviceIds: Array<string> = [];
let devices: Array<string> = [];

deviceManager.createDeviceManager("com.example.appdatamgrverify", (err: BusinessError, manager: void) => {
  if (err) {
    console.log("create device manager failed, err=" + err);
    return;
  }
  dmInstance = manager;
  devices = dmInstance.getTrustedDeviceListSync();
  for (let i = 0; i < devices.length; i++) {
    deviceIds[i] = devices[i].deviceId;
  }
})

let predicates = new data_rdb.RdbPredicates("EMPLOYEE");
predicates.inDevices(deviceIds);
                                  
let predicates = new data_rdb.RdbPredicates("EMPLOYEE");
predicates.inDevices(deviceIds);
```

### inAllDevices<sup>8+</sup>

inAllDevices(): RdbPredicates

同步分布式数据库时连接到组网内所有的远程设备。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回与指定字段匹配的谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.inAllDevices()
```

### equalTo

equalTo(field: string, value: ValueType): RdbPredicates

配置谓词以匹配数据字段为ValueType且值等于指定值的字段。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| field | string | 是 | 数据库表中的列名。 |
| value | [ValueType](#valuetype) | 是 | 指示要与谓词匹配的值。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回与指定字段匹配的谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "lisi")
```


### notEqualTo

notEqualTo(field: string, value: ValueType): RdbPredicates

配置谓词以匹配数据字段为ValueType且值不等于指定值的字段。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| field | string | 是 | 数据库表中的列名。 |
| value | [ValueType](#valuetype) | 是 | 指示要与谓词匹配的值。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回与指定字段匹配的谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.notEqualTo("NAME", "lisi")
```


### beginWrap

beginWrap(): RdbPredicates

向谓词添加左括号。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回带有左括号的Rdb谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "lisi")
    .beginWrap()
    .equalTo("AGE", 18)
    .or()
    .equalTo("SALARY", 200.5)
    .endWrap()
```

### endWrap

endWrap(): RdbPredicates

向谓词添加右括号。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回带有右括号的Rdb谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "lisi")
    .beginWrap()
    .equalTo("AGE", 18)
    .or()
    .equalTo("SALARY", 200.5)
    .endWrap()
```

### or

or(): RdbPredicates

将或条件添加到谓词中。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回带有或条件的Rdb谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "Lisa")
    .or()
    .equalTo("NAME", "Rose")
```

### and

and(): RdbPredicates

向谓词添加和条件。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回带有和条件的Rdb谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "Lisa")
    .and()
    .equalTo("SALARY", 200.5)
```

### contains

contains(field: string, value: string): RdbPredicates

配置谓词以匹配数据字段为string且value包含指定值的字段。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| field | string | 是 | 数据库表中的列名。 |
| value | string | 是 | 指示要与谓词匹配的值。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回与指定字段匹配的谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.contains("NAME", "os")
```

### beginsWith

beginsWith(field: string, value: string): RdbPredicates

配置谓词以匹配数据字段为string且值以指定字符串开头的字段。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| field | string | 是 | 数据库表中的列名。 |
| value | string | 是 | 指示要与谓词匹配的值。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回与指定字段匹配的谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.beginsWith("NAME", "os")
```

### endsWith

endsWith(field: string, value: string): RdbPredicates

配置谓词以匹配数据字段为string且值以指定字符串结尾的字段。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| field | string | 是 | 数据库表中的列名。 |
| value | string | 是 | 指示要与谓词匹配的值。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回与指定字段匹配的谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.endsWith("NAME", "se")
```

### isNull

isNull(field: string): RdbPredicates

配置谓词以匹配值为null的字段。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| field | string | 是 | 数据库表中的列名。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回与指定字段匹配的谓词。 |

**示例**：
```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.isNull("NAME")
```

### isNotNull

isNotNull(field: string): RdbPredicates

配置谓词以匹配值不为null的指定字段。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| field | string | 是 | 数据库表中的列名。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回与指定字段匹配的谓词。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| **错误码ID** | **错误信息**                                                                                                       |
| --------- |----------------------------------------------------------------------------------------------------------------|
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types. |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.isNotNull("NAME")
```

### like

like(field: string, value: string): RdbPredicates

配置谓词以匹配数据字段为string且值类似于指定字符串的字段。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| field | string | 是 | 数据库表中的列名。 |
| value | string | 是 | 指示要与谓词匹配的值。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回与指定字段匹配的谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.like("NAME", "%os%")
```

### glob

glob(field: string, value: string): RdbPredicates

配置RdbPredicates匹配数据字段为string的指定字段。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| field | string | 是 | 数据库表中的列名。 |
| value | string | 是 | 指示要与谓词匹配的值。<br>支持通配符，*表示0个、1个或多个数字或字符，?表示1个数字或字符。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回与指定字段匹配的谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.glob("NAME", "?h*g")
```

### between

between(field: string, low: ValueType, high: ValueType): RdbPredicates

将谓词配置为匹配数据字段为ValueType且value在给定范围内的指定字段。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| field | string | 是 | 数据库表中的列名。 |
| low | [ValueType](#valuetype) | 是 | 指示与谓词匹配的最小值。 |
| high | [ValueType](#valuetype) | 是 | 指示要与谓词匹配的最大值。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回与指定字段匹配的谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.between("AGE", 10, 50)
```

### notBetween

notBetween(field: string, low: ValueType, high: ValueType): RdbPredicates

配置RdbPredicates以匹配数据字段为ValueType且value超出给定范围的指定字段。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| field | string | 是 | 数据库表中的列名。 |
| low | [ValueType](#valuetype) | 是 | 指示与谓词匹配的最小值。 |
| high | [ValueType](#valuetype) | 是 | 指示要与谓词匹配的最大值。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回与指定字段匹配的谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.notBetween("AGE", 10, 50)
```

### greaterThan

greaterThan(field: string, value: ValueType): RdbPredicates

配置谓词以匹配数据字段为ValueType且值大于指定值的字段。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| field | string | 是 | 数据库表中的列名。 |
| value | [ValueType](#valuetype) | 是 | 指示要与谓词匹配的值。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回与指定字段匹配的谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.greaterThan("AGE", 18)
```

### lessThan

lessThan(field: string, value: ValueType): RdbPredicates

配置谓词以匹配数据字段为valueType且value小于指定值的字段。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| field | string | 是 | 数据库表中的列名。 |
| value | [ValueType](#valuetype) | 是 | 指示要与谓词匹配的值。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回与指定字段匹配的谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.lessThan("AGE", 20)
```

### greaterThanOrEqualTo

greaterThanOrEqualTo(field: string, value: ValueType): RdbPredicates

配置谓词以匹配数据字段为ValueType且value大于或等于指定值的字段。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| field | string | 是 | 数据库表中的列名。 |
| value | [ValueType](#valuetype) | 是 | 指示要与谓词匹配的值。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回与指定字段匹配的谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.greaterThanOrEqualTo("AGE", 18)
```

### lessThanOrEqualTo

lessThanOrEqualTo(field: string, value: ValueType): RdbPredicates

配置谓词以匹配数据字段为ValueType且value小于或等于指定值的字段。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| field | string | 是 | 数据库表中的列名。 |
| value | [ValueType](#valuetype) | 是 | 指示要与谓词匹配的值。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回与指定字段匹配的谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.lessThanOrEqualTo("AGE", 20)
```

### orderByAsc

orderByAsc(field: string): RdbPredicates

配置谓词以匹配其值按升序排序的列。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| field | string | 是 | 数据库表中的列名。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回与指定字段匹配的谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.orderByAsc("NAME")
```

### orderByDesc

orderByDesc(field: string): RdbPredicates

配置谓词以匹配其值按降序排序的列。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| field | string | 是 | 数据库表中的列名。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回与指定字段匹配的谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.orderByDesc("AGE")
```

### distinct

distinct(): RdbPredicates

配置谓词以过滤重复记录并仅保留其中一个。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回可用于过滤重复记录的谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "Rose").distinct()
```

### limitAs

limitAs(value: number): RdbPredicates

设置最大数据记录数的谓词。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | number | 是 | 最大数据记录数。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回可用于设置最大数据记录数的谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "Rose").limitAs(3)
```

### offsetAs

offsetAs(rowOffset: number): RdbPredicates

配置RdbPredicates以指定返回结果的起始位置。需要同步调用limitAs接口指定查询数量，否则将无查询结果。如需查询指定偏移位置后的所有行，limitAs接口调用需传参数-1。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| rowOffset | number | 是 | 返回结果的起始位置，取值为正整数。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回具有指定返回结果起始位置的谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "Rose").limitAs(-1).offsetAs(3)
```

### groupBy

groupBy(fields: Array&lt;string&gt;): RdbPredicates

配置RdbPredicates按指定列分组查询结果。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| fields | Array&lt;string&gt; | 是 | 指定分组依赖的列名。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回分组查询列的谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.groupBy(["AGE", "NAME"])
```

### indexedBy

indexedBy(field: string): RdbPredicates

配置RdbPredicates以指定索引列。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| field | string | 是 | 索引列的名称。 |

**返回值**：


| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回具有指定索引列的RdbPredicates。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.indexedBy("SALARY_INDEX")
```

### in

in(field: string, value: Array&lt;ValueType&gt;): RdbPredicates

配置RdbPredicates以匹配数据字段为ValueType数组且值在给定范围内的指定字段。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| field | string | 是 | 数据库表中的列名。 |
| value | Array&lt;[ValueType](#valuetype)&gt; | 是 | 以ValueType型数组形式指定的要匹配的值。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回与指定字段匹配的谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.in("AGE", [18, 20])
```

### notIn

notIn(field: string, value: Array&lt;ValueType&gt;): RdbPredicates

将RdbPredicates配置为匹配数据字段为ValueType且值超出给定范围的指定字段。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| field | string | 是 | 数据库表中的列名。 |
| value | Array&lt;[ValueType](#valuetype)&gt; | 是 | 以ValueType数组形式指定的要匹配的值。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| [RdbPredicates](#rdbpredicates) | 返回与指定字段匹配的谓词。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.notIn("NAME", ["Lisa", "Rose"])
```

## RdbStore

提供管理关系数据库（RDB）方法的接口。

在使用以下相关接口前，请使用[executeSql](#executesql8)接口初始化数据库表结构和相关数据。

### insert

insert(table: string, values: ValuesBucket, callback: AsyncCallback&lt;number&gt;):void

向目标表中插入一行数据，使用callback异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| table | string | 是 | 指定的目标表名。 |
| values | [ValuesBucket](#valuesbucket) | 是 | 表示要插入到表中的数据行。 |
| callback | AsyncCallback&lt;number&gt; | 是 | 指定callback回调函数。如果操作成功，返回行ID；否则返回-1。 |

**示例：**

```ts
import { ValuesBucket } from '@ohos.data.ValuesBucket';

let key1 = "NAME";
let key2 = "AGE";
let key3 = "SALARY";
let key4 = "CODES";
let value1 = "Lisi";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);
const valueBucket: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
  key4: value4,
};

rdbStore.insert("EMPLOYEE", valueBucket, (status: number, rowId: number) => {
  if (status) {
    console.log("Insert is failed");
    return;
  }
  console.log("Insert is successful, rowId = " + rowId);
})
```

### insert

insert(table: string, values: ValuesBucket):Promise&lt;number&gt;

向目标表中插入一行数据，使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| table | string | 是 | 指定的目标表名。 |
| values | [ValuesBucket](#valuesbucket) | 是 | 表示要插入到表中的数据行。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;number&gt; | Promise对象。如果操作成功，返回行ID；否则返回-1。 |

**示例：**

```ts
import { ValuesBucket } from '@ohos.data.ValuesBucket';

let key1 = "NAME";
let key2 = "AGE";
let key3 = "SALARY";
let key4 = "CODES";
let value1 = "Lisi";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);
const valueBucket: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
  key4: value4,
};

let promise: void = rdbStore.insert("EMPLOYEE", valueBucket)
promise.then((rowId: BusinessError) => {
  console.log("Insert is successful, rowId = " + rowId);
}).catch((status: number) => {
  console.log("Insert is failed");
})
```

### batchInsert

batchInsert(table: string, values: Array&lt;ValuesBucket&gt;, callback: AsyncCallback&lt;number&gt;):void

向目标表中插入一组数据，使用callback异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| table | string | 是 | 指定的目标表名。 |
| values | Array&lt;[ValuesBucket](#valuesbucket)&gt; | 是 | 表示要插入到表中的一组数据。 |
| callback | AsyncCallback&lt;number&gt; | 是 | 指定callback回调函数。如果操作成功，返回插入的数据个数，否则返回-1。 |

**示例：**

```ts
import { ValuesBucket } from '@ohos.data.ValuesBucket';

let key1 = "NAME";
let key2 = "AGE";
let key3 = "SALARY";
let key4 = "CODES";
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);
let value5 = "Jack";
let value6 = 19;
let value7 = 101.5;
let value8 = new Uint8Array([6, 7, 8, 9, 10]);
let value9 = "Tom";
let value10 = 20;
let value11 = 102.5;
let value12 = new Uint8Array([11, 12, 13, 14, 15]);
const valueBucket1: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
  key4: value4,
};
const valueBucket2: ValuesBucket = {
  key1: value5,
  key2: value6,
  key3: value7,
  key4: value8,
};
const valueBucket3: ValuesBucket = {
  key1: value9,
  key2: value10,
  key3: value11,
  key4: value12,
};

let valueBuckets = new Array(valueBucket1, valueBucket2, valueBucket3);
rdbStore.batchInsert("EMPLOYEE", valueBuckets, (status: number, insertNum: number) => {
  if (status) {
    console.log("batchInsert is failed, status = " + status);
    return;
  }
  console.log("batchInsert is successful, the number of values that were inserted = " + insertNum);
})
```

### batchInsert

batchInsert(table: string, values: Array&lt;ValuesBucket&gt;):Promise&lt;number&gt;

向目标表中插入一组数据，使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| table | string | 是 | 指定的目标表名。 |
| values | Array&lt;[ValuesBucket](#valuesbucket)&gt; | 是 | 表示要插入到表中的一组数据。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;number&gt; | Promise对象。如果操作成功，返回插入的数据个数，否则返回-1。 |

**示例：**

```ts
import { ValuesBucket } from '@ohos.data.ValuesBucket';

let key1 = "NAME";
let key2 = "AGE";
let key3 = "SALARY";
let key4 = "CODES";
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);
let value5 = "Jack";
let value6 = 19;
let value7 = 101.5;
let value8 = new Uint8Array([6, 7, 8, 9, 10]);
let value9 = "Tom";
let value10 = 20;
let value11 = 102.5;
let value12 = new Uint8Array([11, 12, 13, 14, 15]);
const valueBucket1: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
  key4: value4,
};
const valueBucket2: ValuesBucket = {
  key1: value5,
  key2: value6,
  key3: value7,
  key4: value8,
};
const valueBucket3: ValuesBucket = {
  key1: value9,
  key2: value10,
  key3: value11,
  key4: value12,
};

let valueBuckets = new Array(valueBucket1, valueBucket2, valueBucket3);
let promise: void = rdbStore.batchInsert("EMPLOYEE", valueBuckets);
promise.then((insertNum: number) => {
  console.log("batchInsert is successful, the number of values that were inserted = " + insertNum);
}).catch((status: number) => {
  console.log("batchInsert is failed, status = " + status);
})
```

### update

update(values: ValuesBucket, predicates: RdbPredicates, callback: AsyncCallback&lt;number&gt;):void

根据RdbPredicates的指定实例对象更新数据库中的数据，使用callback异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| values | [ValuesBucket](#valuesbucket) | 是 | values指示数据库中要更新的数据行。键值对与数据库表的列名相关联。 |
| predicates | [RdbPredicates](#rdbpredicates) | 是 | RdbPredicates的实例对象指定的更新条件。 |
| callback | AsyncCallback&lt;number&gt; | 是 | 指定的callback回调方法。返回受影响的行数。 |

**示例：**

```ts
import { ValuesBucket } from '@ohos.data.ValuesBucket';

let key1 = "NAME";
let key2 = "AGE";
let key3 = "SALARY";
let key4 = "CODES";
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

const valueBucket: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
  key4: value4,
};
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "Lisa")
rdbStore.update(valueBucket, predicates, (err: BusinessError, rows: number) => {
  if (err) {
    console.info("Updated failed, err: " + err)
    return
  }
  console.log("Updated row count: " + rows)
})
```

### update

update(values: ValuesBucket, predicates: RdbPredicates):Promise&lt;number&gt;

根据RdbPredicates的指定实例对象更新数据库中的数据，使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| values | [ValuesBucket](#valuesbucket) | 是 | values指示数据库中要更新的数据行。键值对与数据库表的列名相关联。 |
| predicates | [RdbPredicates](#rdbpredicates) | 是 | RdbPredicates的实例对象指定的更新条件。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;number&gt; | 指定的Promise回调方法。返回受影响的行数。 |

**示例：**

```ts
import { ValuesBucket } from '@ohos.data.ValuesBucket';

let key1 = "NAME";
let key2 = "AGE";
let key3 = "SALARY";
let key4 = "CODES";
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

const valueBucket: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
  key4: value4,
};
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "Lisa")
let promise: void = rdbStore.update(valueBucket, predicates)
promise.then(async (rows: number) => {
  console.log("Updated row count: " + rows)
}).catch((err: BusinessError) => {
  console.info("Updated failed, err: " + err)
})
```

### delete

delete(predicates: RdbPredicates, callback: AsyncCallback&lt;number&gt;):void

根据RdbPredicates的指定实例对象从数据库中删除数据，使用callback异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| predicates | [RdbPredicates](#rdbpredicates) | 是 | RdbPredicates的实例对象指定的删除条件。 |
| callback | AsyncCallback&lt;number&gt; | 是 | 指定callback回调函数。返回受影响的行数。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "Lisa")
rdbStore.delete(predicates, (err: BusinessError, rows: number) => {
  if (err) {
    console.info("Delete failed, err: " + err)
    return
  }
  console.log("Delete rows: " + rows)
})
```

### delete

delete(predicates: RdbPredicates):Promise&lt;number&gt;

根据RdbPredicates的指定实例对象从数据库中删除数据，使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| predicates | [RdbPredicates](#rdbpredicates) | 是 | RdbPredicates的实例对象指定的删除条件。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;number&gt; | Promise对象。返回受影响的行数。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "Lisa")
let promise: void = rdbStore.delete(predicates)
promise.then((rows: number) => {
  console.log("Delete rows: " + rows)
}).catch((err: BusinessError) => {
  console.info("Delete failed, err: " + err)
})
```

### query

query(predicates: RdbPredicates, columns: Array&lt;string&gt;, callback: AsyncCallback&lt;ResultSet&gt;):void

根据指定条件查询数据库中的数据，使用callback异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| predicates | [RdbPredicates](#rdbpredicates) | 是 | RdbPredicates的实例对象指定的查询条件。 |
| columns | Array&lt;string&gt; | 是 | 表示要查询的列。如果值为空，则查询应用于所有列。 |
| callback | AsyncCallback&lt;[ResultSet](js-apis-data-resultset.md)&gt; | 是 | 指定callback回调函数。如果操作成功，则返回ResultSet对象。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "Rose")
rdbStore.query(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"], (err: BusinessError, resultSet: void) => {
  if (err) {
    console.info("Query failed, err: " + err)
    return
  }
  console.log("ResultSet column names: " + resultSet.columnNames)
  console.log("ResultSet column count: " + resultSet.columnCount)
})
```

### query

query(predicates: RdbPredicates, columns?: Array&lt;string&gt;):Promise&lt;ResultSet&gt;

根据指定条件查询数据库中的数据，使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| predicates | [RdbPredicates](#rdbpredicates) | 是 | RdbPredicates的实例对象指定的查询条件。 |
| columns | Array&lt;string&gt; | 否 | 表示要查询的列。如果值为空，则查询应用于所有列。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[ResultSet](js-apis-data-resultset.md)&gt; | Promise对象。如果操作成功，则返回ResultSet对象。 |

**示例：**

```ts
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "Rose")
let promise: void = rdbStore.query(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"])
promise.then((resultSet: void) => {
  console.log("ResultSet column names: " + resultSet.columnNames)
  console.log("ResultSet column count: " + resultSet.columnCount)
}).catch((err: BusinessError) => {
  console.info("Query failed, err: " + err)
})
```

### querySql<sup>8+</sup>

querySql(sql: string, bindArgs: Array&lt;ValueType&gt;, callback: AsyncCallback&lt;ResultSet&gt;):void

根据指定SQL语句查询数据库中的数据，使用callback异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| sql | string | 是 | 指定要执行的SQL语句。 |
| bindArgs | Array&lt;[ValueType](#valuetype)&gt; | 是 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数需为空数组。 |
| callback | AsyncCallback&lt;[ResultSet](js-apis-data-resultset.md)&gt; | 是 | 指定callback回调函数。如果操作成功，则返回ResultSet对象。 |

**示例：**

```ts
rdbStore.querySql("SELECT * FROM EMPLOYEE CROSS JOIN BOOK WHERE BOOK.NAME = ?", ['sanguo'], (err: BusinessError, resultSet: void) => {
  if (err) {
    console.info("Query failed, err: " + err)
    return
  }
  console.log("ResultSet column names: " + resultSet.columnNames)
  console.log("ResultSet column count: " + resultSet.columnCount)
})
```

### querySql<sup>8+</sup>

querySql(sql: string, bindArgs?: Array&lt;ValueType&gt;):Promise&lt;ResultSet&gt;

根据指定SQL语句查询数据库中的数据，使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| sql | string | 是 | 指定要执行的SQL语句。 |
| bindArgs | Array&lt;[ValueType](#valuetype)&gt; | 否 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数不填。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[ResultSet](js-apis-data-resultset.md)&gt; | Promise对象。如果操作成功，则返回ResultSet对象。 |

**示例：**

```ts
let promise: void = rdbStore.querySql("SELECT * FROM EMPLOYEE CROSS JOIN BOOK WHERE BOOK.NAME = 'sanguo'")
promise.then((resultSet: void) => {
  console.log("ResultSet column names: " + resultSet.columnNames)
  console.log("ResultSet column count: " + resultSet.columnCount)
}).catch((err: BusinessError) => {
  console.info("Query failed, err: " + err)
})
```

### executeSql<sup>8+</sup>

executeSql(sql: string, bindArgs: Array&lt;ValueType&gt;, callback: AsyncCallback&lt;void&gt;):void

执行包含指定参数但不返回值的SQL语句，使用callback异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| sql | string | 是 | 指定要执行的SQL语句。 |
| bindArgs | Array&lt;[ValueType](#valuetype)&gt; | 是 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数需为空数组。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 指定callback回调函数。 |

**示例：**

```ts
const SQL_DELETE_TABLE = "DELETE FROM test WHERE name = ?"
rdbStore.executeSql(SQL_DELETE_TABLE, ['zhangsan'], (err: BusinessError) => {
  if (err) {
    console.info("ExecuteSql failed, err: " + err)
    return
  }
  console.info('Delete table done.')
})
```

### executeSql<sup>8+</sup>

executeSql(sql: string, bindArgs?: Array&lt;ValueType&gt;):Promise&lt;void&gt;

执行包含指定参数但不返回值的SQL语句，使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| sql | string | 是 | 指定要执行的SQL语句。 |
| bindArgs | Array&lt;[ValueType](#valuetype)&gt; | 否 | SQL语句中参数的值。该值与sql参数语句中的占位符相对应。当sql参数语句完整时，该参数不填。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```ts
const SQL_DELETE_TABLE = "DELETE FROM test WHERE name = 'zhangsan'"
let promise = rdbStore.executeSql(SQL_DELETE_TABLE)
promise.then(() => {
  console.info('Delete table done.')
}).catch((err: BusinessError) => {
  console.info("ExecuteSql failed, err: " + err)
})
```

### beginTransaction<sup>8+</sup>

beginTransaction():void

在开始执行SQL语句之前，开始事务。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**示例：**

```ts
import featureAbility from '@ohos.ability.featureAbility';
import { ValuesBucket } from '@ohos.data.ValuesBucket';

let key1 = "NAME";
let key2 = "AGE";
let key3 = "SALARY";
let key4 = "blobType";
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3]);

const valueBucket: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
  key4: value4,
};

data_rdb.getRdbStore(this.context, "RdbTest.db", 1, async (err: BusinessError, rdbStore) => {
  rdbStore.beginTransaction()
  await rdbStore.insert("test", valueBucket)
  rdbStore.commit()
})
```

### commit<sup>8+</sup>

commit():void

提交已执行的SQL语句。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**示例：**

```ts
import { ValuesBucket } from '@ohos.data.ValuesBucket';
import featureAbility from '@ohos.ability.featureAbility';

let key1 = "NAME";
let key2 = "AGE";
let key3 = "SALARY";
let key4 = "blobType";
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3]);

const valueBucket: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
  key4: value4,
};

data_rdb.getRdbStore(this.context, "RdbTest.db", 1, async (err: BusinessError, rdbStore) => {
  rdbStore.beginTransaction()
  await rdbStore.insert("test", valueBucket)
  rdbStore.commit()
})
```

### rollBack<sup>8+</sup>

rollBack():void

回滚已经执行的SQL语句。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**示例：**

```ts
import { ValuesBucket } from '@ohos.data.ValuesBucket';
import featureAbility from '@ohos.ability.featureAbility';

let key1 = "NAME";
let key2 = "AGE";
let key3 = "SALARY";
let key4 = "blobType";
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3]);

const valueBucket: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
  key4: value4,
};

const STORE_CONFIG = { name: "RdbTest.db"}
data_rdb.getRdbStore(this,context, "RdbTest.db", 1, async (err: BusinessError, rdbStore) => {
    try {
		rdbStore.beginTransaction()
		await rdbStore.insert("test", valueBucket)
		rdbStore.commit()
	} catch (e) {
		rdbStore.rollBack()
	}
})
```

### setDistributedTables<sup>8+</sup>

setDistributedTables(tables: Array&lt;string&gt;, callback: AsyncCallback&lt;void&gt;): void

设置分布式列表，使用callback异步回调。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| tables | Array&lt;string&gt; | 是 | 要设置的分布式列表表名。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 指定callback回调函数。 |

**示例：**

```ts
rdbStore.setDistributedTables(["EMPLOYEE"], (err: BusinessError) => {
  if (err) {
    console.info('SetDistributedTables failed, err: ' + err)
    return
  }
  console.info('SetDistributedTables successfully.')
})
```

### setDistributedTables<sup>8+</sup>

 setDistributedTables(tables: Array&lt;string&gt;): Promise&lt;void&gt;

设置分布式列表，使用Promise异步回调。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| tables | Array&lt;string&gt; | 是 | 要设置的分布式列表表名。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```ts
let promise: void = rdbStore.setDistributedTables(["EMPLOYEE"])
promise.then(() => {
  console.info("SetDistributedTables successfully.")
}).catch((err: BusinessError) => {
  console.info("SetDistributedTables failed, err: " + err)
})
```

### obtainDistributedTableName<sup>8+</sup>

obtainDistributedTableName(device: string, table: string, callback: AsyncCallback&lt;string&gt;): void

根据远程设备的本地表名获取指定远程设备的分布式表名。在查询远程设备数据库时，需要使用分布式表名，使用callback异步回调。

> **说明：**
>
> 其中device通过调用<!--RP1-->[deviceManager.getTrustedDeviceListSync](../apis-distributedservice-kit/js-apis-device-manager-sys.md#gettrusteddevicelistsync)方法得到。<!--RP1End-->deviceManager模块的接口均为系统接口，仅系统应用可用。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| device | string | 是 | 远程设备ID 。 |
| table | string | 是 | 远程设备的本地表名。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 指定的callback回调函数。如果操作成功，返回远程设备的分布式表名。 |

**示例：**

```ts
import deviceManager from '@ohos.distributedHardware.deviceManager';

let dmInstance: Array<string>;

deviceManager.createDeviceManager("com.example.appdatamgrverify", (err: BusinessError, manager: void) => {
  if (err) {
    console.log("create device manager failed, err=" + err);
    return;
  }
  dmInstance = manager;
  let devices: Array<string> = dmInstance.getTrustedDeviceListSync();
  let deviceId: Array<string> = devices[0].deviceId;
})

rdbStore.obtainDistributedTableName(deviceId, "EMPLOYEE", (err: BusinessError, tableName: String) {
  if (err) {
    console.info('ObtainDistributedTableName failed, err: ' + err)
    return
  }
  console.info('ObtainDistributedTableName successfully, tableName=.' + tableName)
})
```

### obtainDistributedTableName<sup>8+</sup>

 obtainDistributedTableName(device: string, table: string): Promise&lt;string&gt;

根据远程设备的本地表名获取指定远程设备的分布式表名。在查询远程设备数据库时，需要使用分布式表名，使用Promise异步回调。

> **说明：**
>
> 其中device通过调用<!--RP1-->[deviceManager.getTrustedDeviceListSync](../apis-distributedservice-kit/js-apis-device-manager-sys.md#gettrusteddevicelistsync)方法得到。<!--RP1End-->deviceManager模块的接口均为系统接口，仅系统应用可用。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| device | string | 是 | 远程设备ID。 |
| table | string | 是 | 远程设备的本地表名。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;string&gt; | Promise对象。如果操作成功，返回远程设备的分布式表名。 |

**示例：**

```ts
import deviceManager from '@ohos.distributedHardware.deviceManager';

let dmInstance: Array<string>;

deviceManager.createDeviceManager("com.example.appdatamgrverify", (err: BusinessError, manager: void) => {
  if (err) {
    console.log("create device manager failed, err=" + err);
    return;
  }
  dmInstance = manager;
  let devices: Array<string> = dmInstance.getTrustedDeviceListSync();
  let deviceId: Array<string> = devices[0].deviceId;
})

let promise: void = rdbStore.obtainDistributedTableName(deviceId, "EMPLOYEE")
promise.then((tableName: String) => {
  console.info('ObtainDistributedTableName successfully, tableName= ' + tableName)
}).catch((err: BusinessError) => {
  console.info('ObtainDistributedTableName failed, err: ' + err)
})
```

### sync<sup>8+</sup>

sync(mode: SyncMode, predicates: RdbPredicates, callback: AsyncCallback&lt;Array&lt;[string, number]&gt;&gt;): void

在设备之间同步数据，使用callback异步回调。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| mode | [SyncMode](#syncmode8) | 是 | 指同步模式。该值可以是推、拉。 |
| predicates | [RdbPredicates](#rdbpredicates) | 是 | 约束同步数据和设备。 |
| callback | AsyncCallback&lt;Array&lt;[string, number]&gt;&gt; | 是 | 指定的callback回调函数，用于向调用者发送同步结果。string：设备ID；number：每个设备同步状态，0表示成功，其他值表示失败。|

**示例：**

```ts
import deviceManager from '@ohos.distributedHardware.deviceManager';

let dmInstance: Array<string>;

deviceManager.createDeviceManager("com.example.appdatamgrverify", (err: BusinessError, manager: void) => {
  if (err) {
    console.log("create device manager failed, err=" + err);
    return;
  }
  dmInstance = manager;
  let devices: Array<string> = dmInstance.getTrustedDeviceListSync();
  for (let i = 0; i < devices.length; i++) {
    let deviceIds: Array<string> = devices[i].deviceId;
  }
})

let predicates = new data_rdb.RdbPredicates('EMPLOYEE')
predicates.inDevices(deviceIds)
rdbStore.sync(data_rdb.SyncMode.SYNC_MODE_PUSH, predicates, (err: BusinessError, result: void) {
  if (err) {
    console.log('Sync failed, err: ' + err)
    return
  }
  console.log('Sync done.')
  for (let i = 0; i < result.length; i++) {
    console.log('device=' + result[i][0] + ' status=' + result[i][1])
  }
})
```

### sync<sup>8+</sup>

 sync(mode: SyncMode, predicates: RdbPredicates): Promise&lt;Array&lt;[string, number]&gt;&gt;

在设备之间同步数据，使用Promise异步回调。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| mode | [SyncMode](#syncmode8) | 是 | 指同步模式。该值可以是推、拉。 |
| predicates | [RdbPredicates](#rdbpredicates) | 是 | 约束同步数据和设备。 |

**返回值**：

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;Array&lt;[string, number]&gt;&gt; | Promise对象，用于向调用者发送同步结果。string：设备ID；number：每个设备同步状态，0表示成功，其他值表示失败。 |

**示例：**

```ts
import deviceManager from '@ohos.distributedHardware.deviceManager';

let dmInstance: Array<string>;

deviceManager.createDeviceManager("com.example.appdatamgrverify", (err: BusinessError, manager: void) => {
  if (err) {
    console.log("create device manager failed, err=" + err);
    return;
  }
  dmInstance = manager;
  let devices: Array<string> = dmInstance.getTrustedDeviceListSync();
  for (let i = 0; i < devices.length; i++) {
    let deviceIds: Array<string> = devices[i].deviceId;
  }
})

let predicates = new data_rdb.RdbPredicates('EMPLOYEE')
predicates.inDevices(deviceIds)
let promise: void = rdbStore.sync(data_rdb.SyncMode.SYNC_MODE_PUSH, predicates)
promise.then((result: void) =>{
  console.log('Sync done.')
  for (let i = 0; i < result.length; i++) {
    console.log('device=' + result[i][0] + ' status=' + result[i][1])
  }
}).catch((err: BusinessError) => {
  console.log('Sync failed')
})
```

### on('dataChange')<sup>8+</sup>

on(event: 'dataChange', type: SubscribeType, observer: Callback&lt;Array&lt;string&gt;&gt;): void

注册数据库的观察者。当分布式数据库中的数据发生更改时，将调用回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| event | string | 是 | 取值为'dataChange'，表示数据更改。 |
| type | [SubscribeType](#subscribetype8) | 是 | 订阅类型。 |
| observer | Callback&lt;Array&lt;string&gt;&gt; | 是 | 指分布式数据库中数据更改事件的观察者。Array&lt;string>为数据库中的数据发生改变的对端设备ID。 |

**示例：**

```ts
let devices: Array<string>;

try {
  rdbStore.on('dataChange', data_rdb.SubscribeType.SUBSCRIBE_TYPE_REMOTE, (storeObserver: Array<string>) => {
    for (let i = 0; i < devices.length; i++) {
      console.log('device=' + devices[i] + ' data changed')
    }
  })
} catch (err) {
  console.log('Register observer failed')
}
```

### off('dataChange')<sup>8+</sup>

off(event:'dataChange', type: SubscribeType, observer: Callback&lt;Array&lt;string&gt;&gt;): void

从数据库中删除指定类型的指定观察者，使用callback异步回调。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| event | string | 是 | 取值为'dataChange'，表示数据更改。 |
| type | [SubscribeType](#subscribetype8)    | 是 | 订阅类型。 |
| observer | Callback&lt;Array&lt;string&gt;&gt; | 是 | 指已注册的数据更改观察者。Array&lt;string>为数据库中的数据发生改变的对端设备ID。 |

**示例：**

```ts
let devices: Array<string>;

try {
  rdbStore.off('dataChange', data_rdb.SubscribeType.SUBSCRIBE_TYPE_REMOTE, (storeObserver: Array<string>) => {
    for (let i = 0; i < devices.length; i++) {
      console.log('device=' + devices[i] + ' data changed')
    }
  })
} catch (err) {
  console.log('Unregister observer failed')
}
```
