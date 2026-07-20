# AppServiceExtensionContext (应用后台服务扩展组件上下文)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yewei0794-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

AppServiceExtensionContext模块是[AppServiceExtensionAbility](js-apis-app-ability-appServiceExtensionAbility.md)的上下文环境，继承自[ExtensionContext](js-apis-inner-application-extensionContext.md)。提供了连接、断开ServiceExtensionAbility（系统应用后台服务扩展组件）的能力，以及AppServiceExtensionAbility终止自身的能力。可用于三方应用与系统后台服务通信。


> **说明：**
> 
>  - 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>  - 本模块接口仅可在Stage模型下使用。
>  - 本模块接口需要在主线程中使用，不要在Worker、TaskPool等子线程中使用。

## 导入模块

```ts
import { common } from '@kit.AbilityKit';
```

## 使用说明

使用AppServiceExtensionContext功能前，通过AppServiceExtensionAbility子类实例获取AppServiceExtensionContext。

**示例：**

```ts
import { AppServiceExtensionAbility, Want } from '@kit.AbilityKit';

export default class AppServiceExtension extends AppServiceExtensionAbility {
  onCreate(want: Want) {
    let context = this.context; // 获取AppServiceExtensionContext
  }
}
```

## AppServiceExtensionContext

### startAbility

startAbility(want: Want, options?: StartOptions): Promise&lt;void&gt;

启动UIAbility。调用后，系统根据Want信息启动目标UIAbility。使用Promise异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md)  | 是 | Want类型参数，传入需要启动的Ability的信息，如Ability名称、Bundle名称等。 |
| options | [StartOptions](js-apis-app-ability-startOptions.md) | 否 | 启动Ability所携带的参数。需要指定窗口模式、显示设备、进程模式等启动参数时传入。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000008 | The crowdtesting application expires. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden. |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled. |
| 16000013 | The application is controlled by EDM. |
| 16000019 | No matching ability is found. |
| 16000050 | Internal error. |
| 16000055 | Installation-free timed out. |
| 16000071 | App clone is not supported. |
| 16000072 | App clone or multi-instance is not supported. |
| 16000073 | The app clone index is invalid. |
| 16000076 | The app instance key is invalid. |
| 16000077 | The number of app instances reaches the limit. |
| 16000078 | The multi-instance is not supported. |
| 16000079 | The APP_INSTANCE_KEY cannot be specified. |
| 16000080 | Creating a new instance is not supported. |

**示例：**

```ts
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
        .catch((err: BusinessError) => {
          // 处理业务逻辑错误
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

### connectServiceExtensionAbility

connectServiceExtensionAbility(want: Want, callback: ConnectOptions): number

将当前AppServiceExtensionAbility连接到一个ServiceExtensionAbility（ServiceExtensionAbility仅支持由系统应用开发，三方应用可连接），通过ConnectOptions的onConnect回调返回的remote对象与ServiceExtensionAbility通信，以使用ServiceExtensionAbility对外提供的能力。可使用返回的connectionID调用disconnectServiceExtensionAbility()断开连接。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md)  | 是 | Want类型参数，传入需要连接的Ability的信息，如Ability名称、Bundle名称等。 |
| callback | [ConnectOptions](js-apis-inner-ability-connectOptions.md) | 是 | ConnectOptions类型的回调函数，用于监听服务连接状态的变化，包括连接成功、连接失败、断开连接。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| number | 返回连接标识符，用于后续通过[disconnectServiceExtensionAbility](#disconnectserviceextensionability)断开连接。 |

**错误码：**

以下错误码详细介绍请参考[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000011 | The context does not exist.        |
| 16000050 | Internal error. |

**示例：**

```ts
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

### disconnectServiceExtensionAbility

disconnectServiceExtensionAbility(connection: number): Promise&lt;void&gt;

将AppServiceExtensionAbility与已连接的ServiceExtensionAbility断开连接，connection为connectServiceExtensionAbility()返回的连接ID。使用Promise异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| connection | number | 是 | 在[connectServiceExtensionAbility](#connectserviceextensionability)中返回的连接id。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码详细介绍请参考[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 16000011 | The context does not exist.        |
| 16000050 | Internal error. |

**示例：**

参见[connectServiceExtensionAbility](#connectserviceextensionability)。

### terminateSelf

terminateSelf(): Promise&lt;void&gt;

销毁AppServiceExtensionAbility自身。使用Promise异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码详细介绍请参考[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000011 | The context does not exist.        |
| 16000050 | Internal error. |

**示例：**

```ts
import { AppServiceExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[AppServiceExtensionAbility]';

export default class AppServiceExtension extends AppServiceExtensionAbility {
  onCreate(want: Want) {
    this.context.terminateSelf().then(() => {
      // 执行正常业务
      hilog.info(0x0000, TAG, '----------- terminateSelf succeed -----------');
    }).catch((error: BusinessError) => {
      // 处理业务逻辑错误
      hilog.error(0x0000, TAG, `terminateSelf failed, error.code: ${error.code}, error.message: ${error.message}`);
    });
  }
}
```
