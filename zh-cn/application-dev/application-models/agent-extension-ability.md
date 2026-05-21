# 使用AgentExtensionAbility组件实现智能体服务

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

## 概述

从API version 24开始，支持开发者使用[AgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md)类型的组件提供智能体服务。系统应用可以连接其他应用实现的[AgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md)组件，并使用相应的智能体服务。

> **说明**
>
> 本文描述中称被连接的[AgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md)为服务端，称连接[AgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md)的组件为客户端。

## 实现AgentExtensionAbility组件

在DevEco Studio工程中手动新建一个[AgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md)，具体步骤如下：

1. 在工程Module对应的ets目录下，右键选择"New > Directory"，新建一个目录并命名为agentextability。

2. 在AgentExtAbility目录，右键选择"New > ArkTS File"，新建一个文件并命名为AgentExtAbility.ets。

    ``` txt
    ├── ets
    │ ├── agentextability
    │ │   ├── AgentExtAbility.ets
    ```

3. 在AgentExtAbility.ets文件中，补充[AgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md)的导入模块，自定义类AgentExtAbility继承[AgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md)并实现生命周期回调。

    <!-- @[ability_agent_service_one](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/AgentExtensionAbility/entry/src/main/ets/AgentExtAbility/AgentExtAbility.ets) -->
    
    ``` TypeScript
    import { common, AgentExtensionAbility, Want } from '@kit.AbilityKit';
    import { hilog } from '@kit.PerformanceAnalysisKit';
    
    export default class AgentExtAbility extends AgentExtensionAbility {
      private comProxy: common.AgentHostProxy | null = null;
      // 创建AgentExtensionAbility
      onCreate(want: Want) {
        hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
      }
    
      // 连接
      onConnect(want: Want, proxy: common.AgentHostProxy) {
        hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onConnect');
        this.comProxy = proxy;
      }
    
      // 断开连接
      onDisconnect(want: Want, proxy: common.AgentHostProxy) {
        hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onDisconnect');
        this.comProxy = null;
      }
      // 接收数据
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
      // 认证
      onAuth(proxy: common.AgentHostProxy, handshakeData: string) {
        hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onAuth');
        try {
          // 处理认证逻辑
          let authResult = 'auth success';
          proxy.authorize(authResult);
        } catch (err) {
          let code = (err as BusinessError).code;
          let msg = (err as BusinessError).message;
          console.error(`sendData failed, err code: ${code}, err msg: ${msg}.`);
        }
      }
      // 销毁
      onDestroy() {
        hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onDestroy');
      }
    }
    ```


4. 在工程Module对应的[module.json5配置文件](../quick-start/module-configuration-file.md)中注册AgentExtensionAbility，type标签需要设置为"agent"，srcEntry标签表示当前ExtensionAbility组件所对应的代码路径。

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

5. 在工程Module的`resources/base/profile/`目录下新建agent_config.json文件，然后在其中配置[AgentCard](../reference/apis-ability-kit/js-apis-inner-application-AgentCard.md)信息，详细操作步骤请参考[Agent配置文件说明](./agent-extension-configuration.md)。

## 使用AgentExtensionAbility组件收发数据

应用可以在服务端AgentExtensionAbility组件的[onData()](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md#ondata)方法中接收客户端传递的数据和[AgentHostProxy](../reference/apis-ability-kit/js-apis-inner-application-agentHostProxy.md)对象，并且可以通过调用[AgentHostProxy](../reference/apis-ability-kit/js-apis-inner-application-agentHostProxy.md)对象的[sendData()](../reference/apis-ability-kit/js-apis-inner-application-agentHostProxy.md#senddata)方法将数据发送给客户端。

<!-- @[ability_agent_service_two](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/AgentExtensionAbility/entry/src/main/ets/AgentExtAbility/AgentExtAbility.ets) -->

``` TypeScript
import { common, AgentExtensionAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class AgentExtAbility extends AgentExtensionAbility {
  // ...
  // 接收数据
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

## 使用AgentExtensionAbility组件接收和发送安全认证请求

应用可以在服务端AgentExtensionAbility组件的[onAuth()](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md#onauth)方法中接收客户端的安全认证请求以及[AgentHostProxy](../reference/apis-ability-kit/js-apis-inner-application-agentHostProxy.md)对象，并且可以通过[AgentHostProxy](../reference/apis-ability-kit/js-apis-inner-application-agentHostProxy.md)的[authorize()](../reference/apis-ability-kit/js-apis-inner-application-agentHostProxy.md#authorize)方法向客户端发送安全认证请求。

<!-- @[ability_agent_service_three](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/AgentExtensionAbility/entry/src/main/ets/AgentExtAbility/AgentExtAbility.ets) -->

``` TypeScript
import { common, AgentExtensionAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class AgentExtAbility extends AgentExtensionAbility {
  // ...
  // 认证
  onAuth(proxy: common.AgentHostProxy, handshakeData: string) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onAuth');
    try {
      // 处理认证逻辑
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