# UIServiceExtensionConnectCallback

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @xhz-sz-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

UIServiceExtensionConnectCallback是UIServiceExtension连接回调接口类，提供UIServiceExtension连接回调数据能力。


> **说明：**
>
>  - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>  - 本模块首批接口从API version 14开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>  - 本模块接口仅可在Stage模型下使用。
>  - 本模块接口需要在主线程中使用，不要在Worker、TaskPool等子线程中使用。

## 导入模块

```ts
import { common } from '@kit.AbilityKit';
```

## UIServiceExtensionConnectCallback.onData

 onData(data: Record&lt;string, Object&gt;): void

接收UIServiceExtension连接的回调数据。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../application-models/component-startup-rules.md)。
>

**原子化服务API（仅ArkTS-Dyn）**：从 API version 14开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 14

**参数：**

| 参数名 | 类型                   | 必填 | 说明         |
| ------ | ---------------------- | ---- | ------------ |
| data   | Record&lt;string, Object&gt; | 是 | 接收UIServiceExtension连接回调数据。 |

**示例：**

```ts
import { common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const TAG: string = '[Extension] ';

@Entry
@Component
struct UIServiceExtensionAbility {
  comProxy: common.UIServiceProxy | null = null;
  dataCallBack: common.UIServiceExtensionConnectCallback = {
    onData: (data: Record<string, Object>) => {
      console.info(`${TAG} dataCallBack received data: ${JSON.stringify(data)}.`);
    },
    onDisconnect: () => {
      console.info(`${TAG} dataCallBack onDisconnect.`);
      this.comProxy = null;
    }
  }

  build() {
    Scroll() {
      Column() {
        // 创建一个按钮，点击按钮后连接UIServiceExtensionAbility
        Button('connectUIServiceExtensionAbility', { type: ButtonType.Capsule, stateEffect: true })
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
            this.myConnectUIServiceExtensionAbility()
          });
      }
      .width('100%')
    }
    .height('100%')
  }

  myConnectUIServiceExtensionAbility() {
    // 获取上下文
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    let startWant: Want = {
      deviceId: '',
      bundleName: 'com.acts.myapplication',
      abilityName: 'UiServiceExtensionAbility'
    };

    try {
      // 连接到UIServiceExtensionAbility
      context.connectUIServiceExtensionAbility(startWant, this.dataCallBack)
        .then((proxy: common.UIServiceProxy) => {
          console.info(TAG + `try to connectUIServiceExtensionAbility ${proxy}`);
          this.comProxy = proxy;
          let formData: Record<string, string> = {
            'PATH': '/tmp/aaa.jpg'
          };
          try {
            console.info(`${TAG} sendData.`);
            this.comProxy.sendData(formData);
          } catch (err) {
            let code = (err as BusinessError).code;
            let message = (err as BusinessError).message;
            console.error(`${TAG} sendData failed, code is ${code}, message is ${message}.`);
          }
        }).catch((err: Error) => {
        let code = (err as BusinessError).code;
        let message = (err as BusinessError).message;
        console.error(`${TAG} connectUIServiceExtensionAbility failed, code is ${code}, message is ${message}.`);
      });
    } catch (err) {
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`${TAG} connectUIServiceExtensionAbility failed, code is ${code}, message is ${message}.`);
    }
  }
}
```

## UIServiceExtensionConnectCallback.onData<sup>23+</sup>

 onData(data: Record&lt;string, RecordData&gt;): void

接收UIServiceExtension连接的回调数据。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../application-models/component-startup-rules.md)。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                             | 必填 | 说明                                 |
| ------ | -------------------------------- | ---- | ------------------------------------ |
| data   | Record&lt;string, RecordData&gt; | 是   | 接收UIServiceExtension连接回调数据。 |

**示例：**

ArkTS-Sta示例：

```ts
'use static'
import { common, Want } from '@kit.AbilityKit';
import { BusinessError, RecordData } from '@kit.BasicServicesKit';
import { Entry, Component, Scroll, Column, Button, ButtonType } from '@kit.ArkUI';

const TAG: string = '[Extension] ';

class MyDataCallBack implements common.UIServiceExtensionConnectCallback {
  onData(data: Record<string, RecordData>) {
    console.info(`dataCallBack received data`, JSON.stringify(data));
  }

  onDisconnect() {
    console.info(`dataCallBack onDisconnect`);
  }
}

@Entry
@Component
struct UIServiceExtensionAbility {
  comProxy: common.UIServiceProxy | null = null;

  build() {
    Scroll() {
      Column() {
        // 创建一个按钮，点击按钮后连接UIServiceExtensionAbility
        Button('connectUIServiceExtensionAbility', { type: ButtonType.Capsule, stateEffect: true })
          .margin({
            top: 5,
            left: 10,
            right: 10,
            bottom: 5
          })
          .onClick(() => {
            this.myConnectUIServiceExtensionAbility()
          });
      }
      .width('100%')
    }
    .height('100%')
  }

  myConnectUIServiceExtensionAbility() {
    // 获取上下文
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    let startWant: Want = {
      deviceId: '',
      bundleName: 'com.acts.myapplication',
      abilityName: 'UiServiceExtensionAbility'
    };

    try {
      let dataCallBack = new MyDataCallBack();
      // 连接到UIServiceExtensionAbility
      context.connectUIServiceExtensionAbility(startWant, dataCallBack)
        .then((proxy: common.UIServiceProxy) => {
          console.info(TAG + `try to connectUIServiceExtensionAbility ${proxy}}`);
          this.comProxy = proxy;
          let formData: Record<string, RecordData> = {
            'PATH': '/tmp/aaa.jpg'
          };
          try {
            console.info(`${TAG} sendData.`);
            this.comProxy?.sendData(formData);
          } catch (err) {
            let code = (err as BusinessError).code;
            let message = (err as BusinessError).message;
            console.error(`${TAG} sendData failed, code is ${code}, message is ${message}.`);
          }
        }).catch((err: Error) => {
        let code = (err as BusinessError).code;
        let message = (err as BusinessError).message;
        console.error(`${TAG} connectUIServiceExtensionAbility failed, code is ${code}, message is ${message}.`);
      });
    } catch (err) {
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`${TAG} connectUIServiceExtensionAbility failed, code is ${code}, message is ${message}.`);
    }
  }
}
```

## UIServiceExtensionConnectCallback.onDisconnect

onDisconnect(): void

成功断开UIServiceExtension连接的回调。

> **说明：**
>
> 组件启动规则详见：[组件启动规则（Stage模型）](../../application-models/component-startup-rules.md)。
>

**原子化服务API（仅ArkTS-Dyn）**：从 API version 14开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 14

**ArkTS-Sta起始版本：** 23

**示例：**

ArkTS-Dyn示例：

```ts
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const TAG: string = '[Extension] ';

@Entry
@Component
struct UIServiceExtensionAbility {
  comProxy: common.UIServiceProxy | null = null;
  // 连接时的回调接口
  dataCallBack: common.UIServiceExtensionConnectCallback = {
    onData: (data: Record<string, Object>) => {
      console.info(`${TAG} dataCallBack received data: ${JSON.stringify(data)}.`);
    },
    onDisconnect: () => {
      // 连接断链后的触发
      console.info(`${TAG} dataCallBack onDisconnect.`);
      this.comProxy = null;
    }
  }

  build() {
    Scroll() {
      Column() {
        // 创建一个按钮，点击后断开已连接的UIServiceExtensionAbility
        Button('disConnectUIServiceExtensionAbility', { type: ButtonType.Capsule, stateEffect: true })
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
            this.myConnectUIServiceExtensionAbility()
          });
      }
      .width('100%')
    }
    .height('100%')
  }

  myConnectUIServiceExtensionAbility() {
    // 获取上下文
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    // 断开连接的UIServiceExtensionAbility
    try {
      // this.comProxy在连接成功后保存
      context.disconnectUIServiceExtensionAbility(this.comProxy).then(() => {
        console.info(`${TAG} disconnectUIServiceExtensionAbility success.`);
      }).catch((err: Error) => {
        let code = (err as BusinessError).code;
        let message = (err as BusinessError).message;
        console.error(`${TAG} disconnectUIServiceExtensionAbility failed, code is ${code}, message is ${message}.`);
      });
    } catch (err) {
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`${TAG} disconnectUIServiceExtensionAbility failed, code is ${code}, message is ${message}.`);
    }
  }
}
```

ArkTS-Sta示例：

```ts
'use static'
import { common } from '@kit.AbilityKit';
import { BusinessError, RecordData } from '@kit.BasicServicesKit';
import { Entry, Component, Scroll, Column, Button, ButtonType } from '@kit.ArkUI';

const TAG: string = '[Extension] ';

@Entry
@Component
struct UIServiceExtensionAbility {
  comProxy: common.UIServiceProxy | null = null;

  build() {
    Scroll() {
      Column() {
        // 创建一个按钮，点击后断开已连接的UIServiceExtensionAbility
        Button('disConnectUIServiceExtensionAbility', { type: ButtonType.Capsule, stateEffect: true })
          .margin({
            top: 5,
            left: 10,
            right: 10,
            bottom: 5
          })
          .onClick(() => {
            this.myConnectUIServiceExtensionAbility()
          });
      }
      .width('100%')
    }
    .height('100%')
  }

  myConnectUIServiceExtensionAbility() {
    if (!this.comProxy) {
      console.warn(`${TAG} No proxy to disconnect`);
      return;
    }
    // 获取上下文
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    // 断开连接的UIServiceExtensionAbility
    try {
      // this.comProxy在连接成功后保存
      const proxy = this.comProxy as common.UIServiceProxy;
      context.disconnectUIServiceExtensionAbility(proxy).then(() => {
        console.info(`${TAG} disconnectUIServiceExtensionAbility success.`);
      }).catch((err: Error) => {
        let code = (err as BusinessError).code;
        let message = (err as BusinessError).message;
        console.error(`${TAG} disconnectUIServiceExtensionAbility failed, code is ${code}, message is ${message}.`);
      });
    } catch (err) {
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`${TAG} disconnectUIServiceExtensionAbility failed, code is ${code}, message is ${message}.`);
    }
  }
}
```
