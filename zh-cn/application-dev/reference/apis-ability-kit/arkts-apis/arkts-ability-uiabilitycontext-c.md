# UIAbilityContext

UIAbilityContext是需要保存状态的[UIAbility](arkts-ability-app-ability-uiability-uiability-c.md)所对应的context，继承自Context，提供 UIAbility的相关配置信息以及操作UIAbility和ServiceExtensionAbility的方法，如启动UIAbility，停止当前UIAbilityContext所属的UIAbility，启动、停止、连接、断开连接 ServiceExtensionAbility等。

**继承/实现关系：** UIAbilityContext extends Context

**起始版本：** 23

<!--Device-unnamed-declare class UIAbilityContext--><!--Device-unnamed-declare class UIAbilityContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## backToCallerAbilityWithResult

```TypeScript
backToCallerAbilityWithResult(abilityResult: AbilityResult, requestCode: string): Promise<void>
```

当通过 [startAbilityForResult](#startabilityforresult) 或[openLink](#openlink)拉起目标方UIAbility，且需要目标方返回结果时，目标方可以通过该接口将结果返回并拉起调用方。与 [terminateSelfWithResult](#terminateselfwithresult) 不同的是，本接口在返回时不会销毁当前UIAbility。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-backToCallerAbilityWithResult(abilityResult: AbilityResult, requestCode: string): Promise<void>--><!--Device-UIAbilityContext-backToCallerAbilityWithResult(abilityResult: AbilityResult, requestCode: string): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| abilityResult | [AbilityResult](arkts-ability-abilityresult-abilityresult-i.md) | 是 | 包含目标方返回给拉起方的结果。 |
| requestCode | string | 是 | 通过 [startAbilityForResult](#startabilityforresult) 或[openLink](#openlink)拉起目标方Ability且需要目标方返回结果时，系统生成的用于标识本次调用的requestCode。该值可以通过want中的 [CALLER_REQUEST_CODE](arkts-app-ability-wantconstant.md)字段获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，包含接口执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000074](../errorcode-ability.md#16000074-返回结果时requestcode对应的调用方不存在) | The caller does not exist. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000075](../errorcode-ability.md#16000075-不支持返回结果时拉起调用方) | BackToCaller is not supported. |

**示例**

调用方通过startAbilityForResult接口拉起目标方, 目标方再调用backToCallerAbilityWithResult接口返回到调用方。

```TypeScript
// 调用方
// index.ets
import { common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(30)
          .fontWeight(FontWeight.Bold)

        Button("Call StartAbilityForResult")
          .onClick(() => {
            let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
            let want: Want = {
              bundleName: 'com.example.demo2',
              abilityName: 'EntryAbility'
            };

            try {
              // 通过startAbilityForResult拉起目标应用
              context.startAbilityForResult(want, (err: BusinessError, result: common.AbilityResult) => {
                if (err.code) {
                  // 处理业务逻辑错误
                  hilog.error(0x0000, 'testTag', `startAbilityForResult failed, code is ${err.code}, message is ${err.message}`);
                  this.message = `startAbilityForResult failed: code is ${err.code}, message is ${err.message}`
                  return;
                }
                // 执行正常业务
                hilog.info(0x0000, 'testTag', `startAbilityForResult succeed`);
                hilog.info(0x0000, 'testTag', `AbilityResult is ${JSON.stringify(result)}`);
                this.message = `AbilityResult.resultCode: ${JSON.stringify(result.resultCode)}`
              });
            } catch (err) {
              // 处理入参错误异常
              let code = (err as BusinessError).code;
              let message = (err as BusinessError).message;
              hilog.error(0x0000, 'testTag', `startAbilityForResult failed, code is ${code}, message is ${message}`);
              this.message = `startAbilityForResult failed, code is ${code}, message is ${message}`;
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

```TypeScript
// 目标方
// EntryAbility.ets
import { AbilityConstant, common, UIAbility, Want, wantConstant } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    // 从want中获取调用方的CALLER_REQUEST_CODE，并保存
    let callerRequestCode: string = want?.parameters?.[wantConstant.Params.CALLER_REQUEST_CODE] as string;
    AppStorage.setOrCreate<string>("callerRequestCode", callerRequestCode)
  }

  onNewWant(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let callerRequestCode: string = want?.parameters?.[wantConstant.Params.CALLER_REQUEST_CODE] as string;
    AppStorage.setOrCreate<string>("callerRequestCode", callerRequestCode)
  }

  onForeground(): void {
    // 获取保存的CALLER_REQUEST_CODE
    let callerRequestCode: string = AppStorage.get<string>("callerRequestCode") as string;
    hilog.info(0x0000, 'testTag', `callerRequestCode is ${callerRequestCode}`);
    let want: Want = {};
    let resultCode = 100;
    let abilityResult: common.AbilityResult = {
      want,
      resultCode
    };
    try {
      // 将结果信息返回给调用方
      this.context.backToCallerAbilityWithResult(abilityResult, callerRequestCode)
        .then(() => {
          // 执行正常业务
          hilog.info(0x0000, 'testTag', 'backToCallerAbilityWithResult succeed');
        })
        .catch((err: BusinessError) => {
          // 处理业务逻辑错误
          hilog.error(0x0000, 'testTag', `backToCallerAbilityWithResult failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // 捕获同步的参数错误
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      hilog.error(0x0000, 'testTag', `backToCallerAbilityWithResult failed, code is ${code}, message is ${message}`);
    }
  }
}
```

调用方通过startAbilityForResult接口拉起目标方，目标方再调用backToCallerAbilityWithResult接口返回到调用方。

```TypeScript
'use static'
// 调用方
// index.ets
import { common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Entry, Text, Column, Row, Component, Button, State } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(30)
          .fontWeight(700)

        Button("Call StartAbilityForResult")
          .onClick(() => {
            let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
            let want: Want = {
              bundleName: 'com.example.demo2',
              abilityName: 'EntryAbility'
            };

            try {
              // 通过startAbilityForResult拉起目标应用
              context.startAbilityForResult(want,
                (err: BusinessError | null, result: common.AbilityResult | undefined) => {
                  if (err?.code) {
                    // 处理业务逻辑错误
                    hilog.error(0x0000, 'testTag',
                      `startAbilityForResult failed, code is ${err?.code}, message is ${err?.message}`);
                    this.message = `startAbilityForResult failed: code is ${err?.code}, message is ${err?.message}`
                    return;
                  }
                  // 执行正常业务
                  hilog.info(0x0000, 'testTag', `startAbilityForResult succeed`);
                  hilog.info(0x0000, 'testTag', `AbilityResult is ${result}`);
                  this.message = `AbilityResult.resultCode: ${result?.resultCode}`
                });
            } catch (err) {
              // 处理入参错误异常
              let code = (err as BusinessError).code;
              let message = (err as BusinessError).message;
              hilog.error(0x0000, 'testTag', `startAbilityForResult failed, code is ${code}, message is ${message}`);
              this.message = `startAbilityForResult failed, code is ${code}, message is ${message}`;
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

```TypeScript
// 目标方
// EntryAbility.ets
import { AbilityConstant, common, UIAbility, Want, wantConstant } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { AppStorage } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    // 从want中获取调用方的CALLER_REQUEST_CODE，并保存
    let callerRequestCode: string = want?.parameters?.[wantConstant.Params.CALLER_REQUEST_CODE] as string;
    AppStorage.setOrCreate<string>("callerRequestCode", callerRequestCode)
  }

  onNewWant(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let callerRequestCode: string = want?.parameters?.[wantConstant.Params.CALLER_REQUEST_CODE] as string;
    AppStorage.setOrCreate<string>("callerRequestCode", callerRequestCode)
  }

  onForeground(): void {
    // 获取保存的CALLER_REQUEST_CODE
    let callerRequestCode: string = AppStorage.get<string>("callerRequestCode") as string;
    hilog.info(0x0000, 'testTag', `callerRequestCode is ${callerRequestCode}`);
    let want: Want = {};
    let resultCode = 100;
    let abilityResult: common.AbilityResult = {
      want,
      resultCode
    };
    try {
      // 将结果信息返回给调用方
      this.context.backToCallerAbilityWithResult(abilityResult, callerRequestCode)
        .then(() => {
          // 执行正常业务
          hilog.info(0x0000, 'testTag', 'backToCallerAbilityWithResult succeed');
        })
        .catch((error) => {
          let err = error as BusinessError;
          // 处理业务逻辑错误
          hilog.error(0x0000, 'testTag',
            `backToCallerAbilityWithResult failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // 捕获同步的参数错误
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      hilog.error(0x0000, 'testTag', `backToCallerAbilityWithResult failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## connectAppServiceExtensionAbility

```TypeScript
connectAppServiceExtensionAbility(want: Want, callback: ConnectOptions): long
```

将当前UIAbility连接到 [AppServiceExtensionAbility](arkts-ability-app-ability-appserviceextensionability-appserviceextensionability-c.md) 。通过返回的proxy与AppServiceExtensionAbility进行通信，以使用AppServiceExtensionAbility对外提供的能力。仅支持在主线程调用。 该接口仅在PC/2in1设备中可正常调用，在其他设备中返回801错误码。 > **说明：** > > 如果 > [AppServiceExtensionAbility](arkts-ability-app-ability-appserviceextensionability-appserviceextensionability-c.md) > 实例未启动，该接口的调用方必须为AppServiceExtensionAbility所属应用或者在AppServiceExtensionAbility支持的应用清单（即 > [extensionAbilities标签](../../../quick-start/module-configuration-file.md#extensionabilities标签)的 > appIdentifierAllowList属性）中的应用。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAbilityContext-connectAppServiceExtensionAbility(want: Want, callback: ConnectOptions): long--><!--Device-UIAbilityContext-connectAppServiceExtensionAbility(want: Want, callback: ConnectOptions): long-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | 连接 [AppServiceExtensionAbility](arkts-ability-app-ability-appserviceextensionability-appserviceextensionability-c.md) 的Want信息。 |
| callback | [ConnectOptions](arkts-ability-connectoptions-connectoptions-i.md) | 是 | ConnectOptions类型的回调函数，返回服务连接成功、连接失败、断开的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 返回连接id， [disconnectAppServiceExtensionAbility]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000201](../errorcode-ability.md#16000201-目标服务还未启动) | The target service has not been started yet. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { UIAbility, Want, common } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'AppServiceExtensionAbility'
    };
    let commRemote: rpc.IRemoteObject;
    let callback: common.ConnectOptions = {
      onConnect(elementName, remote) {
        commRemote = remote;
        console.info('onConnect...');
      },
      onDisconnect(elementName) {
        console.info('onDisconnect...');
      },
      onFailed(code) {
        console.info('onFailed...');
      }
    };
    let connection: number;

    try {
      // 连接AppServiceExtensionAbility
      connection = this.context.connectAppServiceExtensionAbility(want, callback);
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`connectAppServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { UIAbility, Want, common, bundleManager } from '@kit.AbilityKit';
import rpc from '@ohos.rpc';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'AppServiceExtensionAbility'
    };
    let commRemote: rpc.IRemoteObject;
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
      connection = this.context.connectAppServiceExtensionAbility(want, callback);
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`connectAppServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## connectServiceExtensionAbility

```TypeScript
connectServiceExtensionAbility(want: Want, options: ConnectOptions): long
```

将当前UIAbility连接到一个[ServiceExtensionAbility](../../../application-models/extensionability-overview.md)，通过返回的proxy与 ServiceExtensionAbility进行通信，以使用ServiceExtensionAbility对外提供的能力。仅支持在主线程调用。 > **说明：** > > 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAbilityContext-connectServiceExtensionAbility(want: Want, options: ConnectOptions): long--><!--Device-UIAbilityContext-connectServiceExtensionAbility(want: Want, options: ConnectOptions): long-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | 连接ServiceExtensionAbility的Want信息。 |
| options | [ConnectOptions](arkts-ability-connectoptions-connectoptions-i.md) | 是 | 回调对象，返回服务连接成功、连接失败、断开的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 返回连接id，调用方可以通过 [disconnectServiceExtensionAbility]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000053](../errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI.<br>**适用版本：** 10+ |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out.<br>**适用版本：** 10+ |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 10+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed.<br>**适用版本：** 10+ |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type.<br>**适用版本：** 10+ |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires.<br>**适用版本：** 10+ |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { UIAbility, Want, common } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'ServiceExtensionAbility'
    };
    let commRemote: rpc.IRemoteObject;
    let options: common.ConnectOptions = {
      onConnect(elementName, remote) {
        commRemote = remote;
        console.info('onConnect...');
      },
      onDisconnect(elementName) {
        console.info('onDisconnect...');
      },
      onFailed(code) {
        console.info('onFailed...');
      }
    };
    let connection: number;

    try {
      // 连接ServiceExtensionAbility
      connection = this.context.connectServiceExtensionAbility(want, options);
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`connectServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { UIAbility, Want, common, bundleManager } from '@kit.AbilityKit';
import rpc from '@ohos.rpc';
import { BusinessError } from '@kit.BasicServicesKit';

type OnConnectFn = (elementName: bundleManager.ElementName, remote: rpc.IRemoteObject) => void
type OnDisconnectFn = (elementName: bundleManager.ElementName) => void
type OnFailedFn = (code: int) => void

let commRemote: rpc.IRemoteObject;

class ConnectOptions implements common.ConnectOptions {
  onConnect: OnConnectFn = (elementName: bundleManager.ElementName, remote: rpc.IRemoteObject) => {
    commRemote = remote;
    console.info('onConnect...');
  };
  onDisconnect: OnDisconnectFn = (elementName: bundleManager.ElementName) => {
    console.info('onDisconnect...');
  };
  onFailed: OnFailedFn = (code: int) => {
    console.info('onFailed...');
  };
}

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'ServiceExtensionAbility'
    };
    let options: common.ConnectOptions = new ConnectOptions();
    let connection: long;

    try {
      connection = this.context.connectServiceExtensionAbility(want, options);
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`connectServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## connectUIServiceExtensionAbility

```TypeScript
connectUIServiceExtensionAbility(want: Want, callback: UIServiceExtensionConnectCallback) : Promise<UIServiceProxy>
```

连接一个UIServiceExtensionAbility。使用Promise异步回调。 该接口仅在PC/2in1设备中可正常调用，在其他设备中返回801错误码。 > **说明：** > > 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-connectUIServiceExtensionAbility(want: Want, callback: UIServiceExtensionConnectCallback) : Promise<UIServiceProxy>--><!--Device-UIAbilityContext-connectUIServiceExtensionAbility(want: Want, callback: UIServiceExtensionConnectCallback) : Promise<UIServiceProxy>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | 连接UIServiceExtensionAbility的必要信息。 |
| callback | [UIServiceExtensionConnectCallback](arkts-ability-uiserviceextensionconnectcallback-i.md) | 是 | 连接UIServiceExtensionAbility回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[UIServiceProxy](arkts-ability-uiserviceproxy-i.md)&gt; | Promise对象，包含connectUIServiceExtensionAbility执行后返回的 [UIServiceProxy]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const TAG: string = '[Extension] ';

@Entry
@Component
struct UIServiceExtensionAbility {
  dataCallBack : common.UIServiceExtensionConnectCallback = {
    // 接收数据
    onData: (data: Record<string, Object>) => {
      console.info(`dataCallBack received data`, JSON.stringify(data));
    },
    // 连接断开
    onDisconnect: () => {
      console.info(`dataCallBack onDisconnect`);
    }
  }

  async myConnect() {
    // 获取上下文
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    let startWant: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'UiServiceExtAbility'
    };

    try {
      // 连接服务
      context.connectUIServiceExtensionAbility(startWant, this.dataCallBack)
        .then((proxy: common.UIServiceProxy) => {
          console.info(TAG + `try to connectUIServiceExtensionAbility`, JSON.stringify(proxy));
        }).catch((err: Error) => {
        let code = (err as BusinessError).code;
        let message = (err as BusinessError).message;
        console.error(TAG + `connectUIServiceExtensionAbility failed, code is ${code}, message is ${message}`);
      });
    } catch (err) {
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(TAG + `connectUIServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    };
  }

  build() {
    RelativeContainer() {
      // 创建连接按钮
      Button('connectServiceExtensionAbility', { type: ButtonType.Capsule, stateEffect: true })
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          this.myConnect()
        });
    }
    .height('100%')
    .width('100%')
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { common, Want } from '@kit.AbilityKit';
import { BusinessError, RecordData } from '@kit.BasicServicesKit';
import { Entry, RelativeContainer, Button, Component } from '@kit.ArkUI';

const TAG: string = '[Extension] ';

class MyDataCallBack implements common.UIServiceExtensionConnectCallback {
  // 接收数据
  onData(data: Record<string, RecordData>) {
    console.info(`dataCallBack received data`, JSON.stringify(data));
  }

  // 连接断开
  onDisconnect() {
    console.info(`dataCallBack onDisconnect`);
  }
}

@Entry
@Component
struct UIServiceExtensionAbility {
  async myConnect() {
    // 获取上下文
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    let startWant: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'UiServiceExtAbility'
    };

    try {
      // 连接服务
      let dataCallBack = new MyDataCallBack();
      context.connectUIServiceExtensionAbility(startWant, dataCallBack)
        .then((proxy: common.UIServiceProxy) => {
          console.info(TAG + `try to connectUIServiceExtensionAbility`, JSON.stringify(proxy));
        }).catch((err: Error) => {
        let code = (err as BusinessError).code;
        let message = (err as BusinessError).message;
        console.info(TAG + `connectUIServiceExtensionAbility failed, code is ${code}, message is ${message}`);
      });
    } catch (err) {
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.info(TAG + `connectUIServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }

  build() {
    RelativeContainer() {
      // 创建连接按钮
      Button('connectServiceExtensionAbility')
        .onClick(() => {
          this.myConnect();
        });
    }
    .height('100%')
    .width('100%')
  }
}
```

## disconnectAppServiceExtensionAbility

```TypeScript
disconnectAppServiceExtensionAbility(connection: long): Promise<void>
```

断开与 [AppServiceExtensionAbility](arkts-ability-app-ability-appserviceextensionability-appserviceextensionability-c.md) 的连接。仅支持在主线程调用。使用Promise异步回调。 断开连接之后，为了防止使用可能失效的remote对象进行通信，建议将连接成功时返回的remote对象设置为null。 该接口仅在PC/2in1设备中可正常调用，在其他设备中返回801错误码。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAbilityContext-disconnectAppServiceExtensionAbility(connection: long): Promise<void>--><!--Device-UIAbilityContext-disconnectAppServiceExtensionAbility(connection: long): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connection | long | 是 | 在 [connectAppServiceExtensionAbility](#connectappserviceextensionability)返回的连接id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    // connection为connectAppServiceExtensionAbility中的返回值
    let connection = 1;
    let commRemote: rpc.IRemoteObject | null;

    try {
      // 断开与AppServiceExtensionAbility的连接
      this.context.disconnectAppServiceExtensionAbility(connection).then(() => {
        commRemote = null;
        // 执行正常业务
        console.info('disconnectAppServiceExtensionAbility succeed');
      }).catch((err: BusinessError) => {
        // 处理业务逻辑错误
        console.error(`disconnectAppServiceExtensionAbility failed, code is ${err.code}, message is ${err.message}`);
      });
    } catch (err) {
      commRemote = null;
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`disconnectAppServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { UIAbility } from '@kit.AbilityKit';
import rpc from '@ohos.rpc';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    // connection为connectAppServiceExtensionAbility中的返回值
    let connection = 1;
    let commRemote: rpc.IRemoteObject | null;

    try {
      this.context.disconnectAppServiceExtensionAbility(connection).then(() => {
        commRemote = null;
        // 执行正常业务
        console.info('disconnectAppServiceExtensionAbility succeed');
      }).catch((error) => {
        // 处理业务逻辑错误
        let err = error as BusinessError;
        console.error(`disconnectAppServiceExtensionAbility failed, code is ${err.code}, message is ${err.message}`);
      });
    } catch (err) {
      commRemote = null;
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`disconnectAppServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## disconnectServiceExtensionAbility

```TypeScript
disconnectServiceExtensionAbility(connection: long, callback: AsyncCallback<void>): void
```

断开与[ServiceExtensionAbility](../../../application-models/extensionability-overview.md)的连接，断开连接之后开发者需要将连接成功时返回的 remote对象置空。使用callback异步回调。仅支持在主线程调用。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAbilityContext-disconnectServiceExtensionAbility(connection: long, callback: AsyncCallback<void>): void--><!--Device-UIAbilityContext-disconnectServiceExtensionAbility(connection: long, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connection | long | 是 | 连接的ServiceExtensionAbility的标识id，即 [connectServiceExtensionAbility](#connectserviceextensionability)返回的connectionId。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当断开与ServiceExtensionAbility的连接成功，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    // connection为connectServiceExtensionAbility中的返回值
    let connection = 1;
    let commRemote: rpc.IRemoteObject | null;

    try {
      // 断开与ServiceExtensionAbility的连接
      this.context.disconnectServiceExtensionAbility(connection, (err: BusinessError) => {
        commRemote = null;
        if (err.code) {
          // 处理业务逻辑错误
          console.error(`disconnectServiceExtensionAbility failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        // 执行正常业务
        console.info('disconnectServiceExtensionAbility succeed');
      });
    } catch (err) {
      commRemote = null;
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`disconnectServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { UIAbility } from '@kit.AbilityKit';
import rpc from '@ohos.rpc';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    // connection为connectServiceExtensionAbility中的返回值
    let connection = 1;
    let commRemote: rpc.IRemoteObject | null;

    try {
      this.context.disconnectServiceExtensionAbility(connection, (err: BusinessError | null) => {
        commRemote = null;
        if (err?.code) {
          // 处理业务逻辑错误
          console.error(`disconnectServiceExtensionAbility failed, code is ${err?.code}, message is ${err?.message}`);
          return;
        }
        // 执行正常业务
        console.info('disconnectServiceExtensionAbility succeed');
      });
    } catch (err) {
      commRemote = null;
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`disconnectServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## disconnectServiceExtensionAbility

```TypeScript
disconnectServiceExtensionAbility(connection: long): Promise<void>
```

断开与[ServiceExtensionAbility](../../../application-models/extensionability-overview.md)的连接，断开连接之后开发者需要将连接成功时返回的 remote对象置空。使用Promise异步回调。仅支持在主线程调用。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAbilityContext-disconnectServiceExtensionAbility(connection: long): Promise<void>--><!--Device-UIAbilityContext-disconnectServiceExtensionAbility(connection: long): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connection | long | 是 | 连接的ServiceExtensionAbility的标识id，即 [connectServiceExtensionAbility](#connectserviceextensionability)返回的connectionId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    // connection为connectServiceExtensionAbility中的返回值
    let connection = 1;
    let commRemote: rpc.IRemoteObject | null;

    try {
      // 断开与ServiceExtensionAbility的连接
      this.context.disconnectServiceExtensionAbility(connection).then(() => {
        commRemote = null;
        // 执行正常业务
        console.info('disconnectServiceExtensionAbility succeed');
      }).catch((err: BusinessError) => {
        // 处理业务逻辑错误
        console.error(`disconnectServiceExtensionAbility failed, code is ${err.code}, message is ${err.message}`);
      });
    } catch (err) {
      commRemote = null;
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`disconnectServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { UIAbility } from '@kit.AbilityKit';
import rpc from '@ohos.rpc';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    // connection为connectServiceExtensionAbility中的返回值
    let connection = 1;
    let commRemote: rpc.IRemoteObject | null;

    try {
      this.context.disconnectServiceExtensionAbility(connection).then(() => {
        commRemote = null;
        // 执行正常业务
        console.info('disconnectServiceExtensionAbility succeed');
      }).catch((err: BusinessError<void>): void => {
        // 处理业务逻辑错误
        console.error(`disconnectServiceExtensionAbility failed, code is ${err.code}, message is ${err.message}`);
      });
    } catch (err) {
      commRemote = null;
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`disconnectServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## disconnectUIServiceExtensionAbility

```TypeScript
disconnectUIServiceExtensionAbility(proxy: UIServiceProxy): Promise<void>
```

断开与UIServiceExtensionAbility的连接。使用Promise异步回调。 > **说明：** > > 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-disconnectUIServiceExtensionAbility(proxy: UIServiceProxy): Promise<void>--><!--Device-UIAbilityContext-disconnectUIServiceExtensionAbility(proxy: UIServiceProxy): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| proxy | [UIServiceProxy](arkts-ability-uiserviceproxy-i.md) | 是 | [connectUIServiceExtensionAbility](#connectuiserviceextensionability)执行返回的Proxy。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，包含接口执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const TAG: string = '[Extension] ';

@Entry
@Component
struct UIServiceExtensionAbility {
  comProxy: common.UIServiceProxy | null = null;

  build() {
    Scroll() {
      Column() {
        // 创建断开连接的按钮
        Button('disconnectUIServiceExtensionAbility', { type: ButtonType.Capsule, stateEffect: true })
          .margin({
            top: 5,
            left: 10,
            right: 10,
            bottom: 5
          })
          .alignRules({
            center: { anchor: '__container__', align: VerticalAlign.Center },
            middle: { anchor: '__container__', align: HorizontalAlign.Center }
          })
          .onClick(() => {
            this.myDisconnectUIServiceExtensionAbility()
          });
      }
      .width('100%')
    }
    .height('100%')
  }

  myDisconnectUIServiceExtensionAbility() {
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

    try {
      // 断开UIServiceExtension连接
      context.disconnectUIServiceExtensionAbility(this.comProxy)
        .then(() => {
          console.info(TAG + `disconnectUIServiceExtensionAbility succeed ${this.comProxy}`);
        }).catch((err: Error) => {
        let code = (err as BusinessError).code;
        let message = (err as BusinessError).message;
        console.error(TAG + `disconnectUIServiceExtensionAbility failed, code is ${code}, message is ${message}`);
      });
    } catch (err) {
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(TAG + `disconnectUIServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { common, Want } from '@kit.AbilityKit';
import { BusinessError, RecordData } from '@kit.BasicServicesKit';
import { Entry, Column, Button, Component, Scroll } from '@kit.ArkUI';

const TAG: string = '[Extension] ';

class MyComProxy implements common.UIServiceProxy {
  sendData(data: Record<string, RecordData>) {
    console.info(TAG + `MyComProxy data ${data}}`);
  }
}

@Entry
@Component
struct UIServiceExtensionAbility {
  build() {
    Scroll() {
      Column() {
        // 创建断开连接的按钮
        Button('disconnectUIServiceExtensionAbility')
          .margin({
            top: 5,
            left: 10,
            right: 10,
            bottom: 5
          })
          .onClick(() => {
            this.myDisconnectUIServiceExtensionAbility();
          });
      }
      .width('100%')
    }
    .height('100%')
  }

  private myDisconnectUIServiceExtensionAbility(): void {

    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

    try {
      // 断开UIServiceExtension连接
      let comProxy = new MyComProxy();
      context.disconnectUIServiceExtensionAbility(comProxy)
        .then(() => {
          console.info(TAG + `disconnectUIServiceExtensionAbility succeed ${this.comProxy}}`);
        }).catch((err: Error) => {
        let code = (err as BusinessError).code;
        let message = (err as BusinessError).message;
        console.info(TAG + `disconnectUIServiceExtensionAbility failed, code is ${code}, message is ${message}`);
      });
    } catch (err) {
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.info(TAG + `disconnectUIServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## hideAbility

```TypeScript
hideAbility(): Promise<void>
```

隐藏当前UIAbility。使用Promise异步回调。仅支持在主线程调用。 调用此接口前要求确保应用已添加至状态栏。 该接口仅在PC/2in1设备中、或处于[自由多窗模式](../../../windowmanager/window-terminology.md#自由多窗模式)的Tablet设备中可正常调用，在其他设备中返回801错误码。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAbilityContext-hideAbility(): Promise<void>--><!--Device-UIAbilityContext-hideAbility(): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，包含接口执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not support. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000067](../errorcode-ability.md#16000067-ability启动参数校验失败) | The StartOptions check failed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
// Index.ets
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  @State hideAbility: string = 'hideAbility'

  build() {
    Row() {
      Column() {
        Text(this.hideAbility)
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

            // 隐藏当前UIAbility
            context.hideAbility().then(() => {
              console.info(`hideAbility success`);
            }).catch((err: BusinessError) => {
              console.error(`hideAbility fail, err: ${JSON.stringify(err)}`);
            });
          });
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

```TypeScript
// EntryAbility.ts
import { UIAbility, Want, StartOptions, contextConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let options: StartOptions = {
      displayId: 0,
      processMode: contextConstant.ProcessMode.NEW_PROCESS_ATTACH_TO_STATUS_BAR_ITEM,
      startupVisibility: contextConstant.StartupVisibility.STARTUP_HIDE
    };

    try {
      this.context.startAbility(want, options, (err: BusinessError) => {
        if (err.code) {
          // 处理业务逻辑错误
          console.error(`startAbility failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        // 执行正常业务
        console.info('startAbility succeed');
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

ArkTS-Sta示例：

```TypeScript
'use static'
// Index.ets
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Entry, Column, Text, Row, Component, State } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State hideAbility: string = 'hideAbility'

  build() {
    Row() {
      Column() {
        Text(this.hideAbility)
          .fontSize(30)
          .fontWeight(700)
          .onClick(() => {
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

            context.hideAbility().then(() => {
              console.info(`hideAbility success`);
            }).catch((err: BusinessError): void => {
              console.error(`hideAbility fail, err: ${JSON.stringify(err)}`);
            });
          });
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

```TypeScript
// EntryAbility.ts
import { UIAbility, Want, StartOptions, contextConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let options: StartOptions = {
      displayId: 0,
      processMode: contextConstant.ProcessMode.NEW_PROCESS_ATTACH_TO_STATUS_BAR_ITEM,
      startupVisibility: contextConstant.StartupVisibility.STARTUP_HIDE
    };

    try {
      this.context.startAbility(want, options, (err: BusinessError | null) => {
        if (err?.code) {
          // 处理业务逻辑错误
          console.error(`startAbility failed, code is ${err?.code}, message is ${err?.message}`);
          return;
        }
        // 执行正常业务
        console.info('startAbility succeed');
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

## isTerminating

```TypeScript
isTerminating(): boolean
```

查询UIAbility是否处于消亡中状态。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-isTerminating(): boolean--><!--Device-UIAbilityContext-isTerminating(): boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否处于消亡中状态。true表示处于消亡中状态，false表示不处于消亡中状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let isTerminating: boolean = this.context.isTerminating();
    console.info(`ability state is ${isTerminating}`);
  }
}
```

## moveAbilityToBackground

```TypeScript
moveAbilityToBackground(): Promise<void>
```

将处于前台的UIAbility移动到后台。使用Promise异步回调。仅支持在主线程调用。<br/><!--RP1--><!--RP1End--> 从API version 12开始，该接口仅在Phone、Wearable和TV设备中可正常调用，在其他设备上返回16000061错误码。 从API version 13开始，该接口仅在Phone、Tablet、Wearable和TV设备中可正常调用，在其他设备上返回16000061错误码。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-moveAbilityToBackground(): Promise<void>--><!--Device-UIAbilityContext-moveAbilityToBackground(): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，包含接口执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000065](../errorcode-ability.md#16000065-接口只支持ability在前台时调用) | The API can be called only when the ability is running in the foreground. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000066](../errorcode-ability.md#16000066-wukong模式不允许移动ability到前台后台) | An ability cannot switch to the foreground or background in Wukong mode. |
| [16000061](../errorcode-ability.md#16000061-不支持的操作) | Operation not supported. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  @State moveAbilityToBackground: string = 'Move To Background'

  build() {
    Row() {
      Column() {
        Text(this.moveAbilityToBackground)
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

            // 将处于前台的UIAbility移动到后台
            context.moveAbilityToBackground().then(() => {
              console.info(`moveAbilityToBackground success.`);
            }).catch((err: BusinessError) => {
              console.error(`moveAbilityToBackground error: ${JSON.stringify(err)}.`);
            });
          });
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Entry, Column, Text, Row, Component, State } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State moveAbilityToBackground: string = 'Move To Background'

  build() {
    Row() {
      Column() {
        Text(this.moveAbilityToBackground)
          .fontSize(30)
          .fontWeight(700)
          .onClick(() => {
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

            context.moveAbilityToBackground().then(() => {
              console.info(`moveAbilityToBackground success.`);
            }).catch((err: BusinessError<void>): void => {
              console.info(`moveAbilityToBackground error: ${JSON.stringify(err)}.`);
            });
          });
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## openAtomicService

```TypeScript
openAtomicService(appId: string, options?: AtomicServiceOptions): Promise<AbilityResult>
```

启动一个独立窗口的原子化服务。使用Promise异步回调。仅支持在主线程调用。 原子化服务被启动后，有如下情况： - 正常情况下原子化服务可以通过 [terminateSelfWithResult](#terminateselfwithresult) 接口销毁自身，并且返回结果给调用方。 - 异常情况下比如杀死原子化服务会返回异常结果给调用方，异常结果的resultCode为-1。 - 如果不同应用多次调用该接口启动同一个原子化服务，当这个原子化服务调用 [terminateSelfWithResult](#terminateselfwithresult) 接口销毁自身时，只将正常结果返回给最后一个调用方, 其它调用方返回异常结果，异常结果中resultCode为-1。 > **说明：** > > 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-openAtomicService(appId: string, options?: AtomicServiceOptions): Promise<AbilityResult>--><!--Device-UIAbilityContext-openAtomicService(appId: string, options?: AtomicServiceOptions): Promise<AbilityResult>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 应用的唯一标识，由云端统一分配。 |
| options | [AtomicServiceOptions](arkts-ability-app-ability-atomicserviceoptions-atomicserviceoptions-c.md) | 否 | 启动原子化服务所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AbilityResult](arkts-ability-abilityresult-abilityresult-i.md)&gt; | Promise对象，包含返回给拉起方的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000053](../errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000003](../errorcode-ability.md#16000003-指定的id不存在) | The specified ID does not exist. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

```TypeScript
import { UIAbility, common, AtomicServiceOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let appId: string = '6918661953712445909';
    let options: AtomicServiceOptions = {
      displayId: 0
    };

    try {
      // 启动原子化服务
      this.context.openAtomicService(appId, options)
        .then((result: common.AbilityResult) => {
          // 执行正常业务
          console.info('openAtomicService succeed');
        })
        .catch((error: Error): void => {
          // 处理业务逻辑错误
          let err = error as BusinessError;
          console.error(`openAtomicService failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`openAtomicService failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## openLink

```TypeScript
openLink(link: string, options?: OpenLinkOptions, callback?: AsyncCallback<AbilityResult>): Promise<void>
```

通过<!--RP2-->[App Linking](../../../application-models/app-linking-startup.md)<!--RP2End-->或 [Deep Linking](../../../application-models/deep-linking-startup.md)方式启动UIAbility，并通过回调函数接收被拉起的UIAbility退出时的返回结果。使用 Promise异步回调。仅支持在主线程调用。 通过在link字段中传入标准格式的URL，基于隐式want匹配规则拉起目标UIAbility。目标方必须同时具备以下过滤器特征，才能处理App Linking链接： - "actions"列表中包含"ohos.want.action.viewData"。 - "entities"列表中包含"entity.system.browsable"。 - "uris"列表中包含"scheme"为"https"且"domainVerify"为true的元素。 如果希望获取被拉起方终止后的结果，可以设置callback参数，此参数的使用可参照 [startAbilityForResult](#startabilityforresult) 接口。 传入的参数不合法时，如未设置必选参数或link字符串不是标准格式的URL，接口会直接抛出异常。参数校验通过，拉起目标方时出现的错误通过promise返回错误信息。 > **说明：** > > 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-openLink(link: string, options?: OpenLinkOptions, callback?: AsyncCallback<AbilityResult>): Promise<void>--><!--Device-UIAbilityContext-openLink(link: string, options?: OpenLinkOptions, callback?: AsyncCallback<AbilityResult>): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| link | string | 是 | 指示要打开的标准格式URL。 |
| options | [OpenLinkOptions](arkts-ability-app-ability-openlinkoptions-openlinkoptions-i.md) | 否 | 打开URL的选项参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AbilityResult](arkts-ability-abilityresult-abilityresult-i.md)&gt; | 否 | 回调函数，包含返回给拉起方的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，包含接口执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000053](../errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000019](../errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000136](../errorcode-ability.md#16000136-不允许通过app-linking方式拉起应用自身uiability) | The UIAbility is prohibited from launching itself via App Linking.<br>**适用版本：** 23+ |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { common, OpenLinkOptions } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

const DOMAIN = 0xeeee;
const TAG: string = '[openLinkDemo]';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Button("Call StartAbilityForResult")
        .onClick(() => {
          let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
          let link: string = 'https://www.example.com';
          let openLinkOptions: OpenLinkOptions = {
            appLinkingOnly: true,
            parameters: { demo_key: 'demo_value' }
          };

          try {
            // 通过App Linking方式启动UIAbility
            context.openLink(
              link,
              openLinkOptions,
              (err, result) => {
                hilog.error(DOMAIN, TAG, `openLink callback error.code: ${JSON.stringify(err)}`);
                hilog.info(DOMAIN, TAG, `openLink callback result: ${JSON.stringify(result.resultCode)}`);
                hilog.info(DOMAIN, TAG, `openLink callback result data: ${JSON.stringify(result.want)}`);
              }
            ).then(() => {
              hilog.info(DOMAIN, TAG, `open link success.`);
            }).catch((err: BusinessError) => {
              hilog.error(DOMAIN, TAG, `open link failed, errCode ${JSON.stringify(err.code)}`);
            });
          }
          catch (e) {
            hilog.error(DOMAIN, TAG, `exception occured, errCode ${JSON.stringify(e.code)}`);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { common, OpenLinkOptions } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError, RecordData } from '@kit.BasicServicesKit';
import { Entry, Component, Button, RelativeContainer } from '@kit.ArkUI';

const DOMAIN = 0xeeee;
const TAG: string = '[openLinkDemo]';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Button("Call StartAbilityForResult")
        .onClick(() => {
          let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
          let link: string = 'https://www.example.com';
          let openLinkOptions: OpenLinkOptions = {
            appLinkingOnly: true,
            parameters: { 'demo_key': 'demo_value' } as Record<string, RecordData>
          };

          try {
            context.openLink(
              link,
              openLinkOptions,
              (err: BusinessError | null, result: common.AbilityResult | undefined) => {
                hilog.error(DOMAIN, TAG, `openLink callback error.code: ${err}`);
                hilog.info(DOMAIN, TAG, `openLink callback result: ${result?.resultCode}`);
                hilog.info(DOMAIN, TAG, `openLink callback result data: ${result?.want}`);
              }
            ).then(() => {
              hilog.info(DOMAIN, TAG, `open link success.`);
            }).catch((err: BusinessError): void => {
              hilog.error(DOMAIN, TAG, `open link failed, errCode ${JSON.stringify(err.code)}`);
            });
          } catch (e: BusinessError) {
            hilog.error(DOMAIN, TAG, `exception occurred, errCode ${JSON.stringify(e.code)}`);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## reportDrawnCompleted

```TypeScript
reportDrawnCompleted(callback: AsyncCallback<void>): void
```

用于通知系统UIAbility对应的窗口内容已经绘制完成。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-reportDrawnCompleted(callback: AsyncCallback<void>): void--><!--Device-UIAbilityContext-reportDrawnCompleted(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，当通知系统UIAbility对应的窗口内容已经绘制完成的操作成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err?.code) {
        return;
      }

      try {
        this.context.reportDrawnCompleted((err) => {
          if (err?.code) {
            // 处理业务逻辑错误
            console.error(`reportDrawnCompleted failed, code is ${err?.code}, message is ${err?.message}`);
            return;
          }
          // 执行正常业务
          console.info('reportDrawnCompleted succeed');
        });
      } catch (err) {
        // 捕获同步的参数错误
        let code = (err as BusinessError).code;
        let message = (err as BusinessError).message;
        console.error(`reportDrawnCompleted failed, code is ${code}, message is ${message}`);
      }
    });
    console.info("MainAbility onWindowStageCreate");
  }
}
```

## requestDialogService

```TypeScript
requestDialogService(want: Want, result: AsyncCallback<dialogRequest.RequestResult>): void
```

启动一个支持模态弹框的ServiceExtensionAbility。ServiceExtensionAbility被启动后，应用弹出模态弹框，通过调用 [setRequestResult](arkts-ability-dialogrequest-requestcallback-i.md#setrequestresult)接口返回结果给调用者。 使用callback异步回调。仅支持在主线程调用。 > **说明：** > > 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAbilityContext-requestDialogService(want: Want, result: AsyncCallback<dialogRequest.RequestResult>): void--><!--Device-UIAbilityContext-requestDialogService(want: Want, result: AsyncCallback<dialogRequest.RequestResult>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | 启动ServiceExtensionAbility的Want信息。 |
| result | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;dialogRequest.RequestResult&gt; | 是 | 回调函数，当启动一个支持模态弹框的ServiceExtensionAbility成功，err中code为0， data为模态弹框请求结果；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000053](../errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

```TypeScript
import { UIAbility, Want, dialogRequest } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'AuthAccountServiceExtension'
    };

    try {
      this.context.requestDialogService(want,
        (err: BusinessError | null, result: dialogRequest.RequestResult | undefined): void => {
          if (err) {
            // 处理业务逻辑错误
            console.error(`requestDialogService failed, code is ${err.code}, message is ${err.message}`);
            return;
          }
          // 执行正常业务
          console.info(`requestDialogService succeed, result = ${JSON.stringify(result)}`);
        });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`requestDialogService failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## requestDialogService

```TypeScript
requestDialogService(want: Want): Promise<dialogRequest.RequestResult>
```

启动一个支持模态弹框的ServiceExtensionAbility。ServiceExtensionAbility被启动后，应用弹出模态弹框，通过调用 [setRequestResult](arkts-ability-dialogrequest-requestcallback-i.md#setrequestresult)接口返回结果给调用者。 使用Promise异步回调。仅支持在主线程调用。 > **说明：** > > 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAbilityContext-requestDialogService(want: Want): Promise<dialogRequest.RequestResult>--><!--Device-UIAbilityContext-requestDialogService(want: Want): Promise<dialogRequest.RequestResult>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | 启动ServiceExtensionAbility的Want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;dialogRequest.RequestResult&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000053](../errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

```TypeScript
import { UIAbility, Want, dialogRequest } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'AuthAccountServiceExtension'
    };

    try {
      this.context.requestDialogService(want)
        .then((result: dialogRequest.RequestResult) => {
          // 执行正常业务
          console.info(`requestDialogService succeed, result = ${JSON.stringify(result)}`);
        })
        .catch((error: Error) => {
          // 处理业务逻辑错误
          let err = error as BusinessError;
          console.error(`requestDialogService failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`requestDialogService failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## restartApp

```TypeScript
restartApp(want: Want): Promise<void>
```

处于获焦状态的UIAbility可以通过该接口，重启当前UIAbility所在的进程，并拉起应用内的指定UIAbility。仅支持主线程调用。使用Promise异步回调。 如果指定UIAbility就是当前UIAbility，则会刷新窗口至初始状态；如果是其他UIAbility，则会跳转并打开新的UIAbility窗口。 该接口仅在Phone设备中可正常调用，在其他设备中返回801错误码。 > **说明：** > > 通过该接口重启进程时，不会触发进程中Ability的onDestroy生命周期回调。 > > 在原子化服务调用本接口成功后的3秒内，再次调用本接口、 > [restartSelfAtomicService()](arkts-ability-abilitymanager-restartselfatomicservice-f.md)或 > [ApplicationContext.restartApp()](arkts-ability-applicationcontext-c.md#restartapp)接口中的任一接口，系统将 > 返回错误码16000064。 > > 在应用调用本接口成功后的3秒内，若再次调用本接口或 > [ApplicationContext.restartApp()](arkts-ability-applicationcontext-c.md#restartapp)接口中的任一接口，系统将 > 返回错误码16000064。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-restartApp(want: Want): Promise<void>--><!--Device-UIAbilityContext-restartApp(want: Want): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | Want类型参数，传入需要启动的UIAbility的信息，校验bundleName、abilityName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000064](../errorcode-ability.md#16000064-重启应用频繁) | Restart too frequently. |
| [16000065](../errorcode-ability.md#16000065-接口只支持ability在前台时调用) | The API can be called only when the ability is focused. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Connect to system server error. |
| [16000063](../errorcode-ability.md#16000063-重启应用指定组件无效) | The target to restart does not belong to the caller or is not a UIAbility. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { common, Want } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  @State message: string = 'restartApp with window';

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(async () => {
          let want: Want = {
            bundleName: 'com.example.myapplication',
            abilityName: 'EntryAbility'
          };
          let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
          try {
            // 重启当前UIAbility所在的进程并拉起指定UIAbility
            await context.restartApp(want);
          } catch (err) {
            hilog.error(0x0000, 'testTag', `restart failed: ${err.code}, ${err.message}`);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { hilog } from '@kit.PerformanceAnalysisKit';
import { common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Entry, RelativeContainer, FontWeight, Text, Component, State } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'restartApp with window';

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontWeight(FontWeight.Bold)
        .onClick(async () => {
          this.restartFun();
        })
    }
    .height('100%')
    .width('100%')
  }

  private restartFun() {
    let want: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    try {
      await context.restartApp(want);
    } catch (error) {
      let err = error as BusinessError;
      hilog.error(0x0000, 'testTag', `restart failed: ${err.code}, ${err.message}`);
    }
  }
}
```

## restoreWindowStage

```TypeScript
restoreWindowStage(localStorage: LocalStorage): void
```

恢复UIAbility中的WindowStage数据。仅支持在主线程调用。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-restoreWindowStage(localStorage: LocalStorage): void--><!--Device-UIAbilityContext-restoreWindowStage(localStorage: LocalStorage): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localStorage | LocalStorage | 是 | 用于恢复window stage的存储数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let storage = new LocalStorage();
    this.context.restoreWindowStage(storage);
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { UIAbility } from '@kit.AbilityKit';
import { LocalStorage } from '@ohos.arkui.stateManagement';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let storage = new LocalStorage();
    this.context.restoreWindowStage(storage);
  }
}
```

## setAbilityInstanceInfo

```TypeScript
setAbilityInstanceInfo(label: string, icon: image.PixelMap): Promise<void>
```

设置当前UIAbility实例的图标和标签信息。图标与标签信息可在任务中心和快捷栏的界面中显示。使用Promise异步回调。 该接口仅在PC/2in1设备中可正常调用，在其他设备中返回801错误码。

**起始版本：** 23

**需要权限：** ohos.permission.SET_ABILITY_INSTANCE_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAbilityContext-setAbilityInstanceInfo(label: string, icon: image.PixelMap): Promise<void>--><!--Device-UIAbilityContext-setAbilityInstanceInfo(label: string, icon: image.PixelMap): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| label | string | 是 | 新的图标标签。标签长度不超过1024字节，且不可为空字符串。 |
| icon | image.PixelMap | 是 | 新的图标。建议图标大小为512px*512px。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，包含接口执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    windowStage.loadContent('pages/Index', async (err, data) => {
      if (err.code) {
        console.error(`loadContent failed, code is ${err.code}`);
        return;
      }

      let newLabel: string = 'instance label';
      let color = new ArrayBuffer(512 * 512 * 4); // 创建一个ArrayBuffer对象，用于存储图像像素。该对象的大小为（height * width * 4）字节。
      let bufferArr = new Uint8Array(color);
      for (let i = 0; i < bufferArr.length; i += 4) {
        bufferArr[i] = 255;
        bufferArr[i+1] = 0;
        bufferArr[i+2] = 122;
        bufferArr[i+3] = 255;
      }
      let opts: image.InitializationOptions = {
        editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 512, width: 512 }
      };
      let imagePixelMap: image.PixelMap = await image.createPixelMap(color, opts);
      // 设置UIAbility实例的图标和标签信息
      this.context.setAbilityInstanceInfo(newLabel, imagePixelMap)
        .then(() => {
          console.info('setAbilityInstanceInfo success');
        }).catch((err: BusinessError) => {
        console.error(`setAbilityInstanceInfo failed, code is ${err.code}, message is ${err.message}`);
      });
    });
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { UIAbility } from '@kit.AbilityKit';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    windowStage.loadContent('pages/Index', async (err, data): void => {
      if (err) {
        console.error(`loadContent failed, code is ${err.code}`);
      }

      let newLabel: string = 'instance label';
      let color = new ArrayBuffer(0);
      let imagePixelMap: image.PixelMap = await image.createPixelMap(color, {
        size: {
          height: 100,
          width: 100
        }
      });
      this.context.setAbilityInstanceInfo(newLabel, imagePixelMap)
        .then(() => {
          console.info('setAbilityInstanceInfo success');
        }).catch((error) => {
        let err = error as BusinessError;
        console.error(`setAbilityInstanceInfo failed, code is ${err.code}, message is ${err.message}`);
      });
    });
  }
}
```

## setColorMode

```TypeScript
setColorMode(colorMode: ConfigurationConstant.ColorMode): void
```

设置UIAbility的深浅色模式。调用该接口前需要保证该UIAbility对应页面已完成加载。仅支持主线程调用。 > **说明：** > > - 调用该接口前，需要确保窗口已完成创建、且UIAbility对应的页面已完成加载，即在 > [onWindowStageCreate()](arkts-ability-app-ability-uiability-uiability-c.md#onwindowstagecreate)生命周期中通过 > [loadContent](../../../reference/apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9)方法加载页面之后调用。 > > - 调用该接口后会创建新的资源管理器对象，如果此前有缓存资源管理器，需要进行更新。 > > - 深浅色模式生效的优先级：UIAbility的深浅色模式 > 应用的深浅色模式（ > [ApplicationContext.setColorMode](arkts-ability-applicationcontext-c.md#setcolormode)）> 系统的深浅色模 > 式。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-setColorMode(colorMode: ConfigurationConstant.ColorMode): void--><!--Device-UIAbilityContext-setColorMode(colorMode: ConfigurationConstant.ColorMode): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorMode | ConfigurationConstant.ColorMode | 是 | 设置颜色模式，包括: <br> - COLOR_MODE_DARK：深色模式 <br> - COLOR_MODE_LIGHT：浅色 模式 <br> - COLOR_MODE_NOT_SET：不设置（跟随系统或应用） |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

```TypeScript
import { UIAbility, ConfigurationConstant } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';

export default class MyAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err?.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content.');
        return;
      }
      // 设置UIAbility的深浅色模式
      let uiAbilityContext = this.context;
      uiAbilityContext.setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_DARK);
    });
  }
}
```

## setMissionContinueState

```TypeScript
setMissionContinueState(state: AbilityConstant.ContinueState, callback: AsyncCallback<void>): void
```

设置UIAbility任务的流转状态。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-setMissionContinueState(state: AbilityConstant.ContinueState, callback: AsyncCallback<void>): void--><!--Device-UIAbilityContext-setMissionContinueState(state: AbilityConstant.ContinueState, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | AbilityConstant.ContinueState | 是 | 流转状态。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，当设置UIAbility任务的流转状态成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { UIAbility, AbilityConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    try {
      this.context.setMissionContinueState(AbilityConstant.ContinueState.INACTIVE, (err: BusinessError) => {
        if (err.code) {
          console.error(`setMissionContinueState failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        console.info('setMissionContinueState succeed');
      });
    } catch (err) {
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`setMissionContinueState failed, code is ${code}, message is ${message}`);
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import UIAbility from '@ohos.app.ability.UIAbility';
import AbilityConstant from '@ohos.app.ability.AbilityConstant';
import Want from '@ohos.app.ability.Want';
import { BusinessError } from '@ohos.base';

export default class EntryAbility extends UIAbility {
  onForeground() {
    this.context.setMissionContinueState(AbilityConstant.ContinueState.INACTIVE, (result: BusinessError|null,data:string[]|undefined) => {
      console.info(`setMissionContinueState: ${JSON.stringify(result)}`);
    });
  }
}
```

## setMissionContinueState

```TypeScript
setMissionContinueState(state: AbilityConstant.ContinueState): Promise<void>
```

设置UIAbility任务的流转状态。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-setMissionContinueState(state: AbilityConstant.ContinueState): Promise<void>--><!--Device-UIAbilityContext-setMissionContinueState(state: AbilityConstant.ContinueState): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | AbilityConstant.ContinueState | 是 | 流转状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，包含接口执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

ArkTS-Dyn示例:

```TypeScript
import { UIAbility, AbilityConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    this.context.setMissionContinueState(AbilityConstant.ContinueState.INACTIVE).then(() => {
      console.info('success');
    }).catch((err: BusinessError) => {
      console.error(`setMissionContinueState failed, code is ${err.code}, message is ${err.message}`);
    });
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import UIAbility from '@ohos.app.ability.UIAbility';
import AbilityConstant from '@ohos.app.ability.AbilityConstant';
import Want from '@ohos.app.ability.Want';
import { BusinessError } from '@ohos.base';

export default class EntryAbility extends UIAbility {
  onForeground() {
    this.context.setMissionContinueState(AbilityConstant.ContinueState.INACTIVE).then(() => {
      console.info('success');
    }).catch((err: Error) => {
      console.error(`setMissionContinueState failed, code is ${err.code}, message is ${err.message}`);
    });
  }
}
```

## setMissionLabel

```TypeScript
setMissionLabel(label: string, callback: AsyncCallback<void>): void
```

设置UIAbility在多任务界面中显示的名称。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-setMissionLabel(label: string, callback: AsyncCallback<void>): void--><!--Device-UIAbilityContext-setMissionLabel(label: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| label | string | 是 | 任务的名称。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，当设置UIAbility在多任务界面中显示的名称成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

```TypeScript
import { UIAbility, AbilityConstant, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    this.context.setMissionLabel('test', (err: BusinessError | null) => {
      if (err.code) {
        console.error(`setMissionLabel failed, code is ${err.code}, message is ${err.message}`);
        return;
      }
      console.info('setMissionLabel succeed');
    });
  }
}
```

## setMissionLabel

```TypeScript
setMissionLabel(label: string): Promise<void>
```

设置UIAbility在多任务界面中显示的名称。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-setMissionLabel(label: string): Promise<void>--><!--Device-UIAbilityContext-setMissionLabel(label: string): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| label | string | 是 | 任务的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，包含接口执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

```TypeScript
import { UIAbility, AbilityConstant, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    this.context.setMissionLabel('test').then(() => {
      console.info('success');
    }).catch((err: BusinessError<void>): void => {
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`setMissionLabel failed, code is ${code}, message is ${message}`);
    });
  }
}
```

## setMissionWindowIcon

```TypeScript
setMissionWindowIcon(windowIcon: image.PixelMap): Promise<void>
```

设置当前UIAbility在应用窗口、任务中心应用卡片、快捷栏窗口快照的图标。使用Promise异步回调。 该接口仅在PC/2in1设备中可正常调用，在其他设备中返回801错误码。 > **说明：** > > setMissionWindowIcon<!--Del-->、 > [setMissionIcon](arkts-ability-uiabilitycontext-c-sys.md#setmissionicon) > <!--DelEnd-->和 > [setAbilityInstanceInfo](#setabilityinstanceinfo)之间不存在调用优先级关系。 > 当多个接口被依次调用时，后一次调用的接口所设置的图标信息将覆盖之前调用接口所设置的内容，最终生效的图标以最后一次调用的接口为准。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAbilityContext-setMissionWindowIcon(windowIcon: image.PixelMap): Promise<void>--><!--Device-UIAbilityContext-setMissionWindowIcon(windowIcon: image.PixelMap): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowIcon | image.PixelMap | 是 | 在应用窗口、任务中心应用卡片、快捷栏窗口快照显示的Ability图标。图标必须为正方形，且大小不能超过128M，否则返回401参数错误。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000135](../errorcode-ability.md#16000135-uiability的主窗不存在) | The main window of this ability not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. 1. Connect to system service failed; 2.System service failed to communicate with dependency module. |

**示例**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let imagePixelMap: image.PixelMap;
    let color = new ArrayBuffer(1024 * 1024 * 4); // 创建一个ArrayBuffer对象，用于存储图像像素。该对象的大小为（height * width * 4）字节。
    let bufferArr = new Uint8Array(color);
    for (let i = 0; i < bufferArr.length; i += 4) {
      bufferArr[i] = 255;
      bufferArr[i+1] = 0;
      bufferArr[i+2] = 122;
      bufferArr[i+3] = 255;
    }
    image.createPixelMap(color, {
      editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 1024, width: 1024 }
    }).then((data) => {
      imagePixelMap = data;
      this.context.setMissionWindowIcon(imagePixelMap)
        .then(() => {
          console.info('setMissionWindowIcon succeed');
        })
        .catch((err: BusinessError) => {
          console.error(`setMissionWindowIcon failed, code is ${err.code}, message is ${err.message}`);
        });
    }).catch((err: BusinessError) => {
      console.error(`createPixelMap failed, code is ${err.code}, message is ${err.message}`);
    });
  }
}
```

## setOnNewWantSkipScenarios

```TypeScript
setOnNewWantSkipScenarios(scenarios: int): Promise<void>
```

在特定场景下拉起UIAbility时，如果不需要触发[onNewWant](arkts-ability-app-ability-uiability-uiability-c.md#onnewwant)生命周期回调，可以通过该接口设置。仅支持在主线 程调用。使用Promise异步回调。 > **说明：** > > 该接口通常用于[onCreate](arkts-ability-app-ability-uiability-uiability-c.md#oncreate)生命周期回调中。入参取值建议包含所有的 > [Scenarios](arkts-ability-contextconstant-scenarios-e.md)枚举值。详见下方示例代码。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-setOnNewWantSkipScenarios(scenarios: int): Promise<void>--><!--Device-UIAbilityContext-setOnNewWantSkipScenarios(scenarios: int): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scenarios | int | 是 | 取值范围请参考[Scenarios](arkts-ability-contextconstant-scenarios-e.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: Connection to service failed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { AbilityConstant, contextConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    let scenarios: number = contextConstant.Scenarios.SCENARIO_MOVE_MISSION_TO_FRONT |
      contextConstant.Scenarios.SCENARIO_SHOW_ABILITY |
      contextConstant.Scenarios.SCENARIO_BACK_TO_CALLER_ABILITY_WITH_RESULT;

    try {
      // 设置特定场景下拉起UIAbility时不触发onNewWant生命周期回调
      this.context.setOnNewWantSkipScenarios(scenarios).then(() => {
        // 执行正常业务
        console.info('setOnNewWantSkipScenarios succeed');
      }).catch((err: BusinessError) => {
        // 处理业务逻辑错误
        console.error(`setOnNewWantSkipScenarios failed, code is ${err.code}, message is ${err.message}`);
      });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`setOnNewWantSkipScenarios failed, code is ${code}, message is ${message}`);
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { AbilityConstant, contextConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    let scenarios: int = contextConstant.Scenarios.SCENARIO_MOVE_MISSION_TO_FRONT |
    contextConstant.Scenarios.SCENARIO_SHOW_ABILITY |
    contextConstant.Scenarios.SCENARIO_BACK_TO_CALLER_ABILITY_WITH_RESULT;

    try {
      this.context.setOnNewWantSkipScenarios(scenarios).then(() => {
        // 执行正常业务
        console.info('setOnNewWantSkipScenarios succeed');
      }).catch((error: Error) => {
        // 处理业务逻辑错误
        let err = error as BusinessError;
        console.error(`setOnNewWantSkipScenarios failed, code is ${err.code}, message is ${err.message}`);
      });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`setOnNewWantSkipScenarios failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## setRestoreEnabled

```TypeScript
setRestoreEnabled(enabled: boolean): void
```

设置UIAbility是否启用备份恢复。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-setRestoreEnabled(enabled: boolean): void--><!--Device-UIAbilityContext-setRestoreEnabled(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 表示是否启用恢复。true表示启用，false表示不启用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | If the input parameter is not valid parameter. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

```TypeScript
import { UIAbility, AbilityConstant, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let enabled = true;
    try {
      this.context.setRestoreEnabled(enabled);
    } catch (paramError) {
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`setRestoreEnabled failed, err code: ${code}, err msg: ${message}`);
    }
  }
}
```

## showAbility

```TypeScript
showAbility(): Promise<void>
```

显示当前UIAbility。使用Promise异步回调。仅支持在主线程调用。 调用此接口前要求确保应用已添加至状态栏。 该接口仅在PC/2in1设备中、或处于[自由多窗模式](../../../windowmanager/window-terminology.md#自由多窗模式)的Tablet设备中可正常调用，在其他设备中返回801错误码。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAbilityContext-showAbility(): Promise<void>--><!--Device-UIAbilityContext-showAbility(): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，包含接口执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not support. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000067](../errorcode-ability.md#16000067-ability启动参数校验失败) | The StartOptions check failed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
// Index.ets
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  @State showAbility: string = 'showAbility'

  build() {
    Row() {
      Column() {
        Text(this.showAbility)
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

            // 显示当前UIAbility
            context.showAbility().then(() => {
              console.info(`showAbility success`);
            }).catch((err: BusinessError) => {
              console.error(`showAbility fail, err: ${JSON.stringify(err)}`);
            });
          });
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

```TypeScript
// EntryAbility.ts
import { UIAbility, Want, StartOptions, contextConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let options: StartOptions = {
      displayId: 0,
      processMode: contextConstant.ProcessMode.NEW_PROCESS_ATTACH_TO_STATUS_BAR_ITEM,
      startupVisibility: contextConstant.StartupVisibility.STARTUP_SHOW
    };

    try {
      // 启动UIAbility
      this.context.startAbility(want, options, (err: BusinessError) => {
        if (err.code) {
          // 处理业务逻辑错误
          console.error(`startAbility failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        // 执行正常业务
        console.info('startAbility succeed');
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

ArkTS-Sta示例：

```TypeScript
'use static'
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Entry, Column, Text, Row, Component, State } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State moveAbilityToBackground: string = 'Move To Background'

  build() {
    Row() {
      Column() {
        Text(this.moveAbilityToBackground)
          .fontSize(30)
          .fontWeight(700)
          .onClick(() => {
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

            context.moveAbilityToBackground().then(() => {
              console.info(`moveAbilityToBackground success.`);
            }).catch((err: BusinessError<void>): void => {
              console.info(`moveAbilityToBackground error: ${JSON.stringify(err)}.`);
            });
          });
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

```TypeScript
// EntryAbility.ts
import { UIAbility, Want, StartOptions, contextConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let options: StartOptions = {
      displayId: 0,
      processMode: contextConstant.ProcessMode.NEW_PROCESS_ATTACH_TO_STATUS_BAR_ITEM,
      startupVisibility: contextConstant.StartupVisibility.STARTUP_SHOW
    };

    try {
      this.context.startAbility(want, options, (err: BusinessError | null) => {
        if (err?.code) {
          // 处理业务逻辑错误
          console.error(`startAbility failed, code is ${err?.code}, message is ${err?.message}`);
          return;
        }
        // 执行正常业务
        console.info('startAbility succeed');
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

## startAbility

```TypeScript
startAbility(want: Want, callback: AsyncCallback<void>): void
```

启动一个UIAbility。使用callback异步回调。仅支持在主线程调用。 > **说明：** > > 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-startAbility(want: Want, callback: AsyncCallback<void>): void--><!--Device-UIAbilityContext-startAbility(want: Want, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | 启动UIAbility的必要信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，当接口调用成功，err中code为0，message为空字符串；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000053](../errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000080](../errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |
| [16000018](../errorcode-ability.md#16000018-限制api-11以上版本三方应用跳转) | Redirection to a third-party application is not allowed in API version greater than 11.<br>**适用版本：** 12+ |
| [16000019](../errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found.<br>**适用版本：** 12+ |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000071](../errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000076](../errorcode-ability.md#16000076-指定的app_instance_key不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000077](../errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../errorcode-ability.md#16000079-不支持指定app_instance_key) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000072](../errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000073](../errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

```TypeScript
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };

    try {
      // 启动UIAbility
      this.context.startAbility(want, (err: BusinessError<void> | null) => {
        if (err?.code) {
          // 处理业务逻辑错误
          console.error(`startAbility failed, code is ${err?.code}, message is ${err?.message}`);
          return;
        }
        // 执行正常业务
        console.info('startAbility succeed');
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

## startAbility

```TypeScript
startAbility(want: Want, options: StartOptions, callback: AsyncCallback<void>): void
```

启动一个UIAbility。使用callback异步回调。仅支持在主线程调用。 > **说明：** > > 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-startAbility(want: Want, options: StartOptions, callback: AsyncCallback<void>): void--><!--Device-UIAbilityContext-startAbility(want: Want, options: StartOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | 启动UIAbility的必要信息。 |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | 是 | 启动UIAbility所携带的参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，当接口调用成功，err中code为0，message为空字符串；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000053](../errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16300003](../errorcode-ability.md#16300003-目标应用程序不是自身应用程序) | The target application is not the current application.<br>**适用版本：** 12+ |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not support.<br>**适用版本：** 12+ |
| [16000080](../errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |
| [16000018](../errorcode-ability.md#16000018-限制api-11以上版本三方应用跳转) | Redirection to a third-party application is not allowed in API version greater than 11.<br>**适用版本：** 12+ |
| [16000019](../errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found.<br>**适用版本：** 12+ |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000068](../errorcode-ability.md#16000068-ability已经在运行中) | The ability is already running.<br>**适用版本：** 12+ |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000071](../errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type.<br>**适用版本：** 9+ |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000067](../errorcode-ability.md#16000067-ability启动参数校验失败) | The StartOptions check failed.<br>**适用版本：** 12+ |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000076](../errorcode-ability.md#16000076-指定的app_instance_key不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000077](../errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../errorcode-ability.md#16000079-不支持指定app_instance_key) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000072](../errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000073](../errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden.<br>**适用版本：** 9+ |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

```TypeScript
import { UIAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let options: StartOptions = {
      displayId: 0
    };

    try {
      this.context.startAbility(want, options, (err: BusinessError<void> | null) => {
        if (err?.code) {
          // 处理业务逻辑错误
          console.error(`startAbility failed, code is ${err?.code}, message is ${err?.message}`);
          return;
        }
        // 执行正常业务
        console.info('startAbility succeed');
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

## startAbility

```TypeScript
startAbility(want: Want, options?: StartOptions): Promise<void>
```

启动一个UIAbility。使用Promise异步回调。仅支持在主线程调用。 > **说明：** > > 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-startAbility(want: Want, options?: StartOptions): Promise<void>--><!--Device-UIAbilityContext-startAbility(want: Want, options?: StartOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | 启动UIAbility的必要信息。 |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | 否 | 启动UIAbility所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000053](../errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16300003](../errorcode-ability.md#16300003-目标应用程序不是自身应用程序) | The target application is not the current application.<br>**适用版本：** 12+ |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not support.<br>**适用版本：** 12+ |
| [16000080](../errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |
| [16000018](../errorcode-ability.md#16000018-限制api-11以上版本三方应用跳转) | Redirection to a third-party application is not allowed in API version greater than 11.<br>**适用版本：** 12+ |
| [16000019](../errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found.<br>**适用版本：** 12+ |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000068](../errorcode-ability.md#16000068-ability已经在运行中) | The ability is already running.<br>**适用版本：** 12+ |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000071](../errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000067](../errorcode-ability.md#16000067-ability启动参数校验失败) | The StartOptions check failed.<br>**适用版本：** 12+ |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000076](../errorcode-ability.md#16000076-指定的app_instance_key不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000077](../errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../errorcode-ability.md#16000079-不支持指定app_instance_key) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000072](../errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000073](../errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

```TypeScript
import { UIAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let options: StartOptions = {
      displayId: 0
    };

    try {
      // 启动UIAbility
      this.context.startAbility(want, options)
        .then(() => {
          // 执行正常业务
          console.info('startAbility succeed');
        })
        .catch((err: BusinessError<void>): void => {
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

## startAbilityByCall

```TypeScript
startAbilityByCall(want: Want): Promise<Caller>
```

该接口用于获取[Caller](arkts-ability-app-ability-uiability-caller-i.md)通信对象，以便于与 [Callee](arkts-ability-app-ability-uiability-callee-i.md)进行通信。如果指定UIAbility未启动，则会将UIAbility启动至前台或后台。使用Promise异步回调。仅支持在主线程调 用。 该接口不支持拉起启动模式为[specified模式](../../../application-models/uiability-launch-type.md#specified启动模式)的UIAbility。 > **说明：** > > - 跨设备场景下，调用方与目标方必须为同一应用。 > > - 同设备场景下，要求调用方与目标方为不同应用，且调用方具备ohos.permission.ABILITY_BACKGROUND_COMMUNICATION权限（该权限仅系统应用可申请）。 > > - 此外如果应用需要在后台调用该接口，需要具备ohos.permission.START_ABILITIES_FROM_BACKGROUND（该权限仅系统应用可申请）。更多的组件启动规则详见 > [组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。 > > **说明：** > > - API version 10及之前版本，需申请ohos.permission.ABILITY_BACKGROUND_COMMUNICATION（该权限仅系统应用可用）。 > > - API version 11开始，仅需申请ohos.permission.DISTRIBUTED_DATASYNC（该权限仅当执行应用间建链操作时由软总线实施权限校验，在应用拉起阶段不做校验）。

**起始版本：** 23

**需要权限：** 
- API版本11+：ohos.permission.DISTRIBUTED_DATASYNC
- API版本9 - 10：ohos.permission.ABILITY_BACKGROUND_COMMUNICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAbilityContext-startAbilityByCall(want: Want): Promise<Caller>--><!--Device-UIAbilityContext-startAbilityByCall(want: Want): Promise<Caller>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | 传入需要启动的UIAbility信息，包含abilityName、moduleName、bundleName、deviceId、parameters（可选）。将parameters中的' ohos.aafwk.param.callAbilityToForeground'配置为true可将UIAbility拉起到前台；否则表示将UIAbility拉起到后台。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Caller](arkts-ability-app-ability-uiability-caller-i.md)&gt; | Promise对象，获取要通讯的caller对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000080](../errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1.Connect to system service failed. 2.Sending restart message to system service failed. 3.System service failed to communicate with dependency module. 4.Non-system applications are only allowed to call this interface across devices, not on the current device. |
| [16000018](../errorcode-ability.md#16000018-限制api-11以上版本三方应用跳转) | Redirection to a third-party application is not allowed in API version greater than 11.<br>**适用版本：** 12+ |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission.<br>**适用版本：** 9+ |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000071](../errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released.<br>**适用版本：** 9+ |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000076](../errorcode-ability.md#16000076-指定的app_instance_key不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000077](../errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../errorcode-ability.md#16000079-不支持指定app_instance_key) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000072](../errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000073](../errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

下面代码展示的是，调用方启动目标方到后台，获取Caller成功后发消息到目标方，然后释放Caller对象。

```TypeScript
import { Caller, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { rpc } from '@kit.IPCKit';

const DOMAIN = 0x0000;
const LOG_TAG = 'TEST_TAG';

class TestParcelable implements rpc.Parcelable {
  age: number = 0;
  name: string = '';
  marshalling(dataOut: rpc.MessageSequence): boolean {
    dataOut.writeInt(this.age);
    dataOut.writeString(this.name);
    return true;
  }
  unmarshalling(dataIn: rpc.MessageSequence): boolean {
    this.age = dataIn.readInt();
    this.name = dataIn.readString();
    return true;
  }
}

export default class EntryAbility extends UIAbility {
  async onForeground() {
    let caller: Caller;
    // 后台启动Ability
    let wantBackground: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility',
    };

    try {
      // 获取Caller通信对象，将UIAbility启动到后台
      caller = await this.context.startAbilityByCall(wantBackground);
      await caller.call('TEST_CALL', new TestParcelable());
      caller.release();
    } catch (err) {
      // 处理入参错误异常
      hilog.error(DOMAIN, LOG_TAG, `startAbilityByCall failed ${err}`);
    }
  }
}
```

下面代码展示，目标方启动后注册监听，销毁时取消监听。

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { rpc } from '@kit.IPCKit';

const DOMAIN = 0x0000;
const LOG_TAG = 'TEST_TAG';

class TestParcelable implements rpc.Parcelable {
  age: number = 0;
  name: string = '';
  marshalling(dataOut: rpc.MessageSequence): boolean {
    dataOut.writeInt(this.age);
    dataOut.writeString(this.name);
    return true;
  }
  unmarshalling(dataIn: rpc.MessageSequence): boolean {
    this.age = dataIn.readInt();
    this.name = dataIn.readString();
    return true;
  }
}

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(DOMAIN, LOG_TAG, '%{public}s', 'Ability onCreate');
    // 注册监听
    this.callee.on('TEST_CALL', (data: rpc.MessageSequence) => {
      let recv = new TestParcelable();
      data.readParcelable(recv);
      recv.age++;
      return recv;
    });
  }

  onDestroy(): void {
    hilog.info(DOMAIN, LOG_TAG, '%{public}s', 'Ability onDestroy');
    // 取消监听
    this.callee.off('TEST_CALL');
  }
}
```

下面代码展示，调用方启动目标方到前台场景。

```TypeScript
import { Caller, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
const LOG_TAG = 'TEST_TAG';

export default class EntryAbility extends UIAbility {
  async onForeground() {
    let caller: Caller;
    // 启动UIAbility到前台，将parameters中的'ohos.aafwk.param.callAbilityToForeground'配置为true
    let wantForeground: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility',
      parameters: {
        'ohos.aafwk.param.callAbilityToForeground': true
      }
    };

    try {
      // 获取Caller通信对象，将UIAbility启动到前台
      caller = await this.context.startAbilityByCall(wantForeground);
      caller.release();
    } catch (err) {
      // 处理入参错误异常
      hilog.error(DOMAIN, LOG_TAG, `startAbilityByCall failed ${err}`);
    }
  }
}
```

后台启动：

```TypeScript
'use static'
import { UIAbility, Caller, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let caller: Caller;
    // 后台启动Ability，不配置parameters
    let wantBackground: Want = {
      bundleName: 'com.example.myapplication',
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
        }).catch((err: BusinessError<void>): void => {
        // 处理业务逻辑错误
        console.error(`startAbilityByCall failed, code is ${err.code}, message is ${err.message}`);
      });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startAbilityByCall failed, code is ${code}, message is ${message}`);
    }
  }
}
```

前台启动：

```TypeScript
import { UIAbility, Caller, Want } from '@kit.AbilityKit';
import { BusinessError, RecordData } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let caller: Caller;
    // 前台启动Ability，将parameters中的'ohos.aafwk.param.callAbilityToForeground'配置为true
    let wantForeground: Want = {
      bundleName: 'com.example.myapplication',
      moduleName: 'entry',
      abilityName: 'EntryAbility',
      deviceId: '',
      parameters: {
        'ohos.aafwk.param.callAbilityToForeground': true
      } as Record<string, RecordData>
    };

    try {
      this.context.startAbilityByCall(wantForeground)
        .then((obj: Caller) => {
          // 执行正常业务
          caller = obj;
          console.info('startAbilityByCall succeed');
        }).catch((err: BusinessError<void>): void => {
        // 处理业务逻辑错误
        console.error(`startAbilityByCall failed, code is ${err.code}, message is ${err.message}`);
      });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startAbilityByCall failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## startAbilityByType

```TypeScript
startAbilityByType(type: string, wantParam: Record<string, Object>,
    abilityStartCallback: AbilityStartCallback, callback: AsyncCallback<void>): void
```

通过type隐式启动[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)。使用callback异步回调。仅支持在主线 程调用，仅支持处于前台的应用调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-startAbilityByType(type: string, wantParam: Record<string, Object>,    abilityStartCallback: AbilityStartCallback, callback: AsyncCallback<void>): void--><!--Device-UIAbilityContext-startAbilityByType(type: string, wantParam: Record<string, Object>,    abilityStartCallback: AbilityStartCallback, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 启动的UIExtensionAbility类型，取值详见 [通过startAbilityByType接口拉起垂类面板](../../../application-models/start-intent-panel.md#匹配规则)。 |
| wantParam | Record&lt;string, Object&gt; | 是 | 表示扩展参数。 |
| abilityStartCallback | [AbilityStartCallback](arkts-ability-abilitystartcallback-i.md) | 是 | 回调函数，返回启动失败后的详细错误信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，当接口调用成功，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 11+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist.<br>**适用版本：** 11+ |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type.<br>**适用版本：** 11+ |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released.<br>**适用版本：** 11+ |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 11+ |

**示例**

```TypeScript
import { UIAbility, common } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let wantParam: Record<string, Object> = {
      'time': '2023-10-23 20:45'
    };
    let abilityStartCallback: common.AbilityStartCallback = {
      onError: (code: number, name: string, message: string) => {
        console.info(`code:` + code + `name:` + name + `message:` + message);
      },
      onResult: (abilityResult: common.AbilityResult) => {
        console.info(`resultCode:` + abilityResult.resultCode + `bundleName:` + abilityResult.want?.bundleName);
      }
    };

    this.context.startAbilityByType("photoEditor", wantParam, abilityStartCallback, (err) => {
      if (err) {
        console.error(`startAbilityByType fail, err: ${JSON.stringify(err)}`);
      } else {
        console.info(`success`);
      }
    });
  }
}
```

## startAbilityByType

```TypeScript
startAbilityByType(type: string, wantParam: Record<string, RecordData>,
    abilityStartCallback: AbilityStartCallback, callback: AsyncCallback<void>): void
```

通过type隐式启动[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)。使用callback异步回调。仅支持在主线 程调用，仅支持处于前台的应用调用。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAbilityContext-startAbilityByType(type: string, wantParam: Record<string, RecordData>,    abilityStartCallback: AbilityStartCallback, callback: AsyncCallback<void>): void--><!--Device-UIAbilityContext-startAbilityByType(type: string, wantParam: Record<string, RecordData>,    abilityStartCallback: AbilityStartCallback, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 启动的UIExtensionAbility类型，取值详见 [通过startAbilityByType接口拉起垂类面板](../../../application-models/start-intent-panel.md#匹配规则)。 |
| wantParam | Record&lt;string, [RecordData](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-recorddata-t.md)&gt; | 是 | 表示扩展参数。 |
| abilityStartCallback | [AbilityStartCallback](arkts-ability-abilitystartcallback-i.md) | 是 | 回调函数，返回启动失败后的详细错误信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，当接口调用成功，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例**

ArkTS-Sta示例：

```TypeScript
'use static'
import { UIAbility, common } from '@kit.AbilityKit';
import { RecordData } from '@kit.BasicServicesKit';

class MyAbilityStartCallback implements common.AbilityStartCallback {
  onError(code: int, name: string, message: string): void {
    console.info(`startAbilityByType Error:` + "code:" + code + "name:" + name + "message:" + message);
  }

  onResult?: (abilityResult: common.AbilityResult) => void = (parameter: common.AbilityResult) => {
    console.info(`startAbilityByType resultCode:` + parameter.resultCode + `bundleName:` + parameter.want?.bundleName);
  }
}

export default class EntryAbility extends UIAbility {
  onForeground() {
    let wantParam: Record<string, RecordData> = {
      'time': '2023-10-23 20:45'
    };
    let abilityStartCallback = new MyAbilityStartCallback();

    this.context.startAbilityByType("photoEditor", wantParam, abilityStartCallback, (err) => {
      if (err) {
        console.error(`startAbilityByType fail, err: ${JSON.stringify(err)}`);
      } else {
        console.info(`success`);
      }
    });
  }
}
```

## startAbilityByType

```TypeScript
startAbilityByType(type: string, wantParam: Record<string, Object>,
    abilityStartCallback: AbilityStartCallback): Promise<void>
```

通过type隐式启动[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)。使用Promise异步回调。仅支持在主线程 调用，仅支持处于前台的应用调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-startAbilityByType(type: string, wantParam: Record<string, Object>,    abilityStartCallback: AbilityStartCallback): Promise<void>--><!--Device-UIAbilityContext-startAbilityByType(type: string, wantParam: Record<string, Object>,    abilityStartCallback: AbilityStartCallback): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 启动的UIExtensionAbility类型，取值详见 [通过startAbilityByType接口拉起垂类面板](../../../application-models/start-intent-panel.md#匹配规则)。 |
| wantParam | Record&lt;string, Object&gt; | 是 | 表示扩展参数。 |
| abilityStartCallback | [AbilityStartCallback](arkts-ability-abilitystartcallback-i.md) | 是 | 回调函数，返回启动失败后的详细错误信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，包含接口执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 11+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist.<br>**适用版本：** 11+ |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type.<br>**适用版本：** 11+ |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released.<br>**适用版本：** 11+ |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 11+ |

**示例**

```TypeScript
import { UIAbility, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let wantParam: Record<string, Object> = {
      'time': '2023-10-23 20:45'
    };
    let abilityStartCallback: common.AbilityStartCallback = {
      onError: (code: number, name: string, message: string) => {
        console.info(`code:` + code + `name:` + name + `message:` + message);
      },
      onResult: (abilityResult: common.AbilityResult) => {
        console.info(`resultCode:` + abilityResult.resultCode + `bundleName:` + abilityResult.want?.bundleName);
      }
    };

    this.context.startAbilityByType("photoEditor", wantParam, abilityStartCallback).then(() => {
      console.info(`startAbilityByType success`);
    }).catch((err: BusinessError) => {
      console.error(`startAbilityByType fail, err: ${JSON.stringify(err)}`);
    });
  }
}
```

## startAbilityByType

```TypeScript
startAbilityByType(type: string, wantParam: Record<string, RecordData>,
    abilityStartCallback: AbilityStartCallback): Promise<void>
```

通过type隐式启动[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)。使用Promise异步回调。仅支持在主线程 调用，仅支持处于前台的应用调用。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAbilityContext-startAbilityByType(type: string, wantParam: Record<string, RecordData>,    abilityStartCallback: AbilityStartCallback): Promise<void>--><!--Device-UIAbilityContext-startAbilityByType(type: string, wantParam: Record<string, RecordData>,    abilityStartCallback: AbilityStartCallback): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 启动的UIExtensionAbility类型，取值详见 [通过startAbilityByType接口拉起垂类面板](../../../application-models/start-intent-panel.md#匹配规则)。 |
| wantParam | Record&lt;string, [RecordData](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-recorddata-t.md)&gt; | 是 | 表示扩展参数。 |
| abilityStartCallback | [AbilityStartCallback](arkts-ability-abilitystartcallback-i.md) | 是 | 回调函数，返回启动失败后的详细错误信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例**

ArkTS-Sta示例：

```TypeScript
'use static'
import { UIAbility, common } from '@kit.AbilityKit';
import { BusinessError, RecordData } from '@kit.BasicServicesKit';

class MyAbilityStartCallback implements common.AbilityStartCallback {
  onError(code: int, name: string, message: string): void {
    console.info(`startAbilityByType Error:` + "code:" + code + "name:" + name + "message:" + message);
  }

  onResult?: (abilityResult: common.AbilityResult) => void = (parameter: common.AbilityResult) => {
    console.info(`startAbilityByType resultCode:` + parameter.resultCode + `bundleName:` + parameter.want?.bundleName);
  }
}

export default class EntryAbility extends UIAbility {
  onForeground() {
    let wantParam: Record<string, RecordData> = {
      'time': '2023-10-23 20:45'
    };
    let abilityStartCallback = new MyAbilityStartCallback();

    this.context.startAbilityByType("photoEditor", wantParam, abilityStartCallback).then(() => {
      console.info(`startAbilityByType success`);
    }).catch((error) => {
      let err = error as BusinessError;
      console.error(`startAbilityByType fail, err: ${JSON.stringify(err)}`);
    });
  }
}
```

## startAbilityForResult

```TypeScript
startAbilityForResult(want: Want, callback: AsyncCallback<AbilityResult>): void
```

启动一个UIAbility，并通过回调函数接收被拉起的UIAbility退出时的返回结果。使用callback异步回调。仅支持在主线程调用。 UIAbility被启动后，有如下情况： - 正常情况下可以通过调用 [terminateSelfWithResult](#terminateselfwithresult) 接口销毁自身，并将结果返回给调用方。 - 异常情况下比如杀死UIAbility会将异常结果返回给调用方，异常结果中resultCode为-1。 - 如果被启动的UIAbility是[单实例模式](../../../application-models/uiability-launch-type.md#singleton启动模式)，且这个UIAbility被不同应用多次调 用该接口启动，当这个UIAbility调用 [terminateSelfWithResult](#terminateselfwithresult) 接口销毁自身时，只将正常结果返回给最后一个调用方，其它调用方返回异常结果，异常结果中resultCode为-1。 > **说明：** > > 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-startAbilityForResult(want: Want, callback: AsyncCallback<AbilityResult>): void--><!--Device-UIAbilityContext-startAbilityForResult(want: Want, callback: AsyncCallback<AbilityResult>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | 启动Ability的必要信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AbilityResult](arkts-ability-abilityresult-abilityresult-i.md)&gt; | 是 | 回调函数，当接口调用成功，err中code为0，data为被拉起方退出时的结果码和数据；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000053](../errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000080](../errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |
| [16000018](../errorcode-ability.md#16000018-限制api-11以上版本三方应用跳转) | Redirection to a third-party application is not allowed in API version greater than 11.<br>**适用版本：** 12+ |
| [16000019](../errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found.<br>**适用版本：** 12+ |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000071](../errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000076](../errorcode-ability.md#16000076-指定的app_instance_key不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000077](../errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../errorcode-ability.md#16000079-不支持指定app_instance_key) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000072](../errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000073](../errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

```TypeScript
import { UIAbility, Want, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };

    try {
      // 启动UIAbility并获取返回结果
      this.context.startAbilityForResult(want,
        (err: BusinessError<void> | null, result: common.AbilityResult | undefined) => {
          if (err?.code) {
            // 处理业务逻辑错误
            console.error(`startAbilityForResult failed, code is ${err?.code}, message is ${err?.message}`);
            return;
          }
          // 执行正常业务
          console.info('startAbilityForResult succeed');
        });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startAbilityForResult failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## startAbilityForResult

```TypeScript
startAbilityForResult(want: Want, options: StartOptions, callback: AsyncCallback<AbilityResult>): void
```

启动一个UIAbility，并通过回调函数接收被拉起的UIAbility退出时的返回结果。使用callback异步回调。仅支持在主线程调用。 UIAbility被启动后，有如下情况： - 正常情况下可以通过调用 [terminateSelfWithResult](#terminateselfwithresult) 接口销毁自身，并将结果返回给调用方。 - 异常情况下比如杀死UIAbility会将异常结果返回给调用方，异常结果中resultCode为-1。 - 如果被启动的UIAbility是[单实例模式](../../../application-models/uiability-launch-type.md#singleton启动模式)，且这个UIAbility被不同应用多次调 用该接口启动，当这个UIAbility调用 [terminateSelfWithResult](#terminateselfwithresult) 接口销毁自身时，只将正常结果返回给最后一个调用方，其它调用方返回异常结果，异常结果中resultCode为-1。 > **说明：** > > 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-startAbilityForResult(want: Want, options: StartOptions, callback: AsyncCallback<AbilityResult>): void--><!--Device-UIAbilityContext-startAbilityForResult(want: Want, options: StartOptions, callback: AsyncCallback<AbilityResult>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | 启动Ability的必要信息。 |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | 是 | 启动Ability所携带的参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AbilityResult](arkts-ability-abilityresult-abilityresult-i.md)&gt; | 是 | 回调函数，当接口调用成功，err中code为0，data为被拉起方退出时的结果码和数据；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000053](../errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000080](../errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |
| [16000018](../errorcode-ability.md#16000018-限制api-11以上版本三方应用跳转) | Redirection to a third-party application is not allowed in API version greater than 11.<br>**适用版本：** 12+ |
| [16000019](../errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found.<br>**适用版本：** 12+ |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000071](../errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type.<br>**适用版本：** 9+ |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000076](../errorcode-ability.md#16000076-指定的app_instance_key不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000077](../errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../errorcode-ability.md#16000079-不支持指定app_instance_key) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000072](../errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000073](../errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden.<br>**适用版本：** 9+ |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

```TypeScript
import { UIAbility, Want, common, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let options: StartOptions = {
      displayId: 0
    };

    try {
      // 启动UIAbility并获取返回结果
      this.context.startAbilityForResult(want, options,
        (err: BusinessError<void> | null, result: common.AbilityResult | undefined) => {
          if (err?.code) {
            // 处理业务逻辑错误
            console.error(`startAbilityForResult failed, code is ${err?.code}, message is ${err?.message}`);
            return;
          }
          // 执行正常业务
          console.info('startAbilityForResult succeed');
        });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startAbilityForResult failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## startAbilityForResult

```TypeScript
startAbilityForResult(want: Want, options?: StartOptions): Promise<AbilityResult>
```

启动一个UIAbility，并通过回调函数接收被拉起的UIAbility退出时的返回结果。使用Promise异步回调。仅支持在主线程调用。 UIAbility被启动后，有如下情况： - 正常情况下可以通过调用 [terminateSelfWithResult](#terminateselfwithresult) 接口销毁自身，并将结果返回给调用方。 - 异常情况下比如杀死UIAbility会将异常结果返回给调用方，异常结果中resultCode为-1。 - 如果被启动的UIAbility是[单实例模式](../../../application-models/uiability-launch-type.md#singleton启动模式)，且这个UIAbility被不同应用多次调 用该接口启动，当这个UIAbility调用 [terminateSelfWithResult](#terminateselfwithresult) 接口销毁自身时，只将正常结果返回给最后一个调用方，其它调用方返回异常结果，异常结果中resultCode为-1。 > **说明：** > > 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-startAbilityForResult(want: Want, options?: StartOptions): Promise<AbilityResult>--><!--Device-UIAbilityContext-startAbilityForResult(want: Want, options?: StartOptions): Promise<AbilityResult>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | 启动Ability的必要信息。 |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | 否 | 启动Ability所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AbilityResult](arkts-ability-abilityresult-abilityresult-i.md)&gt; | Promise对象，包含返回给拉起方的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000053](../errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 10+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000080](../errorcode-ability.md#16000080-不支持创建新实例) | Creating a new instance is not supported.<br>**适用版本：** 14+ |
| [16000018](../errorcode-ability.md#16000018-限制api-11以上版本三方应用跳转) | Redirection to a third-party application is not allowed in API version greater than 11.<br>**适用版本：** 12+ |
| [16000019](../errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found.<br>**适用版本：** 12+ |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000071](../errorcode-ability.md#16000071-不支持应用分身模式) | App clone is not supported.<br>**适用版本：** 14+ |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled.<br>**适用版本：** 10+ |
| [16000076](../errorcode-ability.md#16000076-指定的app_instance_key不存在) | The app instance key is invalid.<br>**适用版本：** 14+ |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM.<br>**适用版本：** 10+ |
| [16000077](../errorcode-ability.md#16000077-应用的实例数量已达到上限) | The number of app instances reaches the limit.<br>**适用版本：** 14+ |
| [16000078](../errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000079](../errorcode-ability.md#16000079-不支持指定app_instance_key) | The APP_INSTANCE_KEY cannot be specified.<br>**适用版本：** 14+ |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000072](../errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported.<br>**适用版本：** 14+ |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000073](../errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid.<br>**适用版本：** 12+ |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

```TypeScript
import { UIAbility, Want, common, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let options: StartOptions = {
      displayId: 0
    };

    try {
      // 启动UIAbility并获取返回结果
      this.context.startAbilityForResult(want, options)
        .then((result: common.AbilityResult) => {
          // 执行正常业务
          console.info('startAbilityForResult succeed');
        })
        .catch((err: BusinessError<void>): void => {
          // 处理业务逻辑错误
          console.error(`startAbilityForResult failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startAbilityForResult failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## startAppServiceExtensionAbility

```TypeScript
startAppServiceExtensionAbility(want: Want): Promise<void>
```

启动 [AppServiceExtensionAbility](arkts-ability-app-ability-appserviceextensionability-appserviceextensionability-c.md) 实例。使用Promise异步回调。 该接口仅在PC/2in1设备中可正常调用，在其他设备中返回801错误码。 > **说明：** > > 该接口的调用方必须为 > [AppServiceExtensionAbility](arkts-ability-app-ability-appserviceextensionability-appserviceextensionability-c.md) > 所属应用或者在AppServiceExtensionAbility支持的应用清单（即 > [extensionAbilities标签](../../../quick-start/module-configuration-file.md#extensionabilities标签)的 > appIdentifierAllowList属性）中的应用。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAbilityContext-startAppServiceExtensionAbility(want: Want): Promise<void>--><!--Device-UIAbilityContext-startAppServiceExtensionAbility(want: Want): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | 启动 [AppServiceExtensionAbility](arkts-ability-app-ability-appserviceextensionability-appserviceextensionability-c.md) 的Want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000019](../errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000200](../errorcode-ability.md#16000200-不允许该调用方启动应用后台服务) | The caller is not in the appIdentifierAllowList of the target application. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

```TypeScript
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'AppServiceExtensionAbility'
    };

    try {
      // 启动AppServiceExtensionAbility
      this.context.startAppServiceExtensionAbility(want)
        .then(() => {
          // 执行正常业务
          console.info('startAppServiceExtensionAbility succeed');
        })
        .catch((error: Error) => {
          // 处理业务逻辑错误
          let err = error as BusinessError;
          console.error(`startAppServiceExtensionAbility failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startAppServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## startSelfUIAbilityInCurrentProcess

```TypeScript
startSelfUIAbilityInCurrentProcess(want: Want, specifiedFlag: string, options?: StartOptions): Promise<void>
```

在当前进程中启动应用程序自己的UIAbility。 从API version 23开始，该接口仅在PC/2in1和Tablet设备中可正常调用，在其他设备中返回801错误码。 从API version 22开始，该接口仅在PC/2in1设备中可正常调用，在其他设备中返回801错误码。 > **说明：** > > - 只能冷启动目标UIAbility，如果目标UIAbility实例已经启动过，则启动失败。 > > - 通过该接口启动的UIAbility实例，将运行在调用方所在的进程中。其他关于目标UIAbility的进程相关的策略（例如在 > [module.json5配置文件](../../../quick-start/module-configuration-file.md)中通过isolationProcess或isolationMode字段来指定进程），均 > 不会生效。 > **说明：**> > > -目标UIAability只能是冷启动的。如果目标UIAability的实例已经 > 启动，启动失败。 > > > -通过此API启动的UIAbility实例与调用方在同一进程中运行。其他流程相关 > 目标UIAability的策略（例如通过**隔离进程**或**隔离模式**指定的策略） > [module.json5](../../../quick-start/module-configuration-file.md)文件中的字段不生效。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAbilityContext-startSelfUIAbilityInCurrentProcess(want: Want, specifiedFlag: string, options?: StartOptions): Promise<void>--><!--Device-UIAbilityContext-startSelfUIAbilityInCurrentProcess(want: Want, specifiedFlag: string, options?: StartOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | 启动Ability的必要信息。只支持 [显式启动](../../../application-models/explicit-implicit-want-mappings.md#显式want匹配原理)，不支持 [隐式启动](../../../application-models/explicit-implicit-want-mappings.md#隐式want匹配原理)。 |
| specifiedFlag | string | 是 | UIAbility的ID。此ID不得与任何已运行的ID重复 - 开发者自定义的UIAbility标识。该标识不能与已启动的UIAbility标识相同，否则将返回错误。 <br>**说明：**<br>当通过该接口拉起启动模式为 [specified](../../../application-models/uiability-launch-type.md#specified启动模式)的UIAbility时，将不会触发 [onAcceptWant](arkts-ability-app-ability-abilitystage-abilitystage-c.md#onacceptwant)回调。 |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | 否 | 启动Ability所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000053](../errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Connect to system service failed. |
| [16000130](../errorcode-ability.md#16000130-uiability不属于调用方) | The UIAbility not belong to caller. |
| [16000131](../errorcode-ability.md#16000131-uiability已启动) | The UIAbility is already exist, can not start again. |
| [16000124](../errorcode-ability.md#16000124-不支持启动分布式uiability) | Starting a remote UIAbility is not supported. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000122](../errorcode-ability.md#16000122-待启动的目标组件被系统管控模块拦截) | The target component is blocked by the system module and does not support startup. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000123](../errorcode-ability.md#16000123-不支持隐式启动) | Implicit startup is not supported. |

**示例**

```TypeScript
import { UIAbility, StartOptions, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let accountId = 100;
    let options: StartOptions = {
      displayId: 0
    };
    
    let instanceFlag = 'instance1';

    try {
      // 在当前进程中启动应用程序自己的UIAbility
      this.context.startSelfUIAbilityInCurrentProcess(want, instanceFlag, options);
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startSelfUIAbilityInCurrentProcess failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## startUIServiceExtensionAbility

```TypeScript
startUIServiceExtensionAbility(want: Want): Promise<void>
```

启动一个UIServiceExtensionAbility。使用Promise异步回调。 该接口仅在PC/2in1设备中可正常调用，在其他设备中返回801错误码。 > **说明：** > > 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-startUIServiceExtensionAbility(want: Want): Promise<void>--><!--Device-UIAbilityContext-startUIServiceExtensionAbility(want: Want): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | 启动UIServiceExtensionAbility的必要信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，包含接口执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000019](../errorcode-ability.md#16000019-隐式启动未查找到匹配ability) | No matching ability is found. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    Column() {
      Row() {
        // 创建启动按钮
        Button('start ability')
          .enabled(true)
          .onClick(() => {
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
            let startWant: Want = {
              bundleName: 'com.acts.uiserviceextensionability',
              abilityName: 'UiServiceExtAbility',
            };
            try {
              // 启动UIServiceExtensionAbility
              context.startUIServiceExtensionAbility(startWant).then(() => {
                console.info('startUIServiceExtensionAbility success');
              }).catch((error: BusinessError) => {
                console.info('startUIServiceExtensionAbility error', JSON.stringify(error));
              })
            } catch (err) {
              console.info('startUIServiceExtensionAbility failed', JSON.stringify(err));
            }
          })
      }
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Entry, Column, Row, Button, Component } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column() {
      Row() {
        // 创建启动按钮
        Button('start ability')
          .enabled(true)
          .onClick(() => {
            this.clickFun();
          })
      }
    }
  }

  private clickFun() {
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    let startWant: Want = {
      bundleName: 'com.acts.uiserviceextensionability',
      abilityName: 'UiServiceExtAbility',
    };
    try {
      // 启动UIServiceExtensionAbility
      context.startUIServiceExtensionAbility(startWant).then(() => {
        console.info('startUIServiceExtensionAbility success');
      }).catch((err) => {
        let error = err as BusinessError;
        console.info('startUIServiceExtensionAbility error', JSON.stringify(error));
      })
    } catch (err) {
      console.info('startUIServiceExtensionAbility failed', JSON.stringify(err));
    }
  }
}
```

## stopAppServiceExtensionAbility

```TypeScript
stopAppServiceExtensionAbility(want: Want): Promise<void>
```

停止 [AppServiceExtensionAbility](arkts-ability-app-ability-appserviceextensionability-appserviceextensionability-c.md) 实例。使用Promise异步回调。 该接口仅在PC/2in1设备中可正常调用，在其他设备中返回801错误码。 > **说明：** > > 该接口的调用方必须为 > [AppServiceExtensionAbility](arkts-ability-app-ability-appserviceextensionability-appserviceextensionability-c.md) > 所属应用或者在AppServiceExtensionAbility支持的应用清单（即 > [extensionAbilities标签](../../../quick-start/module-configuration-file.md#extensionabilities标签)的 > appIdentifierAllowList属性）中的应用。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIAbilityContext-stopAppServiceExtensionAbility(want: Want): Promise<void>--><!--Device-UIAbilityContext-stopAppServiceExtensionAbility(want: Want): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | 停止 [AppServiceExtensionAbility](arkts-ability-app-ability-appserviceextensionability-appserviceextensionability-c.md) 的Want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000200](../errorcode-ability.md#16000200-不允许该调用方启动应用后台服务) | The caller is not in the appIdentifierAllowList of the target application. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

```TypeScript
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'AppServiceExtensionAbility'
    };

    try {
      // 停止AppServiceExtensionAbility
      this.context.stopAppServiceExtensionAbility(want)
        .then(() => {
          // 执行正常业务
          console.info('stopAppServiceExtensionAbility succeed');
        })
        .catch((error: Error) => {
          // 处理业务逻辑错误
          let err = error as BusinessError;
          console.error(`stopAppServiceExtensionAbility failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`stopAppServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## terminateSelf

```TypeScript
terminateSelf(callback: AsyncCallback<void>): void
```

销毁UIAbility自身。使用callback异步回调。仅支持在主线程调用。 > **说明：** > > 调用该接口后，任务中心的任务默认不会清理，如需清理，需要配置 > [removeMissionAfterTerminate](../../../quick-start/module-configuration-file.md#abilities标签)为true。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-terminateSelf(callback: AsyncCallback<void>): void--><!--Device-UIAbilityContext-terminateSelf(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，当销毁UIAbility自身成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 9+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission.<br>**适用版本：** 9+ |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist.<br>**适用版本：** 9+ |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

使用terminateSelf接口停止UIAbility示例代码如下，默认情况下应用会在最近任务列表中保留快照。

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    try {
      // 销毁UIAbility自身
      this.context.terminateSelf((err: BusinessError<void> | null) => {
        if (err?.code) {
          // 处理业务逻辑错误
          console.error(`terminateSelf failed, code is ${err?.code}, message is ${err?.message}`);
          return;
        }
        // 执行正常业务
        console.info('terminateSelf succeed');
      });
    } catch (err) {
      // 捕获同步的参数错误
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`terminateSelf failed, code is ${code}, message is ${message}`);
    }
  }
}
```

（可选）如果需要在停止UIAbility时，清理任务中心的相关任务（即不保留最近任务列表中的快照），需要在[module.json5](../../../quick-start/module-configuration-file.md)配置文件中将removeMissionAfterTerminate字段取值配置为true。

```TypeScript
{
  "module": {
    // ...
    "abilities": [
      {
        // ...
        "removeMissionAfterTerminate": true
      }
    ]
  }
}
```

## terminateSelf

```TypeScript
terminateSelf(): Promise<void>
```

销毁UIAbility自身。使用Promise异步回调。仅支持在主线程调用。 > **说明：** > > 调用该接口后，任务中心的任务默认不会清理，如需清理，需要配置 > [removeMissionAfterTerminate](../../../quick-start/module-configuration-file.md#abilities标签)为true。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-terminateSelf(): Promise<void>--><!--Device-UIAbilityContext-terminateSelf(): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 9+ |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission.<br>**适用版本：** 9+ |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist.<br>**适用版本：** 9+ |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

使用terminateSelf接口停止UIAbility示例代码如下，默认情况下应用会在最近任务列表中保留快照。

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    try {
      // 销毁UIAbility自身
      this.context.terminateSelf()
        .then(() => {
          // 执行正常业务
          console.info('terminateSelf succeed');
        })
        .catch((err: BusinessError<void>): void => {
          // 处理业务逻辑错误
          console.error(`terminateSelf failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // 捕获同步的参数错误
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`terminateSelf failed, code is ${code}, message is ${message}`);
    }
  }
}
```

（可选）如果需要在停止UIAbility时，清理任务中心的相关任务（即不保留最近任务列表中的快照），需要在[module.json5](../../../quick-start/module-configuration-file.md)配置文件中将removeMissionAfterTerminate字段取值配置为true。

```TypeScript
{
  "module": {
    // ...
    "abilities": [
      {
        // ...
        "removeMissionAfterTerminate": true
      }
    ]
  }
}
```

## terminateSelfWithResult

```TypeScript
terminateSelfWithResult(parameter: AbilityResult, callback: AsyncCallback<void>): void
```

销毁UIAbility自身。使用callback异步回调。仅支持在主线程调用。 仅当UIAbility通过 [startAbilityForResult](#startabilityforresult) 接口拉起时，调用terminateSelfWithResult接口销毁UIAbility，才会返回结果给调用方。 > **说明：** > > 调用该接口后，任务中心的任务默认不会清理，如需清理，需要配置 > [removeMissionAfterTerminate](../../../quick-start/module-configuration-file.md#abilities标签)为true。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-terminateSelfWithResult(parameter: AbilityResult, callback: AsyncCallback<void>): void--><!--Device-UIAbilityContext-terminateSelfWithResult(parameter: AbilityResult, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | [AbilityResult](arkts-ability-abilityresult-abilityresult-i.md) | 是 | 返回给startAbilityForResult?接口调用方的相关信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，当销毁UIAbility自身成功，err中code为0；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 9+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission.<br>**适用版本：** 9+ |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist.<br>**适用版本：** 9+ |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

```TypeScript
import { UIAbility, Want, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let resultCode = 100;
    // 返回给接口调用方AbilityResult信息
    let abilityResult: common.AbilityResult = {
      want,
      resultCode
    };

    try {
      // 销毁UIAbility自身
      this.context.terminateSelfWithResult(abilityResult, (err: BusinessError | null) => {
        if (err?.code) {
          // 处理业务逻辑错误
          console.error(`terminateSelfWithResult failed, code is ${err?.code}, message is ${err?.message}`);
          return;
        }
        // 执行正常业务
        console.info('terminateSelfWithResult succeed');
      });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`terminateSelfWithResult failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## terminateSelfWithResult

```TypeScript
terminateSelfWithResult(parameter: AbilityResult): Promise<void>
```

销毁UIAbility自身。使用Promise异步回调。仅支持在主线程调用。 仅当UIAbility通过 [startAbilityForResult](#startabilityforresult) 接口拉起时，调用terminateSelfWithResult接口销毁UIAbility，才会返回结果给调用方。 > **说明：** > > 调用该接口后，任务中心的任务默认不会清理，如需清理，需要配置 > [removeMissionAfterTerminate](../../../quick-start/module-configuration-file.md#abilities标签)为true。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-terminateSelfWithResult(parameter: AbilityResult): Promise<void>--><!--Device-UIAbilityContext-terminateSelfWithResult(parameter: AbilityResult): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | [AbilityResult](arkts-ability-abilityresult-abilityresult-i.md) | 是 | 返回给startAbilityForResult?接口调用方的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 9+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission.<br>**适用版本：** 9+ |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist.<br>**适用版本：** 9+ |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

```TypeScript
import { UIAbility, Want, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let want: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let resultCode = 100;
    // 返回给接口调用方AbilityResult信息
    let abilityResult: common.AbilityResult = {
      want,
      resultCode
    };

    try {
      // 销毁UIAbility自身
      this.context.terminateSelfWithResult(abilityResult)
        .then(() => {
          // 执行正常业务
          console.info('terminateSelfWithResult succeed');
        })
        .catch((err: BusinessError<void>): void => {
          // 处理业务逻辑错误
          console.error(`terminateSelfWithResult failed, code is ${err.code}, message is ${err.message}`);
        });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`terminateSelfWithResult failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## abilityInfo

```TypeScript
abilityInfo: AbilityInfo
```

UIAbility的相关信息。

**类型：** [AbilityInfo](arkts-ability-abilityinfo-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-abilityInfo: AbilityInfo--><!--Device-UIAbilityContext-abilityInfo: AbilityInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## config

```TypeScript
config: Configuration
```

应用运行时的环境变量，如语言、颜色模式等。

**类型：** [Configuration](arkts-ability-app-ability-configuration-configuration-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-config: Configuration--><!--Device-UIAbilityContext-config: Configuration-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## currentHapModuleInfo

```TypeScript
currentHapModuleInfo: HapModuleInfo
```

当前UIAbility所属HAP的信息。

**类型：** [HapModuleInfo](arkts-ability-hapmoduleinfo-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-currentHapModuleInfo: HapModuleInfo--><!--Device-UIAbilityContext-currentHapModuleInfo: HapModuleInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## windowStage

```TypeScript
windowStage: window.WindowStage
```

当前WindowStage对象。仅支持在主线程调用。

**类型：** window.WindowStage

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-UIAbilityContext-windowStage: window.WindowStage--><!--Device-UIAbilityContext-windowStage: window.WindowStage-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

