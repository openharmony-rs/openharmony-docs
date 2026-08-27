# ServiceExtensionContext（系统接口）

ServiceExtensionContext模块是ServiceExtensionAbility的上下文环境，继承自ExtensionContext。ServiceExtensionContext模块提供ServiceExtensionAbility具有的能力，包括启动、停止、绑定、解绑Ability。

> **说明：**
> 
> - 本模块接口需要在主线程中使用，不要在Worker、TaskPool等子线程中使用。

**继承/实现关系：** ServiceExtensionContext extends ExtensionContext

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## connectServiceExtensionAbility

```TypeScript
connectServiceExtensionAbility(want: Want, options: ConnectOptions): number
```

将当前Ability连接到一个ServiceExtensionAbility。仅支持在主线程调用。

> **说明：**
> 
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | Want类型参数，传入需要启动的Ability的信息，如Ability名称，Bundle名称等。 |
| options | [ConnectOptions](../../apis-ability-kit/arkts-apis/arkts-ability-connectoptions-connectoptions-i.md) | 是 | ConnectOptions类型的回调函数，返回服务连接成功、断开或连接失败后的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回一个number，后续根据这个number去断开连接。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type.<br>**适用版本：** 10+ |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 10+ |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed.<br>**适用版本：** 10+ |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires.<br>**适用版本：** 10+ |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI.<br>**适用版本：** 10+ |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out.<br>**适用版本：** 10+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want, common } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

let commRemote: rpc.IRemoteObject | null; // 断开连接时需要释放

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      bundleName: 'com.example.myapp',
      abilityName: 'MyAbility'
    };
    let options: common.ConnectOptions = {
      onConnect(elementName, remote) {
        commRemote = remote;
        console.info('----------- onConnect -----------');
      },
      onDisconnect(elementName) {
        console.info('----------- onDisconnect -----------');
      },
      onFailed(code) {
        console.error('----------- onFailed -----------');
      }
    };
    let connection: number;

    try {
      connection = this.context.connectServiceExtensionAbility(want, options);
    } catch (paramError) {
      // 处理入参错误异常
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## connectServiceExtensionAbilityWithAccount

```TypeScript
connectServiceExtensionAbilityWithAccount(want: Want, accountId: number, options: ConnectOptions): number
```

将当前Ability连接到一个指定account的ServiceExtensionAbility。仅支持在主线程调用。 该接口在Phone、Tablet中可正常调用，在其他设备类型中返回16000006错误码。

> **说明：**
> 
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。
> 
> 当accountId为当前用户时，无需进行权限校验。

**起始版本：** 9

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 启动Ability的Want信息。 |
| accountId | number | 是 | 系统账号的账号ID。 |
| options | [ConnectOptions](../../apis-ability-kit/arkts-apis/arkts-ability-connectoptions-connectoptions-i.md) | 是 | 远端对象实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回Ability连接的结果code。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type.<br>**适用版本：** 10+ |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 10+ |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed.<br>**适用版本：** 10+ |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires.<br>**适用版本：** 10+ |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI.<br>**适用版本：** 10+ |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out.<br>**适用版本：** 10+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want, common } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

let commRemote: rpc.IRemoteObject | null; // 断开连接时需要释放

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    // accountId为系统账号ID，可通过getOsAccountLocalId接口获取，此处以100为例
    let accountId = 100;
    let options: common.ConnectOptions = {
      onConnect(elementName, remote) {
        commRemote = remote;
        console.info('----------- onConnect -----------');
      },
      onDisconnect(elementName) {
        console.info('----------- onDisconnect -----------');
      },
      onFailed(code) {
        console.info('----------- onFailed -----------');
      }
    };
    let connection: number;

    try {
      connection = this.context.connectServiceExtensionAbilityWithAccount(want, accountId, options);
    } catch (paramError) {
      // 处理入参错误异常
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## disconnectServiceExtensionAbility

```TypeScript
disconnectServiceExtensionAbility(connection: number, callback: AsyncCallback<void>): void
```

将一个Ability与绑定的服务类型的Ability解绑，断开连接之后需要将连接成功时返回的remote对象置空。仅支持在主线程调用。使用callback异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connection | number | 是 | 在connectServiceExtensionAbility中返回的number。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当Ability与绑定服务类型的Ability解绑成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例**

```TypeScript
import { ServiceExtensionAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

let commRemote: rpc.IRemoteObject | null; // 断开连接时需要释放

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    // connection为connectServiceExtensionAbility中的返回值
    let connection = 1;
    try {
      this.context.disconnectServiceExtensionAbility(connection, (error: BusinessError) => {
        commRemote = null;
        if (error.code) {
          // 处理业务逻辑错误
          console.error(`disconnectServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        // 执行正常业务
        console.info('disconnectServiceExtensionAbility succeed');
      });
    } catch (paramError) {
      commRemote = null;
      // 处理入参错误异常
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## disconnectServiceExtensionAbility

```TypeScript
disconnectServiceExtensionAbility(connection: number): Promise<void>
```

将一个Ability与绑定的服务类型的Ability解绑，断开连接之后需要将连接成功时返回的remote对象置空。仅支持在主线程调用。使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connection | number | 是 | 在connectServiceExtensionAbility中返回的number。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例**

```TypeScript
import { ServiceExtensionAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

let commRemote: rpc.IRemoteObject | null; // 断开连接时需要释放

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    // connection为connectServiceExtensionAbility中的返回值
    let connection = 1;
    try {
      this.context.disconnectServiceExtensionAbility(connection)
        .then(() => {
          commRemote = null;
          // 执行正常业务
          console.info('disconnectServiceExtensionAbility succeed');
        })
        .catch((error: BusinessError) => {
          commRemote = null;
          // 处理业务逻辑错误
          console.error(`disconnectServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
        });
    } catch (paramError) {
      commRemote = null;
      // 处理入参错误异常
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## openAtomicService

```TypeScript
openAtomicService(appId: string, options?: AtomicServiceOptions): Promise<void>
```

通过应用ID，拉起原子化服务。使用Promise异步回调。

> **说明：**
> 
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 应用的唯一标识，由云端统一分配。 |
| options | [AtomicServiceOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-atomicserviceoptions-atomicserviceoptions-c.md) | 否 | 跳出式启动原子化服务所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want, AtomicServiceOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class ServiceExtension extends ServiceExtensionAbility {
  onRequest(want: Want, startId: number) {
    let appId: string = '6918661953712445909';
    let options: AtomicServiceOptions = {
      displayId: 0,
    };
    try {
      this.context.openAtomicService(appId, options)
        .then(() => {
          console.info('openAtomicService succeed');
        })
        .catch((err: BusinessError) => {
          console.error(`openAtomicService failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`openAtomicService failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## openLink

```TypeScript
openLink(link: string, options?: OpenLinkOptions): Promise<void>
```

通过AppLinking启动UIAbility。仅支持在主线程调用。使用Promise异步回调。通过在link字段中传入标准格式的URL，基于隐式Want匹配规则拉起目标UIAbility。目标方必须具备以下过滤器特征，才能处理AppLinking链接：  
- "actions"列表中包含"ohos.want.action.viewData"。  
- "entities"列表中包含"entity.system.browsable"。  
- "uris"列表中包含"scheme"为"https"且"domainVerify"为true的元素。  
传入的参数不合法时，如未设置必选参数或link字符串不是标准格式的URL，接口会直接抛出异常。参数校验通过，拉起目标方时出现的错误通过promise返回错误信息。

> **说明：**
> 
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| link | string | 是 | 指示要打开的标准格式URL。 |
| options | [OpenLinkOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-openlinkoptions-openlinkoptions-i.md) | 否 | 打开URL的选项参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Failed to start the invisible ability. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation flag is forbidden. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000019](../../apis-ability-kit/errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000136](../../apis-ability-kit/errorcode-ability.md#16000136-不允许通过app-linking方式拉起应用自身uiability) | The UIAbility is prohibited from launching itself via App Linking.<br>**适用版本：** 23+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want, OpenLinkOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

function log(info: string) {
  console.error(`[ServiceExtApp]:: ${JSON.stringify(info)}`);
}

export default class ServiceExtAbility extends ServiceExtensionAbility {
  onCreate(want: Want) {
    log(`ServiceExtAbility OnCreate`);
  }

  onRequest(want: Want, startId: number) {
    log(`ServiceExtAbility onRequest`);
    let link: string = 'https://www.example.com';
    let openLinkOptions: OpenLinkOptions = {
      appLinkingOnly: false
    };
    try {
      this.context.openLink(
        link,
        openLinkOptions
      ).then(() => {
        log(`open link success.`);
      }).catch((err: BusinessError) => {
        log(`open link failed, errCode ${JSON.stringify(err.code)}`);
      });
    }
    catch (e) {
      log(`exception occurred, errCode ${JSON.stringify(e.code)}`);
    }
  }

  onDestroy() {
    log(`ServiceExtAbility onDestroy`);
  }
}
```

## preStartMission

```TypeScript
preStartMission(bundleName: string, moduleName: string, abilityName: string, startTime: string): Promise<void>
```

打开原子化服务跳过loading框并预打开窗口，使用Promise异步回调。参数校验通过，拉起目标方时出现的错误需要通过异常机制捕获。

**起始版本：** 12

**需要权限：** ohos.permission.PRE_START_ATOMIC_SERVICE

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 打开原子化服务对应的包名。 |
| moduleName | string | 是 | 打开原子化服务对应的模块名。 |
| abilityName | string | 是 | 打开原子化服务对应的能力名。 |
| startTime | string | 是 | 打开原子化服务对应的开始时间，单位为毫秒级的时间戳。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16300007](../../apis-ability-kit/errorcode-ability.md#16300007-指定的原子化服务的下载安装任务信息不存在) | The target free-installation task does not exist. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

function log(info: string) {
  console.error(`[ServiceExtApp]:: ${JSON.stringify(info)}`);
}

export default class ServiceExtAbility extends ServiceExtensionAbility {
  onCreate(want: Want) {
    log(`ServiceExtAbility OnCreate, want: ${JSON.stringify(want)}.`);
  }

  onRequest(want: Want, startId: number) {
    log(`ServiceExtAbility onRequest`);
    try {
      if (want.parameters && want.parameters["ohos.aafwk.param.startTime"]) {
        this.context.preStartMission(
          want.bundleName,
          want.moduleName,
          want.abilityName,
          want.parameters["ohos.aafwk.param.startTime"] as string
        ).then(() => {
          log(`pre-start mission success.`);
        }).catch((err: BusinessError) => {
          log(`pre-start mission failed, errCode: ${err.code}, errMsg: ${err.message}.`);
        });
      }
    } catch (e) {
      let code = (e as BusinessError).code;
      let msg = (e as BusinessError).message;
      log(`exception occurred, errCode: ${code}, errMsg: ${msg}.`);
    }
  }

  onDestroy() {
    log(`ServiceExtAbility onDestroy`);
  }
}
```

## requestModalUIExtension

```TypeScript
requestModalUIExtension(pickerWant: Want, callback: AsyncCallback<void>): void
```

请求在指定的获焦应用上拉起对应类型的UIExtensionAbility。其中，获焦应用通过want.parameters中bundleName来指定，如果未指定获焦应用或指定的应用未获焦，则在系统界面上直接拉起 UIExtensionAbility；被拉起的UIExtensionAbility通过Want中bundleName、abilityName、moduleName字段共同确定，同时需要通过want.parameters中的 ability.want.params.uiExtensionType字段配置UIExtensionAbility的类型。仅支持在主线程调用。使用callback形式异步回调。在获焦应用上拉起UIExtensionAbility之前，必须确保该应用已完成页面初始化，否则将导致拉起失败。应用可通过监听页面加载状态来判断拉起UIExtensionAbility的时机。

> **说明：**
> 
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pickerWant | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 拉起UIExtension的Want信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当拉起UIExtension成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 11 |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist.<br>**适用版本：** 11 |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type.<br>**适用版本：** 11 |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 11 |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released.<br>**适用版本：** 11 |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class ServiceExtension extends ServiceExtensionAbility {
  onCreate() {
    let pickerWant: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'com.example.myapplication.UIExtAbility',
      moduleName: 'entry_test',
      parameters: {
        'bundleName': 'com.example.myapplication',
        // 与com.example.myapplication.UIExtAbility配置的type相同
        'ability.want.params.uiExtensionType': 'sys/commonUI'
      }
    };

    try {
      this.context.requestModalUIExtension(pickerWant, (err: BusinessError) => {
        if (err.code) {
          // 处理业务逻辑错误
          console.error(`requestModalUIExtension failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        // 执行正常业务
        console.info('requestModalUIExtension succeed');
      });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`requestModalUIExtension failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## requestModalUIExtension

```TypeScript
requestModalUIExtension(pickerWant: Want): Promise<void>
```

请求在指定的获焦应用上拉起对应类型的UIExtensionAbility。其中，获焦应用通过want.parameters中bundleName来指定，如果未指定获焦应用或指定的应用未获焦，则在系统界面上直接拉起 UIExtensionAbility；被拉起的UIExtensionAbility通过Want中bundleName、abilityName、moduleName字段共同确定，同时需要通过want.parameters中的 ability.want.params.uiExtensionType字段配置UIExtensionAbility的类型。仅支持在主线程调用。使用promise形式异步回调。在获焦应用上拉起UIExtensionAbility之前，必须确保该应用已完成页面初始化，否则将导致拉起失败。应用可通过监听页面加载状态来判断拉起UIExtensionAbility的时机。

> **说明：**
> 
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pickerWant | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 拉起UIExtension的Want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 11 |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist.<br>**适用版本：** 11 |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type.<br>**适用版本：** 11 |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 11 |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released.<br>**适用版本：** 11 |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class ServiceExtension extends ServiceExtensionAbility {
  onCreate() {
    let pickerWant: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'UIExtAbility',
      moduleName: 'entry_test',
      parameters: {
        'bundleName': 'com.example.myapplication',
        // 与com.example.myapplication.UIExtAbility配置的type相同
        'ability.want.params.uiExtensionType': 'sys/commonUI'
      }
    };

    try {
      this.context.requestModalUIExtension(pickerWant)
        .then(() => {
          // 执行正常业务
          console.info('requestModalUIExtension succeed');
        })
        .catch((err: BusinessError) => {
          // 处理业务逻辑错误
          console.error(`requestModalUIExtension failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`requestModalUIExtension failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## requestModalUIExtensionWithAccount

```TypeScript
requestModalUIExtensionWithAccount(pickerWant: Want, accountId: number): Promise<void>
```

请求指定的焦点应用程序启动对应类型的UIExtensionAbility 指定用户。焦点应用由**want.parameters**中的**bundleName**指定。如果**bundleName**   
> **说明：**
> 
> 
> 关于stage模型中组件的启动规则，请参见
> 【组件启动规则（阶段模型）】(../../../application-models/component-startup-rules.md)。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pickerWant | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 需要用于启动UIExtensionAbility的信息 |
| accountId | number | 是 | 要请求的帐户 取值范围为全体整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 不会返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1.Connect to system service failed; 2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. 4.The logical screen corresponding to the specified accountId is not in the foreground. |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class ServiceExtension extends ServiceExtensionAbility {
  onCreate(want: Want) {
    let pullUIExtWant: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'UIExtAbility',
      moduleName: 'entry_test',
      parameters: {
        'bundleName': 'com.example.myapplication',
        // 与com.example.myapplication.UIExtAbility配置的type相同
        'ability.want.params.uiExtensionType': 'sys/commonUI'
      }
    };
    // 账号ID说明：
    // 1. 示例固定值 100
    // 2. 可通过系统账号管理接口getForegroundOsAccountLocalId(displayId: number) 获取指定逻辑屏上运行的前台系统账号ID
    let accountId = 100;

    try {
      this.context.requestModalUIExtensionWithAccount(pullUIExtWant, accountId)
        .then(() => {
          // 执行正常业务
          console.info('requestModalUIExtensionWithAccount succeed');
        })
        .catch((err: BusinessError) => {
          // 处理业务逻辑错误
          console.error(`requestModalUIExtensionWithAccount failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`requestModalUIExtensionWithAccount failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## startAbility

```TypeScript
startAbility(want: Want, callback: AsyncCallback<void>): void
```

启动Ability。仅支持在主线程调用。使用callback异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | Want类型参数，传入需要启动的Ability的信息，如Ability名称，Bundle名称等。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当启动Ability成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000019](../../apis-ability-kit/errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found.<br>**适用版本：** 12+ |
| [16000073](../../apis-ability-kit/errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000071](../../apis-ability-kit/errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000072](../../apis-ability-kit/errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000076](../../apis-ability-kit/errorcode-ability.md#16000076-指定的app_instance_key不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000077](../../apis-ability-kit/errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../../apis-ability-kit/errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../../apis-ability-kit/errorcode-ability.md#16000079-不支持指定app_instance_key) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000080](../../apis-ability-kit/errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      bundleName: 'com.example.myapp',
      abilityName: 'MyAbility'
    };

    try {
      this.context.startAbility(want, (error: BusinessError) => {
        if (error.code) {
          // 处理业务逻辑错误
          console.error(`startAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        // 执行正常业务
        console.info('startAbility succeed');
      });
    } catch (paramError) {
      // 处理入参错误异常
      console.error(`error.code: ${paramError.code}, error.message: ${paramError.message}`);
    }
  }
}
```

## startAbility

```TypeScript
startAbility(want: Want, options: StartOptions, callback: AsyncCallback<void>): void
```

启动Ability。仅支持在主线程调用。使用callback异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 启动Ability的Want信息。 |
| options | [StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c.md) | 是 | 启动Ability所携带的参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当启动Ability成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000019](../../apis-ability-kit/errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found.<br>**适用版本：** 12+ |
| [16000073](../../apis-ability-kit/errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000071](../../apis-ability-kit/errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000072](../../apis-ability-kit/errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000076](../../apis-ability-kit/errorcode-ability.md#16000076-指定的app_instance_key不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000077](../../apis-ability-kit/errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../../apis-ability-kit/errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../../apis-ability-kit/errorcode-ability.md#16000079-不支持指定app_instance_key) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000080](../../apis-ability-kit/errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let options: StartOptions = {
      windowMode: 0
    };

    try {
      this.context.startAbility(want, options, (error: BusinessError) => {
        if (error.code) {
          // 处理业务逻辑错误
          console.error(`startAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        // 执行正常业务
        console.info('startAbility succeed');
      });
    } catch (paramError) {
      // 处理入参错误异常
      console.error(`error.code: ${paramError.code}, error.message: ${paramError.message}`);
    }
  }
}
```

## startAbility

```TypeScript
startAbility(want: Want, options?: StartOptions): Promise<void>
```

启动Ability。仅支持在主线程调用。使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | Want类型参数，传入需要启动的Ability的信息，如Ability名称，Bundle名称等。 |
| options | [StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c.md) | 否 | 启动Ability所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000019](../../apis-ability-kit/errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found.<br>**适用版本：** 12+ |
| [16000073](../../apis-ability-kit/errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000071](../../apis-ability-kit/errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000072](../../apis-ability-kit/errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000076](../../apis-ability-kit/errorcode-ability.md#16000076-指定的app_instance_key不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000077](../../apis-ability-kit/errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../../apis-ability-kit/errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../../apis-ability-kit/errorcode-ability.md#16000079-不支持指定app_instance_key) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000080](../../apis-ability-kit/errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      bundleName: 'com.example.myapp',
      abilityName: 'MyAbility'
    };
    let options: StartOptions = {
      windowMode: 0,
    };

    try {
      this.context.startAbility(want, options)
        .then((data: void) => {
          // 执行正常业务
          console.info('startAbility succeed');
        })
        .catch((error: BusinessError) => {
          // 处理业务逻辑错误
          console.error(`startAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
        });
    } catch (paramError) {
      // 处理入参错误异常
      console.error(`error.code: ${paramError.code}, error.message: ${paramError.message}`);
    }
  }
}
```

## startAbilityAsCaller

```TypeScript
startAbilityAsCaller(want: Want, callback: AsyncCallback<void>): void
```

使用设置的caller信息启动一个Ability，caller信息由Want携带，在系统服务层识别，Ability可以在onCreate生命周期的Want参数中获取到caller信息。使用该接口启动一个Ability时，Want的 caller信息不会被当前自身的应用信息覆盖，系统服务层可获取到初始caller的信息。仅支持在主线程调用。使用callback异步回调。

> **说明：**
> 
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 启动Ability的Want信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当启动Ability成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000073](../../apis-ability-kit/errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000071](../../apis-ability-kit/errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000072](../../apis-ability-kit/errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000076](../../apis-ability-kit/errorcode-ability.md#16000076-指定的app_instance_key不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000077](../../apis-ability-kit/errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../../apis-ability-kit/errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../../apis-ability-kit/errorcode-ability.md#16000079-不支持指定app_instance_key) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000080](../../apis-ability-kit/errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate(want: Want) {
    // want包含启动该应用的Caller信息
    let localWant: Want = want;
    localWant.bundleName = 'com.example.demo';
    localWant.moduleName = 'entry';
    localWant.abilityName = 'TestAbility';

    // 使用启动方的Caller身份信息启动新Ability
    this.context.startAbilityAsCaller(localWant, (err) => {
      if (err && err.code != 0) {
        console.error(`startAbilityAsCaller failed, err: ${JSON.stringify(err)}`);
      } else {
        console.info('startAbilityAsCaller success.');
      }
    })
  }
}
```

## startAbilityAsCaller

```TypeScript
startAbilityAsCaller(want: Want, options: StartOptions, callback: AsyncCallback<void>): void
```

使用设置的caller信息启动一个Ability，caller信息由Want携带，在系统服务层识别，Ability可以在onCreate生命周期的Want参数中获取到caller信息。使用该接口启动一个Ability时，Want的 caller信息不会被当前自身的应用信息覆盖，系统服务层可获取到初始caller的信息。仅支持在主线程调用。使用callback异步回调。

> **说明：**
> 
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 启动Ability的Want信息。 |
| options | [StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c.md) | 是 | 启动Ability所携带的参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当启动Ability成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000073](../../apis-ability-kit/errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000071](../../apis-ability-kit/errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000072](../../apis-ability-kit/errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000076](../../apis-ability-kit/errorcode-ability.md#16000076-指定的app_instance_key不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000077](../../apis-ability-kit/errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../../apis-ability-kit/errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../../apis-ability-kit/errorcode-ability.md#16000079-不支持指定app_instance_key) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000080](../../apis-ability-kit/errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate(want: Want) {
    // want包含启动该应用的Caller信息
    let localWant: Want = want;
    localWant.bundleName = 'com.example.demo';
    localWant.moduleName = 'entry';
    localWant.abilityName = 'TestAbility';

    let option: StartOptions = {
      displayId: 0
    }

    // 使用启动方的Caller身份信息启动新Ability
    this.context.startAbilityAsCaller(localWant, option, (err) => {
      if (err && err.code != 0) {
        console.error(`startAbilityAsCaller failed, err: ${JSON.stringify(err)}`);
      } else {
        console.info('startAbilityAsCaller success.');
      }
    })
  }
}
```

## startAbilityAsCaller

```TypeScript
startAbilityAsCaller(want: Want, options?: StartOptions): Promise<void>
```

使用设置的caller信息启动一个Ability，caller信息由Want携带，在系统服务层识别，Ability可以在onCreate生命周期的Want参数中获取到caller信息。使用该接口启动一个Ability时，Want的 caller信息不会被当前自身的应用信息覆盖，系统服务层可获取到初始caller的信息。仅支持在主线程调用。使用Promise异步回调。

> **说明：**
> 
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 启动Ability的Want信息。 |
| options | [StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c.md) | 否 | 启动Ability所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000073](../../apis-ability-kit/errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000071](../../apis-ability-kit/errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000072](../../apis-ability-kit/errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000076](../../apis-ability-kit/errorcode-ability.md#16000076-指定的app_instance_key不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000077](../../apis-ability-kit/errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../../apis-ability-kit/errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../../apis-ability-kit/errorcode-ability.md#16000079-不支持指定app_instance_key) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000080](../../apis-ability-kit/errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate(want: Want) {
    // want包含启动该应用的Caller信息
    let localWant: Want = want;
    localWant.bundleName = 'com.example.demo';
    localWant.moduleName = 'entry';
    localWant.abilityName = 'TestAbility';

    let option: StartOptions = {
      displayId: 0
    };

    // 使用启动方的Caller身份信息启动新Ability
    this.context.startAbilityAsCaller(localWant, option)
      .then(() => {
        console.info('startAbilityAsCaller success.');
      })
      .catch((err: BusinessError) => {
        console.error(`startAbilityAsCaller failed, err: ${JSON.stringify(err)}`);
      })
  }
}
```

## startAbilityByCall

```TypeScript
startAbilityByCall(want: Want): Promise<Caller>
```

启动指定Ability至前台或后台，同时获取其Caller通信接口，调用方可使用Caller与被启动的Ability进行通信。仅支持在主线程调用。使用Promise异步回调。该接口不支持拉起启动模式为[specified模式](../../../application-models/uiability-launch-type.md#specified启动模式)的UIAbility。使用规则：  
- 调用方应用位于后台时，使用该接口启动Ability需申请`ohos.permission.START_ABILITIES_FROM_BACKGROUND`权限。  
- 跨应用场景下，目标Ability的exported属性若配置为false，调用方应用需申请`ohos.permission.START_INVISIBLE_ABILITY`权限。  
- 同设备与跨设备场景下，该接口的使用规则存在差异，详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 9

**需要权限：** ohos.permission.ABILITY_BACKGROUND_COMMUNICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 传入需要启动的Ability的信息，包含abilityName、moduleName、bundleName、deviceId、parameters(可选)，parameters缺省或为 空表示后台启动Ability。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Caller](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-caller-i.md)&gt; | Promise对象，返回要通讯的caller对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission.<br>**适用版本：** 9 |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released.<br>**适用版本：** 9 |

**示例**

后台启动：

```TypeScript
import { ServiceExtensionAbility, Caller, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let caller: Caller;
    // 后台启动Ability，不配置parameters
    let wantBackground: Want = {
      bundleName: 'com.example.myservice',
      moduleName: 'entry',
      abilityName: 'EntryAbility',
      deviceId: ''
    };

    try {
      this.context.startAbilityByCall(wantBackground)
        .then((obj: Caller) => {
          // 执行正常业务
          caller = obj;
          console.info('startAbilityByCall succeed');
        }).catch((error: BusinessError) => {
        // 处理业务逻辑错误
        console.error(`startAbilityByCall failed, error.code: ${error.code}, error.message: ${error.message}`);
      });
    } catch (paramError) {
      // 处理入参错误异常
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

前台启动：

```TypeScript
import { ServiceExtensionAbility, Caller, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let caller: Caller;
    // 前台启动Ability，将parameters中的'ohos.aafwk.param.callAbilityToForeground'配置为true
    let wantForeground: Want = {
      bundleName: 'com.example.myservice',
      moduleName: 'entry',
      abilityName: 'EntryAbility',
      deviceId: '',
      parameters: {
        'ohos.aafwk.param.callAbilityToForeground': true
      }
    };

    try {
      this.context.startAbilityByCall(wantForeground)
        .then((obj: Caller) => {
          // 执行正常业务
          caller = obj;
          console.info('startAbilityByCall succeed');
        }).catch((error: BusinessError) => {
        // 处理业务逻辑错误
        console.error(`startAbilityByCall failed, error.code: ${error.code}, error.message: ${error.message}`);
      });
    } catch (paramError) {
      // 处理入参错误异常
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## startAbilityByCallWithAccount

```TypeScript
startAbilityByCallWithAccount(want: Want, accountId: number): Promise<Caller>
```

根据accountId对指定的Ability进行call调用，并且可以使用返回的Caller通信接口与被调用方进行通信。仅支持在主线程调用。使用Promise异步回调。该接口不支持拉起启动模式为[specified模式](../../../application-models/uiability-launch-type.md#specified启动模式)的UIAbility。使用规则：  
- 跨用户场景下，Call调用目标Ability时，调用方应用需同时申请`ohos.permission.ABILITY_BACKGROUND_COMMUNICATION`与`  
ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS`权限。  
- 调用方应用位于后台时，使用该接口启动Ability需申请`ohos.permission.START_ABILITIES_FROM_BACKGROUND`权限。  
- 跨应用场景下，目标Ability的exported属性若配置为false，调用方应用需申请`ohos.permission.START_INVISIBLE_ABILITY`权限。  
- 同设备与跨设备场景下，该接口的使用规则存在差异，详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 10

**需要权限：** ohos.permission.ABILITY_BACKGROUND_COMMUNICATION and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 传入需要启动的Ability的信息，包含abilityName、moduleName、bundleName、deviceId(可选)、parameters(可选)，其中deviceId 缺省或为空表示启动本地Ability，parameters缺省或为空表示后台启动Ability。 |
| accountId | number | 是 | 系统账号的账号ID，-1表示当前活动用户。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Caller](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-caller-i.md)&gt; | Promise对象，返回要通讯的caller对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want, Caller } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let caller: Caller;
    // 系统账号的账号ID, -1表示当前激活用户
    let accountId = -1;
    // 指定启动的Ability
    let want: Want = {
      bundleName: 'com.acts.actscalleeabilityrely',
      moduleName: 'entry',
      abilityName: 'EntryAbility',
      deviceId: '',
      parameters: {
        // 'ohos.aafwk.param.callAbilityToForeground' 值设置为true时为前台启动, 设置false或不设置为后台启动
        'ohos.aafwk.param.callAbilityToForeground': true
      }
    };

    try {
      this.context.startAbilityByCallWithAccount(want, accountId)
        .then((obj: Caller) => {
          // 执行正常业务
          caller = obj;
          console.info('startAbilityByCallWithAccount succeed');
        }).catch((error: BusinessError) => {
        // 处理业务逻辑错误
        console.error(`startAbilityByCallWithAccount failed, error.code: ${error.code}, error.message: ${error.message}`);
      });
    } catch (paramError) {
      // 处理入参错误异常
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## startAbilityWithAccount

```TypeScript
startAbilityWithAccount(want: Want, accountId: number, callback: AsyncCallback<void>): void
```

根据accountId启动Ability。仅支持在主线程调用。使用callback异步回调。

> **说明：**
> 
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 9

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 启动Ability的Want信息。 |
| accountId | number | 是 | 系统账号的账号ID。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当根据accountId启动Ability成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000019](../../apis-ability-kit/errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found.<br>**适用版本：** 12+ |
| [16000073](../../apis-ability-kit/errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000071](../../apis-ability-kit/errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000072](../../apis-ability-kit/errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000076](../../apis-ability-kit/errorcode-ability.md#16000076-指定的app_instance_key不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000077](../../apis-ability-kit/errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../../apis-ability-kit/errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../../apis-ability-kit/errorcode-ability.md#16000079-不支持指定app_instance_key) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000080](../../apis-ability-kit/errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let accountId = 100;

    try {
      this.context.startAbilityWithAccount(want, accountId, (error: BusinessError) => {
        if (error.code) {
          // 处理业务逻辑错误
          console.error(`startAbilityWithAccount failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        // 执行正常业务
        console.info('startAbilityWithAccount succeed');
      });
    } catch (paramError) {
      // 处理入参错误异常
      console.error(`error.code: ${paramError.code}, error.message: ${paramError.message}`);
    }
  }
}
```

## startAbilityWithAccount

```TypeScript
startAbilityWithAccount(want: Want, accountId: number, options: StartOptions, callback: AsyncCallback<void>): void
```

根据accountId启动Ability。仅支持在主线程调用。使用callback异步回调。

> **说明：**
> 
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 9

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 启动Ability的Want信息。 |
| accountId | number | 是 | 系统账号的账号ID。 |
| options | [StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c.md) | 是 | 启动Ability所携带的参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当根据accountId启动Ability成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type.<br>**适用版本：** 9 |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden.<br>**适用版本：** 9 |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000019](../../apis-ability-kit/errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found.<br>**适用版本：** 12+ |
| [16000073](../../apis-ability-kit/errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000071](../../apis-ability-kit/errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000072](../../apis-ability-kit/errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000076](../../apis-ability-kit/errorcode-ability.md#16000076-指定的app_instance_key不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000077](../../apis-ability-kit/errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../../apis-ability-kit/errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../../apis-ability-kit/errorcode-ability.md#16000079-不支持指定app_instance_key) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000080](../../apis-ability-kit/errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    // accountId为系统账号ID，可通过getOsAccountLocalId接口获取，此处以100为例
    let accountId = 100;
    let options: StartOptions = {
      windowMode: 0
    };

    try {
      this.context.startAbilityWithAccount(want, accountId, options, (error: BusinessError) => {
        if (error.code) {
          // 处理业务逻辑错误
          console.error(`startAbilityWithAccount failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        // 执行正常业务
        console.info('startAbilityWithAccount succeed');
      });
    } catch (paramError) {
      // 处理入参错误异常
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## startAbilityWithAccount

```TypeScript
startAbilityWithAccount(want: Want, accountId: number, options?: StartOptions): Promise<void>
```

根据accountId启动Ability。仅支持在主线程调用。使用Promise异步回调。

> **说明：**
> 
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 9

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 启动Ability的Want信息。 |
| accountId | number | 是 | 系统账号的账号ID。 |
| options | [StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c.md) | 否 | 启动Ability所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000019](../../apis-ability-kit/errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found.<br>**适用版本：** 12+ |
| [16000073](../../apis-ability-kit/errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000071](../../apis-ability-kit/errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000072](../../apis-ability-kit/errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000076](../../apis-ability-kit/errorcode-ability.md#16000076-指定的app_instance_key不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000077](../../apis-ability-kit/errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../../apis-ability-kit/errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../../apis-ability-kit/errorcode-ability.md#16000079-不支持指定app_instance_key) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000080](../../apis-ability-kit/errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    // accountId为系统账号ID，可通过getOsAccountLocalId接口获取，此处以100为例
    let accountId = 100;
    let options: StartOptions = {
      windowMode: 0
    };

    try {
      this.context.startAbilityWithAccount(want, accountId, options)
        .then((data: void) => {
          // 执行正常业务
          console.info('startAbilityWithAccount succeed');
        })
        .catch((error: BusinessError) => {
          // 处理业务逻辑错误
          console.error(`startAbilityWithAccount failed, error.code: ${error.code}, error.message: ${error.message}`);
        });
    } catch (paramError) {
      // 处理入参错误异常
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## startRecentAbility

```TypeScript
startRecentAbility(want: Want, callback: AsyncCallback<void>): void
```

启动一个指定的Ability，如果该Ability有多个实例，将拉起最近启动的那个实例。仅支持在主线程调用。使用callback异步回调。

> **说明：**
> 
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 需要启动Ability的Want信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当启动一个指定的Ability成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api.<br>**适用版本：** 14+ |
| [16000071](../../apis-ability-kit/errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000072](../../apis-ability-kit/errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000073](../../apis-ability-kit/errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 14+ |
| [16000076](../../apis-ability-kit/errorcode-ability.md#16000076-指定的app_instance_key不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000077](../../apis-ability-kit/errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../../apis-ability-kit/errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../../apis-ability-kit/errorcode-ability.md#16000079-不支持指定app_instance_key) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000080](../../apis-ability-kit/errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };

    try {
      this.context.startRecentAbility(want, (err: BusinessError) => {
        if (err.code) {
          // 处理业务逻辑错误
          console.error(`startRecentAbility failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        // 执行正常业务
        console.info('startRecentAbility succeed');
      });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startRecentAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## startRecentAbility

```TypeScript
startRecentAbility(want: Want, options: StartOptions, callback: AsyncCallback<void>): void
```

启动一个指定的Ability，如果该Ability有多个实例，将拉起最近启动的那个实例。仅支持在主线程调用。使用callback异步回调。当开发者需要携带启动参数时可以选择此API。

> **说明：**
> 
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 需要启动Ability的Want信息。 |
| options | [StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c.md) | 是 | 启动Ability所携带的参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当启动一个指定的Ability成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type.<br>**适用版本：** 9 |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden.<br>**适用版本：** 9 |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api.<br>**适用版本：** 14+ |
| [16000071](../../apis-ability-kit/errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000072](../../apis-ability-kit/errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000073](../../apis-ability-kit/errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 14+ |
| [16000076](../../apis-ability-kit/errorcode-ability.md#16000076-指定的app_instance_key不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000077](../../apis-ability-kit/errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../../apis-ability-kit/errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../../apis-ability-kit/errorcode-ability.md#16000079-不支持指定app_instance_key) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000080](../../apis-ability-kit/errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let options: StartOptions = {
      windowMode: 0
    };

    try {
      this.context.startRecentAbility(want, options, (err: BusinessError) => {
        if (err.code) {
          // 处理业务逻辑错误
          console.error(`startRecentAbility failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        // 执行正常业务
        console.info('startRecentAbility succeed');
      });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startRecentAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## startRecentAbility

```TypeScript
startRecentAbility(want: Want, options?: StartOptions): Promise<void>
```

启动一个指定的Ability，如果该Ability有多个实例，将拉起最近启动的那个实例。使用Promise异步回调。仅支持在主线程调用。

> **说明：**
> 
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 需要启动Ability的Want信息。 |
| options | [StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c.md) | 否 | 启动Ability所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | The promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api.<br>**适用版本：** 14+ |
| [16000071](../../apis-ability-kit/errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000072](../../apis-ability-kit/errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000073](../../apis-ability-kit/errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 14+ |
| [16000076](../../apis-ability-kit/errorcode-ability.md#16000076-指定的app_instance_key不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000077](../../apis-ability-kit/errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../../apis-ability-kit/errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../../apis-ability-kit/errorcode-ability.md#16000079-不支持指定app_instance_key) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000080](../../apis-ability-kit/errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let options: StartOptions = {
      windowMode: 0,
    };

    try {
      this.context.startRecentAbility(want, options)
        .then(() => {
          // 执行正常业务
          console.info('startRecentAbility succeed');
        })
        .catch((err: BusinessError) => {
          // 处理业务逻辑错误
          console.error(`startRecentAbility failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startRecentAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## startServiceExtensionAbility

```TypeScript
startServiceExtensionAbility(want: Want, callback: AsyncCallback<void>): void
```

启动一个新的ServiceExtensionAbility。使用callback异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 启动Ability的Want信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当启动一个新的ServiceExtensionAbility成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 10+ |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000019](../../apis-ability-kit/errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };

    try {
      this.context.startServiceExtensionAbility(want, (error: BusinessError) => {
        if (error.code) {
          // 处理业务逻辑错误
          console.error(`startServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        // 执行正常业务
        console.info('startServiceExtensionAbility succeed');
      });
    } catch (paramError) {
      // 处理入参错误异常
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## startServiceExtensionAbility

```TypeScript
startServiceExtensionAbility(want: Want): Promise<void>
```

启动一个新的ServiceExtensionAbility。使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 启动Ability的Want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 10+ |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000019](../../apis-ability-kit/errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };

    try {
      this.context.startServiceExtensionAbility(want)
        .then((data) => {
          // 执行正常业务
          console.info('startServiceExtensionAbility succeed');
        })
        .catch((error: BusinessError) => {
          // 处理业务逻辑错误
          console.error(`startServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
        });
    } catch (paramError) {
      // 处理入参错误异常
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## startServiceExtensionAbilityWithAccount

```TypeScript
startServiceExtensionAbilityWithAccount(want: Want, accountId: number, callback: AsyncCallback<void>): void
```

启动一个新的ServiceExtensionAbility。使用callback异步回调。

> **说明：**
> 
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。
> 
> 当accountId为当前用户时，无需进行权限校验。

**起始版本：** 9

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 启动Ability的Want信息。 |
| accountId | number | 是 | 系统账号的账号ID。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当启动一个新的ServiceExtensionAbility成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 10+ |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000019](../../apis-ability-kit/errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    // accountId为系统账号ID，可通过getOsAccountLocalId接口获取，此处以100为例
    let accountId = 100;

    try {
      this.context.startServiceExtensionAbilityWithAccount(want, accountId, (error: BusinessError) => {
        if (error.code) {
          // 处理业务逻辑错误
          console.error(`startServiceExtensionAbilityWithAccount failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        // 执行正常业务
        console.info('startServiceExtensionAbilityWithAccount succeed');
      });
    } catch (paramError) {
      // 处理入参错误异常
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## startServiceExtensionAbilityWithAccount

```TypeScript
startServiceExtensionAbilityWithAccount(want: Want, accountId: number): Promise<void>
```

启动一个新的ServiceExtensionAbility。使用Promise异步回调。

> **说明：**
> 
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。
> 
> 当accountId为当前用户时，无需进行权限校验。

**起始版本：** 9

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 启动Ability的Want信息。 |
| accountId | number | 是 | 系统账号的账号ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 10+ |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000019](../../apis-ability-kit/errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    // accountId为系统账号ID，可通过getOsAccountLocalId接口获取，此处以100为例
    let accountId = 100;

    try {
      this.context.startServiceExtensionAbilityWithAccount(want, accountId)
        .then((data: void) => {
          // 执行正常业务
          console.info('startServiceExtensionAbilityWithAccount succeed');
        })
        .catch((error: BusinessError) => {
          // 处理业务逻辑错误
          console.error(`startServiceExtensionAbilityWithAccount failed, error.code: ${error.code}, error.message: ${error.message}`);
        });
    } catch (paramError) {
      // 处理入参错误异常
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## startUIAbilities

```TypeScript
startUIAbilities(wantList: Array<Want>): Promise<void>
```

同时启动多个UIAbility。使用Promise异步回调。开发者可以传入多个UIAbility对应的Want信息，这些UIAbility可以指向一个或多个应用。当所有的UIAbility都能启动成功时，系统会通过多个窗口同时展示这些UIAbility。根据窗口的处理，不同设备上可能会有不 同的展示效果（包括窗口形态、数量和排版布局）。 该接口在Phone、Tablet中可正常调用，在其他设备类型中返回801错误码。

> **说明：**
> 
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wantList | Array&lt;[Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)&gt; | 是 | 需要被同时拉起的多个UIAbility的启动参数列表，最多支持传入4个Want。启动参数Want不支持隐式启动、跨用户启动、分布式、免安装和按需加载，不指明分身的 情况下默认启动主应用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000073](../../apis-ability-kit/errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid. |
| [16000076](../../apis-ability-kit/errorcode-ability.md#16000076-指定的app_instance_key不存在) | The app instance key is invalid. |
| [16000080](../../apis-ability-kit/errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported. |
| [16000120](../../apis-ability-kit/errorcode-ability.md#16000120-wantlist内的元素个数超出4个或小于1个) | A maximum of four UIAbility instances can be started simultaneously. The current parameter exceeds the maximum number or is less than 1. |
| [16000121](../../apis-ability-kit/errorcode-ability.md#16000121-待启动的目标组件类型不是uiability) | The target component type is not a UIAbility. |
| [16000122](../../apis-ability-kit/errorcode-ability.md#16000122-待启动的目标组件被系统管控模块拦截) | The target component is blocked by the system module and does not support startup. |
| [16000123](../../apis-ability-kit/errorcode-ability.md#16000123-不支持隐式启动) | Implicit startup is not supported. |
| [16000124](../../apis-ability-kit/errorcode-ability.md#16000124-不支持启动分布式uiability) | Starting a remote UIAbility is not supported. |
| [16000125](../../apis-ability-kit/errorcode-ability.md#16000125-不支持启动插件uiability) | Starting a plugin UIAbility is not supported. |
| [16000126](../../apis-ability-kit/errorcode-ability.md#16000126-不支持启动dlp文件) | Starting DLP files is not supported. |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryServiceExtAbility extends ServiceExtensionAbility {
  onRequest() {
    let want1: Want = {
      bundleName: 'com.example.myapplication1',
      abilityName: 'EntryAbility'
    };
    let want2: Want = {
      bundleName: 'com.example.myapplication2',
      abilityName: 'EntryAbility'
    };
    let wantList: Array<Want> = [want1, want2];
    try {
      this.context.startUIAbilities(wantList).then(() => {
        console.info(`TestTag:: start succeeded.`);
      }).catch((error: BusinessError) => {
        console.info(`TestTag:: startUIAbilities failed: ${JSON.stringify(error)}`);
      });
    } catch (paramError) {
      // 处理入参错误异常
      console.error(`error.code: ${paramError.code}, error.message: ${paramError.message}`);
    }
  }
}
```

## startUIServiceExtensionAbility

```TypeScript
startUIServiceExtensionAbility(want: Want): Promise<void>
```

启动一个新的[UIServiceExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiserviceextensionability-uiserviceextensionability-c-sys.md) 。使用Promise异步回调。

> **说明：**
> 
> 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | Indicates the want info to start. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000019](../../apis-ability-kit/errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';

export default class MyServiceExtensionAbility extends ServiceExtensionAbility {
  onRequest(want: Want, startId: number) {
    const startWant: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'UIServiceExtensionAbility'
    }
    // 启动一个UIServiceExtensionAbility
    this.context.startUIServiceExtensionAbility(startWant).then(() => {
      console.info('succeeded');
    }).catch((error: BusinessError) => {
      console.error(`error code: ${error.code}, error message : ${error.message}`);
    })
  }
}
```

## stopServiceExtensionAbility

```TypeScript
stopServiceExtensionAbility(want: Want, callback: AsyncCallback<void>): void
```

停止指定的ServiceExtensionAbility后台服务。使用callback异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 停止Ability的Want信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当停止同一应用程序内的服务成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 10+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };

    try {
      this.context.stopServiceExtensionAbility(want, (error: BusinessError) => {
        if (error.code) {
          // 处理业务逻辑错误
          console.error(`stopServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        // 执行正常业务
        console.info('stopServiceExtensionAbility succeed');
      });
    } catch (paramError) {
      // 处理入参错误异常
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## stopServiceExtensionAbility

```TypeScript
stopServiceExtensionAbility(want: Want): Promise<void>
```

停止指定的ServiceExtensionAbility后台服务。使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 停止Ability的Want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 10+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };

    try {
      this.context.stopServiceExtensionAbility(want)
        .then(() => {
          // 执行正常业务
          console.info('stopServiceExtensionAbility succeed');
        })
        .catch((error: BusinessError) => {
          // 处理业务逻辑错误
          console.error(`stopServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
        });
    } catch (paramError) {
      // 处理入参错误异常
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## stopServiceExtensionAbilityWithAccount

```TypeScript
stopServiceExtensionAbilityWithAccount(want: Want, accountId: number, callback: AsyncCallback<void>): void
```

停止指定账号下指定的ServiceExtensionAbility后台服务。使用callback异步回调。

> **说明：**
> 
> 当accountId为当前用户时，无需进行权限校验。

**起始版本：** 9

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 停止Ability的Want信息。 |
| accountId | number | 是 | 需要停止的系统账号的账号ID。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当使用账户停止同一应用程序内的服务成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 10+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    // accountId为系统账号ID，可通过getOsAccountLocalId接口获取，此处以100为例
    let accountId = 100;

    try {
      this.context.stopServiceExtensionAbilityWithAccount(want, accountId, (error: BusinessError) => {
        if (error.code) {
          // 处理业务逻辑错误
          console.error(`stopServiceExtensionAbilityWithAccount failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        // 执行正常业务
        console.info('stopServiceExtensionAbilityWithAccount succeed');
      });
    } catch (paramError) {
      // 处理入参错误异常
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## stopServiceExtensionAbilityWithAccount

```TypeScript
stopServiceExtensionAbilityWithAccount(want: Want, accountId: number): Promise<void>
```

停止指定账号下指定的ServiceExtensionAbility后台服务。使用Promise异步回调。

> **说明：**
> 
> 当accountId为当前用户时，无需进行权限校验。

**起始版本：** 9

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 停止Ability的Want信息。 |
| accountId | number | 是 | 需要停止的系统账号的账号ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 10+ |

**示例**

```TypeScript
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    // accountId为系统账号ID，可通过getOsAccountLocalId接口获取，此处以100为例
    let accountId = 100;

    try {
      this.context.stopServiceExtensionAbilityWithAccount(want, accountId)
        .then(() => {
          // 执行正常业务
          console.info('stopServiceExtensionAbilityWithAccount succeed');
        })
        .catch((error: BusinessError) => {
          // 处理业务逻辑错误
          console.error(`stopServiceExtensionAbilityWithAccount failed, error.code: ${error.code}, error.message: ${error.message}`);
        });
    } catch (paramError) {
      // 处理入参错误异常
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## terminateSelf

```TypeScript
terminateSelf(callback: AsyncCallback<void>): void
```

停止Ability自身。仅支持在主线程调用。使用callback异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当停止Ability自身成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist.<br>**适用版本：** 9 |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 9 |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission.<br>**适用版本：** 9 |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例**

```TypeScript
import { ServiceExtensionAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    this.context.terminateSelf((error: BusinessError) => {
      if (error.code) {
        // 处理业务逻辑错误
        console.error(`terminateSelf failed, error.code: ${error.code}, error.message: ${error.message}`);
        return;
      }
      // 执行正常业务
      console.info('terminateSelf succeed');
    });
  }
}
```

## terminateSelf

```TypeScript
terminateSelf(): Promise<void>
```

停止Ability自身。仅支持在主线程调用。使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist.<br>**适用版本：** 9 |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 9 |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission.<br>**适用版本：** 9 |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例**

```TypeScript
import { ServiceExtensionAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class EntryAbility extends ServiceExtensionAbility {
  onCreate() {
    this.context.terminateSelf().then(() => {
      // 执行正常业务
      console.info('terminateSelf succeed');
    }).catch((error: BusinessError) => {
      // 处理业务逻辑错误
      console.error(`terminateSelf failed, error.code: ${error.code}, error.message: ${error.message}`);
    });
  }
}
```
