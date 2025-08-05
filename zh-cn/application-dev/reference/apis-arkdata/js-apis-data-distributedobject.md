# @ohos.data.distributedDataObject (分布式数据对象)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @lvcong_oh-->
<!--SE: @hollokin; @yuchaozhng-->
<!--TSE: @lj_liujing; @yippo; @logic42-->

本模块提供管理基本数据对象的相关能力，包括创建、查询、删除、修改、订阅等；同时支持相同应用多设备间的分布式数据对象协同能力。分布式数据对象处理数据时，不会解析用户数据的内容，存储路径安全性较低，不建议传输个人敏感数据和隐私数据。

> **说明：**
> 
> 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块

```ts
import { distributedDataObject } from '@kit.ArkData';
```

## distributedDataObject.create<sup>9+</sup>

create(context: Context, source: object): DataObject

创建一个分布式数据对象。对象属性支持基本类型（数字类型、布尔类型和字符串类型）以及复杂类型（数组、基本类型嵌套）。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | context | Context | 是 | 应用的上下文。 <br>FA模型的应用Context定义见[Context](../apis-ability-kit/js-apis-inner-app-context.md)。 <br>Stage模型的应用Context定义见[Context](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md)。 |
  | source | object | 是 | 设置分布式数据对象的属性。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [DataObject](#dataobject) | 创建完成的分布式数据对象。 |

**错误码：**

  以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

  | 错误码ID | 错误信息 |
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例：**

FA模型示例：
<!--code_no_check_fa-->
```ts
// 导入模块
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
// 获取context
let context = featureAbility.getContext();
class SourceObject {
    name: string
    age: number
    isVis: boolean

    constructor(name: string, age: number, isVis: boolean) {
        this.name = name;
        this.age = age;
        this.isVis = isVis;
    }
}

let source: SourceObject = new SourceObject("jack", 18, false);
let g_object: distributedDataObject.DataObject = distributedDataObject.create(context, source);
```

Stage模型示例：

```ts
// 导入模块
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let g_object: distributedDataObject.DataObject|null = null;
class SourceObject {
    name: string
    age: number
    isVis: boolean

    constructor(name: string, age: number, isVis: boolean) {
        this.name = name;
        this.age = age;
        this.isVis = isVis;
    }
}

class EntryAbility extends UIAbility {
    onWindowStageCreate(windowStage: window.WindowStage) {
        let source: SourceObject = new SourceObject("jack", 18, false);
        g_object = distributedDataObject.create(this.context, source);
    }
}
```

## distributedDataObject.genSessionId

genSessionId(): string

随机创建一个sessionId。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**返回值：**

  | 类型 | 说明 |
  | -------- | -------- |
  | string | 随机创建的sessionId。 |

**示例：**

```ts
let sessionId: string = distributedDataObject.genSessionId();
```

## SaveSuccessResponse<sup>9+</sup>

[save](#save9)接口回调信息。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| sessionId | string | 是 | 多设备协同的唯一标识。 |
| version | number | 是 | 已保存对象的版本，取值为非负整数。 |
| deviceId | string | 是 | 存储数据的设备号，标识需要保存对象的设备。"local"表示本地设备，否则表示其他设备的设备号。 |

## RevokeSaveSuccessResponse<sup>9+</sup>

[revokeSave](#revokesave9)接口回调信息。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| sessionId | string | 是 | 多设备协同的唯一标识。 |

## BindInfo<sup>11+</sup>

数据库的绑定信息。当前版本只支持关系型数据库的绑定。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

  | 名称       | 类型                                                               | 只读 | 可选 | 说明                                 |
  | ---------- | ------------------------------------------------------------------ | ---- | ---- | ------------------------------------ |
  | storeName  | string                                                             | 否   | 否   | 待绑定资产在所属的数据库中的库名。   |
  | tableName  | string                                                             | 否   | 否   | 待绑定资产在所属的数据库中的表名。   |
  | primaryKey | [commonType.ValuesBucket](js-apis-data-commonType.md#valuesbucket) | 否   | 否   | 待绑定资产在所属的数据库中的主键。   |
  | field      | string                                                             | 否   | 否   | 待绑定资产在所属的数据库中的列名。   |
  | assetName  | string                                                             | 否   | 否   | 待绑定资产在所属的数据库中的资产名。 |

## DataObserver<sup>20+</sup>

type DataObserver = (sessionId: string, fields: Array&lt;string&gt;) => void

定义获取分布式对象数据变更的监听回调函数。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

| 参数名     | 类型                                              | 必填 | 说明                                                         |
| -------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| sessionId | string                           | 是   |   标识变更对象的sessionId。长度需小于128字节，且只能包含字母、数字或下划线_。                                          |
| fields    | Array&lt;string&gt;                   | 是   | 标识对象变更的属性名。属性名可自定义，要求字符串非空且长度不超过128字节。                                     |

## StatusObserver<sup>20+</sup>

type StatusObserver = (sessionId: string, networkId: string, status: string) => void

定义获取分布式对象状态变更的监听回调函数。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| sessionId | string | 是 | 标识变更对象的sessionId。长度不大于128字节，且只能包含字母、数字或下划线_。 |
| networkId | string | 是 | 对端设备的网络标识。要求字符串非空且长度不超过255字节。 |
| status    | string | 是 | 标识分布式对象的状态，可能的取值有'online'（上线）、'offline'（下线）和'restore'（恢复）。 |

## ProgressObserver<sup>20+</sup>

type ProgressObserver = (sessionId: string, progress: number) => void

定义传输进度的监听回调函数。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| sessionId | string | 是 | 标识变更对象的sessionId。长度不大于128字节，且只能包含字母、数字或下划线_。 |
| progress    | number | 是 | 标识资产传输进度。取值范围为[-1, 100]，取值为整数，-1表示获取进度失败，100表示传输完成。 |

## DataObject

表示一个分布式数据对象。在使用以下接口前，需调用[create()](#distributeddataobjectcreate9)获取DataObject对象。

### setSessionId<sup>9+</sup>

setSessionId(sessionId: string, callback: AsyncCallback&lt;void&gt;): void

设置sessionId，使用callback方式异步回调。当可信组网中有多个设备处于协同状态时，如果多个设备间的分布式对象设置为同一个sessionId，就能自动同步。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

  | 参数名    | 类型                      | 必填 | 说明                                                                                                           |
  | --------- | ------------------------- | ---- | -------------------------------------------------------------------------------------------------------------- |
  | sessionId | string                    | 是   | 分布式数据对象在可信组网中的标识ID，长度不大于128，且只能包含字母数字或下划线_。当传入""、null时表示退出分布式组网。 |
  | callback  | AsyncCallback&lt;void&gt; | 是   | 加入session的异步回调。                                                                                        |

**错误码：**

  以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[分布式数据对象错误码](errorcode-distributed-dataObject.md)。

  | 错误码ID | 错误信息                                                                                                                                                           |
  | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
  | 201      | Permission verification failed.                                                                                                                                    |
  | 401      | Parameter error. Possible causes: 1. Incorrect parameter types; 2. The sessionId allows only letters, digits, and underscores(_), and cannot exceed 128 in length. |
  | 15400001 | Failed to create the in-memory database.                                                                                                                                               |

**示例：**

```ts
// g_object加入分布式组网
g_object.setSessionId(distributedDataObject.genSessionId(), ()=>{
    console.info("join session");
});
// g_object退出分布式组网
g_object.setSessionId("", ()=>{
    console.info("leave all session");
});
```

### setSessionId<sup>9+</sup>

setSessionId(callback: AsyncCallback&lt;void&gt;): void

退出所有已加入的session，使用callback方式异步回调。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;void&gt; | 是 | 退出所有已加入session的异步回调。 |

**错误码：**

  以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[分布式数据对象错误码](errorcode-distributed-dataObject.md)。

  | 错误码ID | 错误信息 |
  | -------- | -------- |
  | 401      | Parameter error. Incorrect parameter types. |
  | 15400001 | Failed to create the in-memory database. |

**示例：**

```ts
// g_object加入分布式组网
g_object.setSessionId(distributedDataObject.genSessionId(), ()=>{
    console.info("join session");
});
// 退出分布式组网
g_object.setSessionId(() => {
    console.info("leave all session.");
});
```

### setSessionId<sup>9+</sup>

setSessionId(sessionId?: string): Promise&lt;void&gt;

设置sessionId或退出分布式组网，使用Promise异步回调。当传入""、null或不传入参数时，表示退出分布式组网。当可信组网中有多个设备处于协同状态时，如果多个设备间的分布式对象设置为同一个sessionId，就能自动同步。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

  | 参数名    | 类型   | 必填 | 说明                                                                                                                         |
  | --------- | ------ | ---- | ---------------------------------------------------------------------------------------------------------------------------- |
  | sessionId | string | 否   | 分布式数据对象在可信组网中的标识ID，长度不大于128，且只能包含字母数字或下划线_。当传入""、null或不传入参数时表示退出分布式组网。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象。|

**错误码：**

  以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[分布式数据对象错误码](errorcode-distributed-dataObject.md)。

  | 错误码ID | 错误信息                                                                                                                                                           |
  | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
  | 201      | Permission verification failed.                                                                                                                                    |
  | 401      | Parameter error. Possible causes: 1. Incorrect parameter types; 2. The sessionId allows only letters, digits, and underscores(_), and cannot exceed 128 in length. |
  | 15400001 | Failed to create the in-memory database.                                                                                                                                               |

**示例：**

```ts
// g_object加入分布式组网
g_object.setSessionId(distributedDataObject.genSessionId()).then (()=>{
    console.info("join session.");
    }).catch((error: BusinessError)=>{
        console.error("error:" + error.code + error.message);
});
// 退出分布式组网
g_object.setSessionId().then (()=>{
    console.info("leave all session.");
    }).catch((error: BusinessError)=>{
        console.error("error:" + error.code + error.message);
});
```

### on('change')<sup>9+</sup>

on(type: 'change', callback: (sessionId: string, fields: Array&lt;string&gt;) => void): void

监听分布式数据对象的数据变更。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 事件类型，固定为'change'，表示数据变更。 |
| callback | (sessionId: string, fields: Array&lt;string&gt;) => void  | 是 | 变更回调对象实例。<br>sessionId：标识变更对象的sessionId； <br>fields：标识对象变更的属性名。 |

**错误码：**

  以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

  | 错误码ID | 错误信息 |
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例：**

```ts
g_object.on("change", (sessionId: string, fields: Array<string>) => {
    console.info("change" + sessionId);
    if (g_object != null && fields != null && fields != undefined) {
        for (let index: number = 0; index < fields.length; index++) {
            console.info("changed !" + fields[index] + " " + g_object[fields[index]]);
        }
    }
});
```

### off('change')<sup>9+</sup>

off(type: 'change', callback?: (sessionId: string, fields: Array&lt;string&gt;) => void): void

当不再进行数据变更监听时，使用此接口删除对象的变更监听。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 事件类型，固定为'change'，表示数据变更。 |
| callback | (sessionId: string, fields: Array&lt;string&gt;) => void  | 否 | 需要删除的数据变更回调，若不设置则删除该对象所有的数据变更回调。<br>sessionId：标识变更对象的sessionId； <br>fields：标识对象变更的属性名。 |

**错误码：**

  以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

  | 错误码ID | 错误信息 |
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例：**

```ts
// 删除数据变更回调changeCallback
g_object.off("change", (sessionId: string, fields: Array<string>) => {
    console.info("change" + sessionId);
    if (g_object != null && fields != null && fields != undefined) {
        for (let index: number = 0; index < fields.length; index++) {
            console.info("changed !" + fields[index] + " " + g_object[fields[index]]);
        }
    }
});
// 删除所有的数据变更回调
g_object.off("change");
```

### on('status')<sup>9+</sup>

on(type: 'status', callback: (sessionId: string, networkId: string, status: 'online' \| 'offline' ) => void): void

监听分布式数据对象的上下线。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 事件类型，固定为'status'，表示对象上下线。 |
| callback | (sessionId: string, networkId: string, status: 'online' \| 'offline' ) => void | 是 | 监听上下线回调实例。<br>sessionId：标识变更对象的sessionId； <br>networkId：标识对象设备； <br>status：标识对象为'online'(上线)或'offline'(下线)的状态。 |

**错误码：**

  以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

  | 错误码ID | 错误信息 |
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例：**

```ts
g_object.on("status", (sessionId: string, networkId: string, status: 'online' | 'offline') => {
    console.info("status changed " + sessionId + " " + status + " " + networkId);
});
```

### off('status')<sup>9+</sup>

off(type: 'status', callback?:(sessionId: string, networkId: string, status: 'online' \| 'offline') => void): void

当不再进行对象上下线监听时，使用此接口删除对象的上下线监听。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 事件类型，固定为'status'，表示对象上下线。 |
| callback | (sessionId: string, networkId: string, status: 'online' \| 'offline' ) => void | 否 | 需要删除的上下线回调，若不设置则删除该对象所有的上下线回调。<br>sessionId：标识变更对象的sessionId； <br>networkId：标识变更对象； <br>status：标识对象为'online'(上线)或'offline'(下线)的状态。 |

**错误码：**

  以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

  | 错误码ID | 错误信息 |
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例：**

```ts
// 删除上下线回调changeCallback
g_object.off("status", (sessionId: string, networkId: string, status: 'online' | 'offline') => {
    console.info("status changed " + sessionId + " " + status + " " + networkId);
});
// 删除所有的上下线回调
g_object.off("status");
```

### save<sup>9+</sup>

save(deviceId: string, callback: AsyncCallback&lt;SaveSuccessResponse&gt;): void

保存分布式数据对象。使用callback方式异步回调。

对象数据保存成功后，当应用存在时不会释放对象数据，当应用退出后，重新进入应用时，恢复保存在设备上的数据。

有以下几种情况时，保存的数据将会被释放：

- 存储时间超过24小时。
- 应用卸载。
- 成功恢复数据之后。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | deviceId | string | 是 | 保存数据的deviceId，当deviceId为"local"，代表存储在本地设备。 |
  | callback | AsyncCallback&lt;[SaveSuccessResponse](#savesuccessresponse9)&gt; | 是 | 回调函数。返回SaveSuccessResponse，包含sessionId、version、deviceId等信息。 |

**错误码：**

  以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

  | 错误码ID | 错误信息 |
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
  | 801      | Capability not supported. |

**示例：**

```ts
g_object.setSessionId("123456");
g_object.save("local", (err: BusinessError, result:distributedDataObject.SaveSuccessResponse) => {
    if (err) {
        console.error("save failed, error code = " + err.code);
        console.error("save failed, error message: " + err.message);
        return;
    }
    console.info("save callback");
    console.info("save sessionId: " + result.sessionId);
    console.info("save version: " + result.version);
    console.info("save deviceId:  " + result.deviceId);
});
```

### save<sup>9+</sup>

save(deviceId: string): Promise&lt;SaveSuccessResponse&gt;

保存分布式数据对象。使用Promise方式作为异步回调。

对象数据保存成功后，当应用存在时不会释放对象数据，当应用退出后，重新进入应用时，恢复保存在设备上的数据。

有以下几种情况时，保存的数据将会被释放：

- 存储时间超过24小时。
- 应用卸载。
- 成功恢复数据之后。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | deviceId | string | 是 | 保存数据的设备号，当deviceId默认为"local"，标识需要保存对象的设备。 |

**返回值：**

  | 类型 | 说明 |
  | -------- | -------- |
  | Promise&lt;[SaveSuccessResponse](#savesuccessresponse9)&gt; | Promise对象。返回SaveSuccessResponse，包含sessionId、version、deviceId等信息。|

**错误码：**

  以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

  | 错误码ID | 错误信息 |
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
  | 801      | Capability not supported. |

**示例：**

```ts
g_object.setSessionId("123456");
g_object.save("local").then((callbackInfo: distributedDataObject.SaveSuccessResponse) => {
    console.info("save callback");
    console.info("save sessionId " + callbackInfo.sessionId);
    console.info("save version " + callbackInfo.version);
    console.info("save deviceId " + callbackInfo.deviceId);
}).catch((err: BusinessError) => {
    console.error("save failed, error code = " + err.code);
    console.error("save failed, error message: " + err.message);
});
```

### revokeSave<sup>9+</sup>

revokeSave(callback: AsyncCallback&lt;RevokeSaveSuccessResponse&gt;): void

撤回保存的分布式数据对象。使用callback方式作为异步方法。

如果对象保存在本地设备，那么将删除所有受信任设备上所保存的数据。
如果对象保存在其他设备，那么将删除本地设备上的数据。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;[RevokeSaveSuccessResponse](#revokesavesuccessresponse9)&gt; | 是 | 回调函数。返回RevokeSaveSuccessResponse，包含sessionId。 |

**错误码：**

  以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

  | 错误码ID | 错误信息 |
  | -------- | -------- |
  | 401      | Parameter error. Incorrect parameter types. |
  | 801      | Capability not supported. |

**示例：**

```ts
g_object.setSessionId("123456");
// 持久化数据
g_object.save("local", (err: BusinessError, result: distributedDataObject.SaveSuccessResponse) => {
    if (err) {
        console.error("save failed, error code = " + err.code);
        console.error("save failed, error message: " + err.message);
        return;
    }
    console.info("save callback");
    console.info("save sessionId: " + result.sessionId);
    console.info("save version: " + result.version);
    console.info("save deviceId:  " + result.deviceId);
});
// 删除持久化保存的数据
g_object.revokeSave((err: BusinessError, result: distributedDataObject.RevokeSaveSuccessResponse) => {
    if (err) {
      console.error("revokeSave failed, error code = " + err.code);
      console.error("revokeSave failed, error message: " + err.message);
      return;
    }
    console.info("revokeSave callback");
    console.info("revokeSave sessionId " + result.sessionId);
});
```

### revokeSave<sup>9+</sup>

revokeSave(): Promise&lt;RevokeSaveSuccessResponse&gt;

撤回保存的分布式数据对象。使用Promise方式作为异步方法。

如果对象保存在本地设备，那么将删除所有受信任设备上所保存的数据。
如果对象保存在其他设备，那么将删除本地设备上的数据。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**返回值：**

  | 类型 | 说明 |
  | -------- | -------- |
  | Promise&lt;[RevokeSaveSuccessResponse](#revokesavesuccessresponse9)&gt; | Promise对象。返回RevokeSaveSuccessResponse，包含sessionId。 |

**错误码：**

  以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

  | 错误码ID | 错误信息 |
  | -------- | -------- |
  | 801      | Capability not supported. |

**示例：**

```ts
g_object.setSessionId("123456");
// 持久化数据
g_object.save("local").then((result: distributedDataObject.SaveSuccessResponse) => {
    console.info("save callback");
    console.info("save sessionId " + result.sessionId);
    console.info("save version " + result.version);
    console.info("save deviceId " + result.deviceId);
}).catch((err: BusinessError) => {
    console.error("save failed, error code = " + err.code);
    console.error("save failed, error message: " + err.message);
});
// 删除持久化保存的数据
g_object.revokeSave().then((result: distributedDataObject.RevokeSaveSuccessResponse) => {
    console.info("revokeSave callback");
    console.info("sessionId" + result.sessionId);
}).catch((err: BusinessError)=> {
    console.error("revokeSave failed, error code = " + err.code);
    console.error("revokeSave failed, error message = " + err.message);
});
```

### bindAssetStore<sup>11+</sup>

bindAssetStore(assetKey: string, bindInfo: BindInfo, callback: AsyncCallback&lt;void&gt;): void

绑定分布式对象中的单个资产与其对应的数据库信息，当前版本只支持分布式对象中的资产与关系型数据库的绑定。使用callback方式异步回调。

当分布式对象中包含的资产和关系型数据库中包含的资产指向同一个实体资产文件，即两个资产的Uri相同时，就会存在冲突，我们把这种资产称为融合资产。如果需要分布式数据管理进行融合资产的冲突解决，需要先进行资产的绑定。当应用退出session后，绑定关系随之消失。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

  | 参数名   | 类型                      | 必填 | 说明                                                                               |
  | -------- | ------------------------- | ---- | ---------------------------------------------------------------------------------- |
  | assetKey | string                    | 是   | 待绑定的融合资产在分布式对象中的键值。                                             |
  | bindInfo | [BindInfo](#bindinfo11)   | 是   | 待绑定的融合资产在数据库中的信息，包含库名、表名、主键、列名及在数据库中的资产名。 |
  | callback | AsyncCallback&lt;void&gt; | 是   | 绑定数据库的回调。                                                                 |

**错误码：**

  以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

  | 错误码ID | 错误信息 |
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
  | 801      | Capability not supported. |

**示例：**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { commonType } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

class Note {
  title: string | undefined
  text: string | undefined
  attachment: commonType.Asset | undefined

  constructor(title: string | undefined, text: string | undefined, attachment: commonType.Asset | undefined) {
    this.title = title;
    this.text = text;
    this.attachment = attachment;
  }
}

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let attachment: commonType.Asset = {
      name: 'test_img.jpg',
      uri: 'file://com.example.myapplication/data/storage/el2/distributedfiles/dir/test_img.jpg',
      path: '/dir/test_img.jpg',
      createTime: '2024-01-02 10:00:00',
      modifyTime: '2024-01-02 10:00:00',
      size: '5',
      status: commonType.AssetStatus.ASSET_NORMAL
    }
    let note: Note = new Note('test', 'test', attachment);
    let g_object: distributedDataObject.DataObject = distributedDataObject.create(this.context, note);
    g_object.setSessionId('123456');

    const bindInfo: distributedDataObject.BindInfo = {
      storeName: 'notepad',
      tableName: 'note_t',
      primaryKey: {
        'uuid': '00000000-0000-0000-0000-000000000000'
      },
      field: 'attachment',
      assetName: attachment.name as string
    }

    g_object.bindAssetStore('attachment', bindInfo, (err: BusinessError) => {
      if (err) {
        console.error('bindAssetStore failed.');
      }
      console.info('bindAssetStore success.');
    });
  }
}
```

### bindAssetStore<sup>11+</sup>

bindAssetStore(assetKey: string, bindInfo: BindInfo): Promise&lt;void&gt;

绑定分布式对象中的单个资产与其对应的数据库信息，当前版本只支持分布式对象中的资产与关系型数据库的绑定。使用Promise方式作为异步回调。

当分布式对象中包含的资产和关系型数据库中包含的资产指向同一个实体资产文件，即两个资产的Uri相同时，就会存在冲突，我们把这种资产称为融合资产。如果需要分布式数据管理进行融合资产的冲突解决，需要先进行资产的绑定。当应用退出session后，绑定关系随之消失。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

  | 参数名   | 类型                    | 必填 | 说明                                                                               |
  | -------- | ----------------------- | ---- | ---------------------------------------------------------------------------------- |
  | assetKey | string                  | 是   | 待绑定的融合资产在分布式对象中的键值。                                             |
  | bindInfo | [BindInfo](#bindinfo11) | 是   | 待绑定的融合资产在数据库中的信息，包含库名、表名、主键、列名及在数据库中的资产名。 |

**返回值：**

  | 类型                | 说明          |
  | ------------------- | ------------- |
  | Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

  以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

  | 错误码ID | 错误信息 |
  | -------- | -------- |
  | 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
  | 801      | Capability not supported. |

**示例：**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { commonType } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

class Note {
  title: string | undefined
  text: string | undefined
  attachment: commonType.Asset | undefined

  constructor(title: string | undefined, text: string | undefined, attachment: commonType.Asset | undefined) {
    this.title = title;
    this.text = text;
    this.attachment = attachment;
  }
}

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let attachment: commonType.Asset = {
      name: 'test_img.jpg',
      uri: 'file://com.example.myapplication/data/storage/el2/distributedfiles/dir/test_img.jpg',
      path: '/dir/test_img.jpg',
      createTime: '2024-01-02 10:00:00',
      modifyTime: '2024-01-02 10:00:00',
      size: '5',
      status: commonType.AssetStatus.ASSET_NORMAL
    }
    let note: Note = new Note('test', 'test', attachment);
    let g_object: distributedDataObject.DataObject = distributedDataObject.create(this.context, note);
    g_object.setSessionId('123456');

    const bindInfo: distributedDataObject.BindInfo = {
      storeName: 'notepad',
      tableName: 'note_t',
      primaryKey: {
        'uuid': '00000000-0000-0000-0000-000000000000'
      },
      field: 'attachment',
      assetName: attachment.name as string
    }

    g_object.bindAssetStore("attachment", bindInfo).then(() => {
      console.info('bindAssetStore success.');
    }).catch((err: BusinessError) => {
      console.error("bindAssetStore failed, error code = " + err.code);
    });
  }
}
```

### on('change')<sup>20+</sup>

on(type: 'change', callback: DataObserver): void

监听分布式对象的数据变更。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 事件类型，固定为'change'，表示数据变更。 |
| callback | [DataObserver](#dataobserver20) | 是 | 表示分布式对象数据变更的回调实例。 |

**示例：**

```ts
const changeCallback1: distributedDataObject.DataObserver = (sessionId: string, fields: Array<string>) => {
  console.info("change callback1 " + sessionId);
  if (fields != null && fields != undefined) {
      for (let index: number = 0; index < fields.length; index++) {
          console.info("change !" + fields[index]);
      }
  }
}
try {
  g_object.on("change", changeCallback1);
} catch (error) {
  console.error("Execute failed, error code =  " + error.code);
}
```

### off('change')<sup>20+</sup>

off(type: 'change', callback?: DataObserver): void

当不再进行数据变更监听时，使用此接口删除分布式对象数据变更监听的回调实例。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 事件类型，固定为'change'，表示数据变更。 |
| callback | [DataObserver](#dataobserver20) | 否 | 需要删除的数据变更回调实例，若不设置则删除该对象所有的数据变更回调实例。 |

**示例：**

```ts
const changeCallback1: distributedDataObject.DataObserver = (sessionId: string, fields: Array<string>) => {
  console.info("change callback1 " + sessionId);
  if (fields != null && fields != undefined) {
      for (let index: number = 0; index < fields.length; index++) {
          console.info("change !" + fields[index]);
      }
  }
}

const changeCallback2: distributedDataObject.DataObserver = (sessionId: string, fields: Array<string>) => {
  console.info("change callback2 " + sessionId);
  if (fields != null && fields != undefined) {
      for (let index: number = 0; index < fields.length; index++) {
          console.info("change !" + fields[index]);
      }
  }
}

try {
  // 删除单个数据变更回调函数
  g_object.on("change", changeCallback1);
  g_object.off("change", changeCallback1);

  // 删除所有数据变更回调函数
  g_object.on("change", changeCallback1);
  g_object.on("change", changeCallback2);
  g_object.off("change");
} catch (error) {
  console.error("Execute failed, error code =  " + error.code);
}
```

### on('status')<sup>20+</sup>

on(type: 'status', callback: StatusObserver): void

监听分布式对象的状态变更。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 事件类型，固定为'status'，表示分布式对象状态变更事件。 |
| callback | [StatusObserver](#statusobserver20) | 是 | 表示分布式对象状态变更的回调实例。 |

**示例：**

```ts
const statusCallback1: distributedDataObject.StatusObserver = (sessionId: string, networkId: string, status: string) => {
  console.info("status callback " + sessionId);
}
try {
  g_object.on("status", statusCallback1);
} catch (error) {
  console.error("Execute failed, error code =  " + error.code);
}
```

### off('status')<sup>20+</sup>

off(type: 'status', callback?: StatusObserver): void

当不再进行分布式对象状态变更监听时，使用此接口删除分布式对象状态变更的回调实例。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 事件类型，固定为'status'，表示数据对象状态变更事件。 |
| callback | [StatusObserver](#statusobserver20) | 否 | 需要删除状态变更的回调实例，若不设置则删除该对象所有的状态变更回调实例。 |

**示例：**

```ts
const statusCallback1: distributedDataObject.StatusObserver = (sessionId: string, networkId: string, status: string) => {
  console.info("status callback1" + sessionId);
}

const statusCallback2: distributedDataObject.StatusObserver = (sessionId: string, networkId: string, status: string) => {
  console.info("status callback2" + sessionId);
}
try {
  // 删除单个状态变更回调函数
  g_object.on("status", statusCallback1);
  g_object.off("status", statusCallback1);

  // 删除所有状态变更回调函数
  g_object.on("status", statusCallback1);
  g_object.on("status", statusCallback2);
  g_object.off("status");
} catch (error) {
  console.error("Execute failed, error code =  " + error.code);
}
```

### on('progressChanged')<sup>20+</sup>

on(type: 'progressChanged', callback: ProgressObserver): void

监听资产传输进度。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 事件类型，固定为'progressChanged'，表示资产传输进度变化事件。 |
| callback | [ProgressObserver](#progressobserver20) | 是 | 表示资产传输进度变化的回调实例。 |

**示例：**

```ts
const progressChangedCallback: distributedDataObject.ProgressObserver = (sessionId: string, progress: number) => {
  console.info("progressChanged callback" + sessionId);
  console.info("progressChanged callback" + progress);
}
try {
  g_object.on("progressChanged", progressChangedCallback);
} catch (error) {
  console.error("Execute failed, error code =  " + error.code);
}
```

### off('progressChanged')<sup>20+</sup>

off(type: 'progressChanged', callback?: ProgressObserver): void

当不再进行资产传输进度监听时，使用此接口取消监听。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 事件类型，固定为'progressChanged'，表示资产传输进度变化事件。 |
| callback | [ProgressObserver](#progressobserver20) | 否 | 需要取消监听的事件回调，若不设置，则取消对该事件的所有监听。 |

**示例：**

```ts
const progressChangedCallback1: distributedDataObject.ProgressObserver = (sessionId: string, progress: number) => {
  console.info("progressChanged callback1" + sessionId);
  console.info("progressChanged callback1" + progress);
}

const progressChangedCallback2: distributedDataObject.ProgressObserver = (sessionId: string, progress: number) => {
  console.info("progressChanged callback2" + sessionId);
  console.info("progressChanged callback2" + progress);
}
try {
  g_object.on("progressChanged", progressChangedCallback1);
  // 取消对资产传输进度的监听
  g_object.off("progressChanged", progressChangedCallback1);

  g_object.on("progressChanged", progressChangedCallback1);
  g_object.on("progressChanged", progressChangedCallback2);
  //取消对资产传输进度的所有监听
  g_object.off("progressChanged");
} catch (error) {
  console.error("Execute failed, error code =  " + error.code);
}
```
### setAsset<sup>20+</sup>

setAsset(assetKey: string, uri: string): Promise&lt;void&gt;

设置分布式对象中的单个资产的属性信息，该接口必须在[setSessionId](#setsessionid9-2)接口调用前使用。使用Promise异步回调。

> **注意：**
>
> 在设置资产时必须保证assetKey存在且对应文件为资产类型文件，否则无法保证对端能接收到此次设置的资产。
>
> 在设置资产时必须保证uri为正确且真实存在的分布式路径，否则无法保证对端能接收到此次设置的资产。

有以下几种异常场景:

  | 触发条件  | 操作结果 |
  | -------- | -------- |
  | 调用[setSessionId](#setsessionid9-2)接口设置sessionId后再调用[setAsset](#setasset20)接口设置资产。   | 设置资产失败，抛出15400003异常。 |
  | assetKey为无效值，例如：null（不存在）、undefined（未定义）或''（空字符串）。            | 设置资产失败，抛出15400002异常。 |
  | assetKey存在、对应文件为非资产类型。 | 系统会强制修改该字段对应的文件类型为资产类型且设置资产字段，可能出现真实资产无法同步至对端设备。 |
  | uri为无效值，例如：null（不存在）、undefined（未定义）或''（空字符串）。                  | 设置资产失败，抛出15400002异常。 |


**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

  | 参数名   | 类型                    | 必填 | 说明                                                                               |
  | -------- | ----------------------- | ---- | ---------------------------------------------------------------------------------- |
  | assetKey | string                  | 是   | 分布式对象中资产类型数据对应的属性名。<br/>**使用约束：** <br/>（1）提供的assetKey对应的文件必须已存在且类型为资产[Asset](js-apis-data-commonType.md#asset)，才可进行正确的设置资产。若assetKey对应文件不存在或文件存在但类型不是资产类型，可能会出现资产设置错误。<br/>（2）在协同或接续场景下需要双端满足assetKey对应的文件存在且为资产类型，才可将设置的资产同步到对端设备。                                             |
  | uri      | string                  | 是   | 待设置的新资产的uri，表示该资产的存放的分布式路径。必须为真实存在的资产对应的分布式路径。 |

**返回值：**

  | 类型                | 说明          |
  | ------------------- | ------------- |
  | Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

  以下错误码的详细介绍请参见[分布式数据对象错误码](errorcode-distributed-dataObject.md)。

  | 错误码ID | 错误信息 |
  | -------- | -------- |
  | 15400002 | Parameter error. Possible causes: 1. The assetKey is invalid, such as ""; 2. The uri is invalid, such as "". |
  | 15400003 | The sessionId of the distributed object has been set. |

**示例:**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { commonType, distributedDataObject } from '@kit.ArkData';

class Note {
  title: string | undefined
  text: string | undefined
  attachment: commonType.Asset | undefined

  constructor(title: string | undefined, text: string | undefined, attachment: commonType.Asset | undefined) {
    this.title = title;
    this.text = text;
    this.attachment = attachment;
  }
}

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let attachment: commonType.Asset = {
      name: 'test_img.jpg',
      uri: 'file://com.example.myapplication/data/storage/el2/distributedfiles/dir/test_img.jpg',
      path: '/dir/test_img.jpg',
      createTime: '2024-01-02 10:00:00',
      modifyTime: '2024-01-02 10:00:00',
      size: '5',
      status: commonType.AssetStatus.ASSET_NORMAL
    }
    let note: Note = new Note('test', 'test', attachment);
    let g_object: distributedDataObject.DataObject = distributedDataObject.create(this.context, note);

    let uri = "file://test/test.img";
    g_object.setAsset("attachment", uri).then(() => {
      console.info('setAsset success.');
    }).catch((err: BusinessError) => {
      console.error("setAsset failed, error code = " + err.code);
    });
  }
}
```

### setAssets<sup>20+</sup>

setAssets(assetsKey: string, uris: Array&lt;string&gt;): Promise&lt;void&gt;

设置分布式对象中的多个资产的属性信息，该接口必须在[setSessionId](#setsessionid9-2)接口调用前使用。uris数组的数量范围为1-50。使用Promise异步回调。

> **注意：**
>
> 在设置资产时必须保证assetsKey存在且对应文件为资产类型文件，否则无法保证对端能接收到此次设置的资产。
>
> 在设置资产时必须保证uris数组内uri均为正确且真实存在的分布式路径，否则无法保证对端能接收到此次设置的资产。

有以下几种异常场景:

  | 触发条件  | 操作结果 |
  | -------- | -------- |
  | 调用[setSessionId](#setsessionid9-2)接口设置sessionId后再调用[setAssets](#setassets20)接口设置资产。   | 设置资产失败，抛出15400003异常。 |
  | assetsKey为无效值，例如：null（不存在）、undefined（未定义）或''（空字符串）。            | 设置资产失败，抛出15400002异常。 |
  | assetsKey存在、对应文件为非资产类型。 | 系统会强制修改该字段对应的文件类型为资产类型且设置资产字段，可能出现真实资产无法同步至对端设备。 |
  | assetsKey存在、且对应文件为资产类型。 | 设置资产成功、更新uri信息。 |
  | uris数组uri元素数量为0或超过50（不包含50）个字符。     | 设置资产失败，抛出15400002异常。 |
  | uris数组uri元素数量为1-50之间，存在单个或多个uri无效，例如：null（不存在）、undefined（未定义）或''（空字符串）。| 设置资产失败，抛出15400002异常。 |

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

  | 参数名   | 类型                    | 必填 | 说明                                                                               |
  | -------- | ----------------------- | ---- | ---------------------------------------------------------------------------------- |
  | assetsKey | string                 | 是   | 分布式对象中资产数组类型数据对应的属性名。<br/>**使用约束：** <br/>（1）提供的assetsKey对应的文件已存在且类型必须为资产[Asset](js-apis-data-commonType.md#asset)，才可进行正确的设置资产。若assetsKey对应文件不存在或文件存在但类型不是资产类型，可能会出现资产设置错误。<br/>（2）在协同或接续场景下需要双端满足assetsKey对应的文件存在且为资产类型，才可将设置的资产数组同步到对端设备。                                             |
  | uris      | Array&lt;string&gt;    | 是   | 待设置的新资产数组的uri集合，表示资产数组内每个资产的存放的分布式路径。数组元素有效范围为1-50，元素uri必须为真实存在的资产对应的分布式路径。 |

**返回值：**

  | 类型                | 说明          |
  | ------------------- | ------------- |
  | Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

  以下错误码的详细介绍请参见[分布式数据对象错误码](errorcode-distributed-dataObject.md)。

  | 错误码ID | 错误信息 |
  | -------- | -------- |
  | 15400002 | Parameter error. Possible causes:1. The assetsKey is invalid, such as ""; 2. The uris is invalid, such as the length of uris is more than 50. |
  | 15400003 | The sessionId of the distributed object has been set. |

**示例:**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { commonType, distributedDataObject } from '@kit.ArkData';

class Note {
  title: string | undefined
  text: string | undefined
  attachment: commonType.Asset | undefined

  constructor(title: string | undefined, text: string | undefined, attachment: commonType.Asset | undefined) {
    this.title = title;
    this.text = text;
    this.attachment = attachment;
  }
}

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let attachment: commonType.Asset = {
      name: 'test_img.jpg',
      uri: 'file://com.example.myapplication/data/storage/el2/distributedfiles/dir/test_img.jpg',
      path: '/dir/test_img.jpg',
      createTime: '2024-01-02 10:00:00',
      modifyTime: '2024-01-02 10:00:00',
      size: '5',
      status: commonType.AssetStatus.ASSET_NORMAL
    }
    let note: Note = new Note('test', 'test', attachment);
    let g_object: distributedDataObject.DataObject = distributedDataObject.create(this.context, note);

    let uris: Array<string> = ["file://test/test_1.txt", "file://test/test_2.txt"];
    g_object.setAssets("attachment", uris).then(() => {
      console.info('setAssets success.');
    }).catch((err: BusinessError) => {
      console.error("setAssets failed, error code = " + err.code);
    });
  }
}
```

## distributedDataObject.createDistributedObject<sup>(deprecated)</sup>

createDistributedObject(source: object): DistributedObject


创建一个分布式数据对象。

> **说明：**
>
> 从 API Version 8 开始支持，从 API Version 9 开始废弃，建议使用[distributedDataObject.create](#distributeddataobjectcreate9)替代。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | source | object | 是 | 设置分布式数据对象的属性。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [DistributedObject](#distributedobjectdeprecated) | 创建完成的分布式数据对象。 |

**示例：**

```ts
class SourceObject {
    name: string
    age: number
    isVis: boolean

    constructor(name: string, age: number, isVis: boolean) {
        this.name = name
        this.age = age
        this.isVis = isVis
    }
}

let source: SourceObject = new SourceObject("jack", 18, false);
let g_object: distributedDataObject.DistributedObject = distributedDataObject.createDistributedObject(source);
```

## DistributedObject<sup>(deprecated)</sup>

表示一个分布式数据对象。在使用以下接口前，需调用[createDistributedObject()](#distributeddataobjectcreatedistributedobjectdeprecated)获取DistributedObject对象。

### setSessionId<sup>(deprecated)</sup>

setSessionId(sessionId?: string): boolean

设置sessionId。当可信组网中有多个设备处于协同状态时，如果多个设备间的分布式对象设置为同一个sessionId，就能自动同步。

> **说明：**
>
> 从 API Version 8 开始支持，从 API Version 9 开始废弃，建议使用[setSessionId](#setsessionid9)替代。

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | sessionId | string | 否 | 分布式数据对象在可信组网中的标识ID。如果要退出分布式组网，设置为""或不设置均可。 |

**返回值：**

  | 类型 | 说明 |
  | -------- | -------- |
  | boolean | true：标识设置sessionId成功。 <br>false：标识设置sessionId失败。 |

**示例：**

```ts
class SourceObject {
    name: string
    age: number
    isVis: boolean

    constructor(name: string, age: number, isVis: boolean) {
        this.name = name
        this.age = age
        this.isVis = isVis
    }
}

let source: SourceObject = new SourceObject("jack", 18, false);
let g_object: distributedDataObject.DistributedObject = distributedDataObject.createDistributedObject(source);
// g_object加入分布式组网
g_object.setSessionId(distributedDataObject.genSessionId());
// 设置为""退出分布式组网
g_object.setSessionId("");
```

### on('change')<sup>(deprecated)</sup>

on(type: 'change', callback: (sessionId: string, fields: Array&lt;string&gt;) => void): void

监听分布式数据对象的变更。

> **说明：**
>
> 从 API Version 8 开始支持，从 API Version 9 开始废弃，建议使用[on('change')](#onchange9)替代。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 事件类型，固定为'change'，表示数据变更。 |
| callback | (sessionId: string, fields: Array&lt;string&gt;) => void  | 是 | 变更回调对象实例。<br>sessionId：标识变更对象的sessionId； <br>fields：标识对象变更的属性名。 |

**示例：**

```ts
class SourceObject {
    name: string
    age: number
    isVis: boolean

    constructor(name: string, age: number, isVis: boolean) {
        this.name = name
        this.age = age
        this.isVis = isVis
    }
}

let source: SourceObject = new SourceObject("jack", 18, false);
let g_object: distributedDataObject.DistributedObject = distributedDataObject.createDistributedObject(source);
g_object.on("change", (sessionId: string, fields: Array<string>) => {
    console.info("change" + sessionId);
    if (fields != null && fields != undefined) {
        for (let index: number = 0; index < fields.length; index++) {
            console.info("changed !" + fields[index] + " " + g_object[fields[index]]);
        }
    }
});
```

### off('change')<sup>(deprecated)</sup>

off(type: 'change', callback?: (sessionId: string, fields: Array&lt;string&gt;) => void): void

当不再进行数据变更监听时，使用此接口删除对象的变更监听。

> **说明：**
>
> 从 API Version 8 开始支持，从 API Version 9 开始废弃，建议使用[off('change')](#offchange9)替代。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 事件类型，固定为'change'，表示数据变更。 |
| callback | (sessionId: string, fields: Array&lt;string&gt;) => void  | 否 | 需要删除的数据变更回调，若不设置则删除该对象所有的数据变更回调。<br>sessionId：标识变更对象的sessionId； <br>fields：标识对象变更的属性名。 |

**示例：**

```ts
class SourceObject {
    name: string
    age: number
    isVis: boolean

    constructor(name: string, age: number, isVis: boolean) {
        this.name = name
        this.age = age
        this.isVis = isVis
    }
}

let source: SourceObject = new SourceObject("jack", 18, false);
let g_object: distributedDataObject.DistributedObject = distributedDataObject.createDistributedObject(source);
// 删除数据变更回调changeCallback
g_object.off("change", (sessionId: string, fields: Array<string>) => {
    console.info("change" + sessionId);
    if (fields != null && fields != undefined) {
        for (let index: number = 0; index < fields.length; index++) {
            console.info("changed !" + fields[index] + " " + g_object[fields[index]]);
        }
    }
});
// 删除所有的数据变更回调
g_object.off("change");
```

### on('status')<sup>(deprecated)</sup>

on(type: 'status', callback: (sessionId: string, networkId: string, status: 'online' | 'offline' ) => void): void

监听分布式数据对象的上下线。

> **说明：**
>
> 从 API Version 8 开始支持，从 API Version 9 开始废弃，建议使用[on('status')](#onstatus9)替代。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 事件类型，固定为'status'，表示对象上下线。 |
| callback | (sessionId: string, networkId: string, status: 'online' \| 'offline' ) => void | 是 | 监听上下线回调实例。<br>sessionId：标识变更对象的sessionId； <br>networkId：标识对象设备； <br>status：标识对象为'online'(上线)或'offline'(下线)的状态。 |

**示例：**

```ts
class SourceObject {
    name: string
    age: number
    isVis: boolean

    constructor(name: string, age: number, isVis: boolean) {
        this.name = name
        this.age = age
        this.isVis = isVis
    }
}

let source: SourceObject = new SourceObject("jack", 18, false);
let g_object: distributedDataObject.DistributedObject = distributedDataObject.createDistributedObject(source);

g_object.on("status", (sessionId: string, networkId: string, status: 'online' | 'offline') => {
    console.info("status changed " + sessionId + " " + status + " " + networkId);
});
```

### off('status')<sup>(deprecated)</sup>

off(type: 'status', callback?: (sessionId: string, networkId: string, status: 'online' | 'offline' ) => void): void

当不再进行对象上下线监听时，使用此接口删除对象的上下线监听。

> **说明：**
>
> 从 API Version 8 开始支持，从 API Version 9 开始废弃，建议使用[off('status')](#offstatus9)替代。

**系统能力：** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | string | 是 | 事件类型，固定为'status'，表示对象上下线。 |
| callback | (sessionId: string, networkId: string, status: 'online' \| 'offline' ) => void | 否 | 需要删除的上下线回调，若不设置则删除该对象所有的上下线回调。<br>sessionId：标识变更对象的sessionId； <br>networkId：标识变更对象； <br>status：标识对象为'online'(上线)或'offline'(下线)的状态。 |


**示例：**

```ts
class SourceObject {
    name: string
    age: number
    isVis: boolean

    constructor(name: string, age: number, isVis: boolean) {
        this.name = name
        this.age = age
        this.isVis = isVis
    }
}

let source: SourceObject = new SourceObject("jack", 18, false);
let g_object: distributedDataObject.DistributedObject = distributedDataObject.createDistributedObject(source);
// 删除上下线回调changeCallback
g_object.off("status", (sessionId: string, networkId: string, status: 'online' | 'offline') => {
    console.info("status changed " + sessionId + " " + status + " " + networkId);
});
// 删除所有的上下线回调
g_object.off("status");
```