# AgentExtensionConnectCallback (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

You can use the callback APIs provided by AgentExtensionConnectCallback to receive data and security authentication requests from the server and detect the disconnection operation of the AgentExtensionAbility server.

> **NOTE**
>
>  - The initial APIs of this module are supported since API version 24. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>  - The APIs provided by this module are system APIs.
>  - The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { common } from '@kit.AbilityKit';
```

## AgentExtensionConnectCallback

### onData

onData(data: string): void

Defines the callback API for receiving data from the AgentExtensionAbility server.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**System API**: This is a system API.

**Parameters:**

| Name| Type  | Mandatory| Description          |
| ------ | ------ | ---- | ------------ |
| data   | string | Yes  | Data received from the AgentExtensionAbility server.|

**Example:**

```ts
import { common, Want, agentManager} from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const TAG: string = '[Extension] ';

@Entry
@Component
struct AgentExtensionAbility {
  comProxy: common.AgentProxy | null = null;
  dataCallBack: common.AgentExtensionConnectCallback = {
    onData: (data: string) => {
      console.info(`${TAG} dataCallBack received data: ${data}.`);
    },
    onAuth: (handShakeData: string): void => {
      console.info(`onData, data: ${handShakeData}.`);
    },
    onDisconnect: () => {
      console.info(`${TAG} dataCallBack onDisconnect.`);
      this.comProxy = null;
    }
  }

  build() {
    Scroll() {
      Column() {
        // Create a button for connecting to AgentExtension.
        Button('connectAgentExtensionAbility', { type: ButtonType.Capsule, stateEffect: true })
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
            this.myConnectAgentExtensionAbility()
          });
      }
      .width('100%')
    }
    .height('100%')
  }

  // Customize a function for connecting to AgentExtension.
  myConnectAgentExtensionAbility() {
    let startWant: Want = {
      deviceId: '',
      bundleName: 'com.acts.myapplication',
      abilityName: 'AgentExtensionAbility'
    };

    try {
      let agentId: string = 'test';
      // Connect to AgentExtension.
      agentManager.connectAgentExtensionAbility(startWant, agentId, this.dataCallBack)
        .then((proxy: common.AgentProxy) => {
          console.info(TAG + `try to connectAgentExtensionAbility ${proxy}}`);
          this.comProxy = proxy;
        }).catch((err: Error) => {
        let code = (err as BusinessError).code;
        let message = (err as BusinessError).message;
        console.error(`${TAG} connectAgentExtensionAbility failed, code is ${code}, message is ${message}.`);
      });
    } catch (err) {
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`${TAG} connectAgentExtensionAbility failed, code is ${code}, message is ${message}.`);
    }
  }
}
```

### onAuth

onAuth(handshakeData: string): void

Defines the callback API for receiving security authentication from the AgentExtensionAbility server.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**System API**: This is a system API.

**Parameters:**

| Name        | Type  | Mandatory| Description          |
| -------------- | ------ | ---- | ------------ |
| handshakeData | string | Yes  | Security authentication data received from the AgentExtensionAbility server.|

**Example:**

```ts
import { common, Want, agentManager} from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const TAG: string = '[Extension] ';

@Entry
@Component
struct AgentExtensionAbility {
  comProxy: common.AgentProxy | null = null;
  dataCallBack: common.AgentExtensionConnectCallback = {
    onData: (data: string) => {
      console.info(`${TAG} dataCallBack received data: ${data}.`);
    },
    onAuth: (handShakeData: string): void => {
      console.info(`onAuth, handshakeData: ${handShakeData}.`);
    },
    onDisconnect: () => {
      console.info(`${TAG} dataCallBack onDisconnect.`);
      this.comProxy = null;
    }
  }

  build() {
    Scroll() {
      Column() {
        // Create a button for connecting to AgentExtension.
        Button('connectAgentExtensionAbility', { type: ButtonType.Capsule, stateEffect: true })
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
            this.myConnectAgentExtensionAbility()
          });
      }
      .width('100%')
    }
    .height('100%')
  }

  // Customize a function for connecting to AgentExtension.
  myConnectAgentExtensionAbility() {
    let startWant: Want = {
      deviceId: '',
      bundleName: 'com.acts.myapplication',
      abilityName: 'AgentExtensionAbility'
    };

    try {
      let agentId: string = 'test';
      // Connect to AgentExtension.
      agentManager.connectAgentExtensionAbility(startWant, agentId, this.dataCallBack)
        .then((proxy: common.AgentProxy) => {
          console.info(TAG + `try to connectAgentExtensionAbility ${proxy}}`);
          this.comProxy = proxy;
        }).catch((err: Error) => {
        let code = (err as BusinessError).code;
        let message = (err as BusinessError).message;
        console.error(`${TAG} connectAgentExtensionAbility failed, code is ${code}, message is ${message}.`);
      });
    } catch (err) {
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`${TAG} connectAgentExtensionAbility failed, code is ${code}, message is ${message}.`);
    }
  }
}
```

### onDisconnect

onDisconnect(): void

Defines the callback API triggered when disconnecting from the AgentExtensionAbility server.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**System API**: This is a system API.

**Example:**

```ts
import { common, Want, agentManager} from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const TAG: string = '[Extension] ';

@Entry
@Component
struct AgentExtensionAbility {
  comProxy: common.AgentProxy | null = null;
  dataCallBack: common.AgentExtensionConnectCallback = {
    onData: (data: string) => {
      console.info(`${TAG} dataCallBack received data: ${data}.`);
    },
    onAuth: (handShakeData: string): void => {
      console.info(`onAuth, handshakeData: ${handShakeData}.`);
    },
    onDisconnect: () => {
      console.info(`${TAG} dataCallBack onDisconnect.`);
      this.comProxy = null;
    }
  }

  build() {
    Scroll() {
      Column() {
        // Create a button for connecting to AgentExtension.
        Button('connectAgentExtensionAbility', { type: ButtonType.Capsule, stateEffect: true })
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
            this.myConnectAgentExtensionAbility()
          });
      }
      .width('100%')
    }
    .height('100%')
  }

  // Customize a function for connecting to AgentExtension.
  myConnectAgentExtensionAbility() {
    let startWant: Want = {
      deviceId: '',
      bundleName: 'com.acts.myapplication',
      abilityName: 'AgentExtensionAbility'
    };

    try {
      let agentId: string = 'test';
      // Connect to AgentExtension.
      agentManager.connectAgentExtensionAbility(startWant, agentId, this.dataCallBack)
        .then((proxy: common.AgentProxy) => {
          console.info(TAG + `try to connectAgentExtensionAbility ${proxy}}`);
          this.comProxy = proxy;
        }).catch((err: Error) => {
        let code = (err as BusinessError).code;
        let message = (err as BusinessError).message;
        console.error(`${TAG} connectAgentExtensionAbility failed, code is ${code}, message is ${message}.`);
      });
    } catch (err) {
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`${TAG} connectAgentExtensionAbility failed, code is ${code}, message is ${message}.`);
    }
  }
}
```
