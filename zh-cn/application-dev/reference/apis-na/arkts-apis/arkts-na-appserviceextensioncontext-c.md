# AppServiceExtensionContext

AppServiceExtensionContext模块是 [AppServiceExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-appserviceextensionability-appserviceextensionability-c.md#AppServiceExtensionAbility)的 上下文环境，继承自[ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md#ExtensionContext)。 AppServiceExtensionContext提供了连接、断开ServiceExtensionAbility（系统应用后台服务扩展组件）的能力，以及AppServiceExtensionAbility终止自身的能力。这里的 ServiceExtensionAbility只能由系统应用开发，支持三方应用连接。 > **说明：** > > - 本模块接口需要在主线程中使用，不要在Worker、TaskPool等子线程中使用。

**继承/实现关系：** AppServiceExtensionContext extends ExtensionContext

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare class AppServiceExtensionContext--><!--Device-unnamed-declare class AppServiceExtensionContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## connectServiceExtensionAbility

```TypeScript
connectServiceExtensionAbility(want: Want, callback: ConnectOptions): long
```

将当前AppServiceExtensionAbility连接到一个ServiceExtensionAbility，通过返回的proxy与ServiceExtensionAbility进行通信，以使用 ServiceExtensionAbility对外提供的能力。仅支持在主线程调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AppServiceExtensionContext-connectServiceExtensionAbility(want: Want, callback: ConnectOptions): long--><!--Device-AppServiceExtensionContext-connectServiceExtensionAbility(want: Want, callback: ConnectOptions): long-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | Want类型参数，传入需要连接的Ability的信息，如Ability名称，Bundle名称等。 |
| callback | [ConnectOptions](../../apis-ability-kit/arkts-apis/arkts-ability-connectoptions-connectoptions-i.md) | 是 | ConnectOptions类型的回调函数，返回服务连接成功、连接失败、断开的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 返回连接id，客户端可以通过 [disconnectServiceExtensionAbility]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { AppServiceExtensionAbility, Want, common } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let commRemote: rpc.IRemoteObject | null = null; // 断开连接时需要释放
const TAG: string = '[AppServiceExtensionAbility]';

export default class AppServiceExtension extends AppServiceExtensionAbility {
  connection: number = 0;

  onCreate(localWant: Want) {
    let want: Want = {
      bundleName: 'com.example.myapp',
      abilityName: 'MyAbility'
    };
    let callback: common.ConnectOptions = {
      onConnect(elementName, remote) {
        commRemote = remote;
        hilog.info(0x0000, TAG, '----------- onConnect -----------');
      },
      onDisconnect(elementName) {
        hilog.info(0x0000, TAG, '----------- onDisconnect -----------');
      },
      onFailed(code) {
        hilog.error(0x0000, TAG, '----------- onFailed -----------');
      }
    };


    try {
      this.connection = this.context.connectServiceExtensionAbility(want, callback);
    } catch (paramError) {
      commRemote = null;
      // 处理入参错误异常
      hilog.error(0x0000, TAG, `error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }

  onDestroy(): void {
    this.context.disconnectServiceExtensionAbility(this.connection).then(() => {
      commRemote = null;
      // 执行正常业务
      hilog.info(0x0000, TAG, '----------- disconnectServiceExtensionAbility success -----------');
    })
      .catch((error: BusinessError) => {
        commRemote = null;
        // 处理业务逻辑错误
        hilog.error(0x0000, TAG, `disconnectServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
      });
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { AppServiceExtensionAbility, Want, common, bundleManager } from '@kit.AbilityKit';
import rpc from '@ohos.rpc';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let commRemote: rpc.IRemoteObject; // 断开连接时需要释放
const TAG: string = '[AppServiceExtensionAbility]';

class AppServiceExtension extends AppServiceExtensionAbility {
  onCreate() {
    let want: Want = {
      bundleName: 'com.example.myapp',
      abilityName: 'MyAbility'
    };
    let callback: common.ConnectOptions = {
      onConnect: (elementName: bundleManager.ElementName, remote: rpc.IRemoteObject): void => {
        console.info(`onConnect elementName: ${JSON.stringify(elementName)}`);
      },
      onDisconnect: (elementName: bundleManager.ElementName): void => {
        console.info(`onDisconnect elementName: ${JSON.stringify(elementName)}`);
      },
      onFailed: (code: int): void => {
        console.error(`onFailed code: ${code}`);
      }
    };
    let connection: long;

    try {
      connection = this.context.connectServiceExtensionAbility(want, callback);
    } catch (paramError) {
      // 处理入参错误异常
      hilog.error(0x0000, TAG,
        `error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## disconnectServiceExtensionAbility

```TypeScript
disconnectServiceExtensionAbility(connection: long): Promise<void>
```

将AppServiceExtensionAbility与已连接的ServiceExtensionAbility断开连接。仅支持在主线程调用。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AppServiceExtensionContext-disconnectServiceExtensionAbility(connection: long): Promise<void>--><!--Device-AppServiceExtensionContext-disconnectServiceExtensionAbility(connection: long): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connection | long | 是 | 在 [connectServiceExtensionAbility](#connectServiceExtensionAbility)中返回的连接id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## 示例

ArkTS-Sta示例：

```TypeScript
'use static'
import { AppServiceExtensionAbility } from '@kit.AbilityKit';
import rpc from '@ohos.rpc';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let commRemote: rpc.IRemoteObject | null; // 断开连接时需要释放
const TAG: string = '[AppServiceExtensionAbility]';

class AppServiceExtension extends AppServiceExtensionAbility {
  onCreate() {
    // connection为connectServiceExtensionAbility中的返回值
    let connection = 1;
    try {
      this.context.disconnectServiceExtensionAbility(connection)
        .then(() => {
          commRemote = null;
          // 执行正常业务
          hilog.info(0x0000, TAG, '----------- disconnectServiceExtensionAbility success -----------');
        })
        .catch((err: Error) => {
          commRemote = null;
          // 处理业务逻辑错误
          let error = err as BusinessError;
          hilog.error(0x0000, TAG,
            `disconnectServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
        });
    } catch (paramError) {
      commRemote = null;
      // 处理入参错误异常
      hilog.error(0x0000, TAG,
        `error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## startAbility

```TypeScript
startAbility(want: Want, options?: StartOptions): Promise<void>
```

启动UIAbility。仅支持在主线程调用。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AppServiceExtensionContext-startAbility(want: Want, options?: StartOptions): Promise<void>--><!--Device-AppServiceExtensionContext-startAbility(want: Want, options?: StartOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | Want类型参数，传入需要启动的Ability的信息，如Ability名称、Bundle名称等。 |
| options | [StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c.md) | 否 | 启动Ability所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16000080](../../apis-ability-kit/errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000019](../../apis-ability-kit/errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000071](../../apis-ability-kit/errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000076](../../apis-ability-kit/errorcode-ability.md#16000076-指定的appinstancekey不存在) | The app instance key is invalid. |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000077](../../apis-ability-kit/errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit. |
| [16000078](../../apis-ability-kit/errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported. |
| [16000079](../../apis-ability-kit/errorcode-ability.md#16000079-不支持指定appinstancekey) | The APP_INSTANCE_KEY cannot be specified. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000072](../../apis-ability-kit/errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000073](../../apis-ability-kit/errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## 示例

```TypeScript
import { AppServiceExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyAppServiceExtensionAbility extends AppServiceExtensionAbility {
  onCreate(want: Want) {
    let wantInfo: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let options: StartOptions = {
      displayId: 0
    };

    try {
      this.context.startAbility(wantInfo, options)
        .then(() => {
          // 执行正常业务
          console.info('startAbility succeed');
        })
        .catch((error: Error) => {
          // 处理业务逻辑错误
          let err = error as BusinessError;
          console.error(`startAbility failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## terminateSelf

```TypeScript
terminateSelf(): Promise<void>
```

销毁AppServiceExtensionAbility自身。仅支持在主线程调用。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AppServiceExtensionContext-terminateSelf(): Promise<void>--><!--Device-AppServiceExtensionContext-terminateSelf(): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## 示例

```TypeScript
import { AppServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[AppServiceExtensionAbility]';

export default class AppServiceExtension extends AppServiceExtensionAbility {
  onCreate(want: Want) {
    this.context.terminateSelf().then(() => {
      // 执行正常业务
      hilog.info(0x0000, TAG, '----------- terminateSelf succeed -----------');
    }).catch((err: Error) => {
      // 处理业务逻辑错误
      let error = err as BusinessError;
      hilog.error(0x0000, TAG, `terminateSelf failed, error.code: ${error.code}, error.message: ${error.message}`);
    });
  }
}
```

