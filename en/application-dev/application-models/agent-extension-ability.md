# Using AgentExtensionAbility for Agent Services

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

## Overview

Starting from API version 24, you can use the [AgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md) component to provide agent services. System applications can connect to the [AgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md) component implemented by other applications and use the corresponding agent services.

> **NOTE**
>
> In this document, the connected [AgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md) is referred to as the server, and the component that connects to the [AgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md) is referred to as the client.

## Implementing the AgentExtensionAbility Component

To manually create a [AgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md) in a DevEco Studio project, perform the following steps:

1. In the **ets** directory of the project module, right-click and choose **New > Directory** to create a directory named **agentextability**.

2. In the **AgentExtAbility** directory, right-click and choose **New > ArkTS File** to create a file named **AgentExtAbility.ets**.

    ``` txt
    ├── ets
    │ ├── agentextability
    │ │   ├── AgentExtAbility.ets
    ```

3. In the AgentExtAbility.ets file, add the import module of [AgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md). The custom class AgentExtAbility inherits [AgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md) and implements lifecycle callbacks.

    <!-- @[ability_agent_service_one](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/AgentExtensionAbility/entry/src/main/ets/AgentExtAbility/AgentExtAbility.ets) -->
    
    ``` TypeScript
    import { common, AgentExtensionAbility, Want } from '@kit.AbilityKit';
    import { hilog } from '@kit.PerformanceAnalysisKit';
    
    export default class AgentExtAbility extends AgentExtensionAbility {
      private comProxy: common.AgentHostProxy | null = null;
      // Create an AgentExtensionAbility.
      onCreate(want: Want) {
        hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
      }
    
      // Connect.
      onConnect(want: Want, proxy: common.AgentHostProxy) {
        hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onConnect');
        this.comProxy = proxy;
      }
    
      // Disconnect.
      onDisconnect(want: Want, proxy: common.AgentHostProxy) {
        hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onDisconnect');
        this.comProxy = null;
      }
      // Receive data.
      onData(proxy: common.AgentHostProxy, data: string) {
        hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onData');
        try {
          let replyData = 'reply message';
          proxy.sendData(replyData);
        } catch (err) {
          let code = (err as BusinessError).code;
          let msg = (err as BusinessError).message;
          console.error(`sendData failed, err code: ${code}, err msg: ${msg}.`);
        }
      }
      // Authenticate.
      onAuth(proxy: common.AgentHostProxy, handshakeData: string) {
        hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onAuth');
        try {
          // Process the authentication logic.
          let authResult = 'auth success';
          proxy.authorize(authResult);
        } catch (err) {
          let code = (err as BusinessError).code;
          let msg = (err as BusinessError).message;
          console.error(`sendData failed, err code: ${code}, err msg: ${msg}.`);
        }
      }
      // Destroy.
      onDestroy() {
        hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onDestroy');
      }
    }
    ```


4. Register AgentExtensionAbility in the [module.json5 Configuration File](../quick-start/module-configuration-file.md) of the project module. Set **type** to **agent** and **srcEntry** to the code path of the current ExtensionAbility component.

    ```json
    {
      "module": {
        "extensionAbilities": [
          {
            "name": "AgentExtAbility",
            "icon": "$media:icon",
            "description": "agent",
            "type": "agent",
            "exported": true,
            "srcEntry": "./ets/agentextability/AgentExtAbility.ets",
            "metadata": [
              {
                "name": "ohos.extension.agent",
                "resource": "$profile:agent_config",
              }
            ]
          }
        ]
      }
    }
    ```

5. Create the agent_config.json file in the `resources/base/profile/` directory of the project module and configure [AgentCard](../reference/apis-ability-kit/js-apis-inner-application-AgentCard.md) information in the file. For details, see [Agent Configuration File](./agent-extension-configuration.md).

## Using AgentExtensionAbility to Send and Receive Data

Your application can receive the data and [AgentHostProxy](../reference/apis-ability-kit/js-apis-inner-application-agentHostProxy.md) object from the client in the [onData()](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md#ondata) method of the AgentExtensionAbility component on the server, and send the data to the client by calling the [sendData()](../reference/apis-ability-kit/js-apis-inner-application-agentHostProxy.md#senddata) method of the [AgentHostProxy](../reference/apis-ability-kit/js-apis-inner-application-agentHostProxy.md) object.

<!-- @[ability_agent_service_two](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/AgentExtensionAbility/entry/src/main/ets/AgentExtAbility/AgentExtAbility.ets) -->

``` TypeScript
import { common, AgentExtensionAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class AgentExtAbility extends AgentExtensionAbility {
  // ...
  // Receive data.
  onData(proxy: common.AgentHostProxy, data: string) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onData');
    try {
      let replyData = 'reply message';
      proxy.sendData(replyData);
    } catch (err) {
      let code = (err as BusinessError).code;
      let msg = (err as BusinessError).message;
      console.error(`sendData failed, err code: ${code}, err msg: ${msg}.`);
    }
  }
  // ...
}
```

## Using AgentExtensionAbility to Receive and Send Security Authentication Requests

Your application can receive the security authentication request and [AgentHostProxy](../reference/apis-ability-kit/js-apis-inner-application-agentHostProxy.md) object from the client in the [onAuth()](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md#onauth) method of the AgentExtensionAbility component on the server, and send the security authentication request to the client using the [authorize()](../reference/apis-ability-kit/js-apis-inner-application-agentHostProxy.md#authorize) method of [AgentHostProxy](../reference/apis-ability-kit/js-apis-inner-application-agentHostProxy.md).

<!-- @[ability_agent_service_three](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/AgentExtensionAbility/entry/src/main/ets/AgentExtAbility/AgentExtAbility.ets) -->

``` TypeScript
import { common, AgentExtensionAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class AgentExtAbility extends AgentExtensionAbility {
  // ...
  // Authenticate.
  onAuth(proxy: common.AgentHostProxy, handshakeData: string) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onAuth');
    try {
      // Process the authentication logic.
      let authResult = 'auth success';
      proxy.authorize(authResult);
    } catch (err) {
      let code = (err as BusinessError).code;
      let msg = (err as BusinessError).message;
      console.error(`sendData failed, err code: ${code}, err msg: ${msg}.`);
    }
  }
  // ...
}
```
