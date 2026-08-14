# UIServiceProxy

UIServiceProxy提供代理能力，可以从UIServiceExtension客户端发送数据到服务端。 > **说明：** > > - 本模块接口需要在主线程中使用，不要在Worker、TaskPool等子线程中使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export default interface UIServiceProxy--><!--Device-unnamed-export default interface UIServiceProxy-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## sendData

```TypeScript
sendData(data: Record<string, Object>): void
```

给UIServiceExtension服务端发送数据。 > **说明：** > > 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-UIServiceProxy-sendData(data: Record<string, Object>): void--><!--Device-UIServiceProxy-sendData(data: Record<string, Object>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | 是 | 待发送给UIServiceExtension服务端的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## 示例

```TypeScript
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
        // 创建一个连接UIServiceExtension的按钮
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

  // 自定义连接UIServiceExtension的函数
  myConnectUIServiceExtensionAbility() {
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    let startWant: Want = {
      deviceId: '',
      bundleName: 'com.acts.myapplication',
      abilityName: 'UiServiceExtensionAbility'
    };

    try {
      // 连接UIServiceExtension
      context.connectUIServiceExtensionAbility(startWant, this.dataCallBack)
        .then((proxy: common.UIServiceProxy) => {
          console.info(TAG + `try to connectUIServiceExtensionAbility ${proxy}}`);
          this.comProxy = proxy;
          let formData: Record<string, string> = {
            'PATH': '/tmp/aaa.jpg'
          };
          try {
            console.info(`${TAG} sendData.`);
            // 给UIServiceExtension发送数据
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

## sendData

```TypeScript
sendData(data: Record<string, RecordData>): void
```

给UIServiceExtension服务端发送数据。 > **说明：** > > 组件启动规则详见：[组件启动规则（Stage模型）](../../../application-models/component-startup-rules.md)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIServiceProxy-sendData(data: Record<string, RecordData>): void--><!--Device-UIServiceProxy-sendData(data: Record<string, RecordData>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, [RecordData](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-recorddata-t.md)&gt; | 是 | 待发送给UIServiceExtension服务端的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible cause: Connect to stub failed. |

## 示例

ArkTS-Sta示例：

```TypeScript
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
        // 创建一个连接UIServiceExtension的按钮
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

  // 自定义连接UIServiceExtension的函数
  myConnectUIServiceExtensionAbility() {
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    let startWant: Want = {
      deviceId: '',
      bundleName: 'com.acts.myapplication',
      abilityName: 'UiServiceExtensionAbility'
    };

    try {
      let dataCallBack = new MyDataCallBack();
      // 连接UIServiceExtension
      context.connectUIServiceExtensionAbility(startWant, dataCallBack)
        .then((proxy: common.UIServiceProxy) => {
          console.info(TAG + `try to connectUIServiceExtensionAbility ${proxy}}`);
          this.comProxy = proxy;
          let formData: Record<string, RecordData> = {
            'PATH': '/tmp/aaa.jpg'
          };
          try {
            console.info(`${TAG} sendData.`);
            // 给UIServiceExtension发送数据
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

