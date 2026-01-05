# @ohos.application.StaticSubscriberExtensionContext (StaticSubscriberExtensionContext)

StaticSubscriberExtensionContext模块是StaticSubscriberExtensionAbility的上下文环境，继承自ExtensionContext。

StaticSubscriberExtensionContext模块提供StaticSubscriberExtensionAbility具有的接口和能力。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。
>
> - 本模块接口均为系统接口。

## 导入模块

```ts
import { StaticSubscriberExtensionContext } from '@kit.BasicServicesKit';
```

## 使用说明

在使用StaticSubscriberExtensionContext的功能前，需要通过StaticSubscriberExtensionAbility获取。

```ts
import { StaticSubscriberExtensionAbility, StaticSubscriberExtensionContext } from '@kit.BasicServicesKit';
```

## StaticSubscriberExtensionContext.startAbility

startAbility(want: Want, callback: AsyncCallback&lt;void&gt;): void;

拉起一个静态订阅所属的同应用的Ability。使用callback异步回调。

使用规则：
 - 调用方应用位于后台时，使用该接口启动Ability需申请`ohos.permission.START_ABILITIES_FROM_BACKGROUND`权限
 - 跨应用场景下，目标Ability的visible属性若配置为false，调用方应用需申请`ohos.permission.START_INVISIBLE_ABILITY`权限

**需要权限**：ohos.permission.START_ABILITIES_FROM_BACKGROUND

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**系统应用**：该接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名   | 类型                                | 必填 | 说明                       |
| -------- | ----------------------------------- | ---- | -------------------------- |
| want     | [Want](../apis-ability-kit/js-apis-wantAgent.md) | 是   | 启动Ability的want信息。    |
| callback | AsyncCallback&lt;void&gt;           | 是   | callback形式返回启动结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](../apis-ability-kit/errorcode-ability.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      |
| 16000001 | The specified ability does not exist.                        |
| 16000002 | Incorrect ability type.                                      |
| 16000004 | Cannot start an invisible component.                         |
| 16000005 | The specified process does not have the permission.          |
| 16000006 | Cross-user operations are not allowed.                       |
| 16000008 | The crowdtesting application expires.                        |
| 16000009 | An ability cannot be started or stopped in Wukong mode.      |
| 16000011 | The context does not exist.                                  |
| 16000050 | Internal error.                                              |
| 16000053 | The ability is not on the top of the UI.                     |
| 16000055 | Installation-free timed out.                                 |
| 16200001 | The caller has been released.                                |
| 16300003 | The target application is not the current application.       |

**示例：**

  ```ts
import { commonEventManager, BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

let want: Want = {
  bundleName: "com.example.myapp",
  abilityName: "MyAbility"
};

class MyStaticSubscriberExtensionAbility extends StaticSubscriberExtensionAbility {
  onReceiveEvent(event: commonEventManager.CommonEventData) {
    console.info(`onReceiveEvent, event: ${JSON.stringify(event)}`);

    try {
      this.context.startAbility(want, (error: BusinessError): void=> {
        if (error) {
          // 处理业务逻辑错误
          console.error(`startAbility failed, error.code: ${JSON.stringify(error.code)}, error.message: ${JSON.stringify(error.message)}.`);
          return;
        }
        // 执行正常业务
        console.info('startAbility succeed');
      });
    } catch (paramError) {
      // 处理入参错误异常
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`startAbility failed, error.code: ${JSON.stringify(code)}, error.message: ${JSON.stringify(message)}.`);
    }
  }
}
  ```

## StaticSubscriberExtensionContext.startAbility

startAbility(want: Want): Promise&lt;void&gt;;

拉起一个静态订阅所属的同应用的Ability。使用Promise异步回调。

使用规则：
 - 调用方应用位于后台时，使用该接口启动Ability需申请`ohos.permission.START_ABILITIES_FROM_BACKGROUND`权限
 - 跨应用场景下，目标Ability的visible属性若配置为false，调用方应用需申请`ohos.permission.START_INVISIBLE_ABILITY`权限

**需要权限**：ohos.permission.START_ABILITIES_FROM_BACKGROUND

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**系统应用**：该接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：22

**参数：**

| 参数名 | 类型                                | 必填 | 说明                    |
| ------ | ----------------------------------- | ---- | ----------------------- |
| want   | [Want](../apis-ability-kit/js-apis-wantAgent.md) | 是   | 启动Ability的want信息。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise形式返回启动结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](../apis-ability-kit/errorcode-ability.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.      |
| 16000001 | The specified ability does not exist.                        |
| 16000002 | Incorrect ability type.                                      |
| 16000004 | Cannot start an invisible component.                         |
| 16000005 | The specified process does not have the permission.          |
| 16000006 | Cross-user operations are not allowed.                       |
| 16000008 | The crowdtesting application expires.                        |
| 16000009 | An ability cannot be started or stopped in Wukong mode.      |
| 16000011 | The context does not exist.                                  |
| 16000050 | Internal error.                                              |
| 16000053 | The ability is not on the top of the UI.                     |
| 16000055 | Installation-free timed out.                                 |
| 16200001 | The caller has been released.                                |
| 16300003 | The target application is not the current application.       |

**示例：**

ArkTS-Dyn示例：
  ```ts
import { commonEventManager, BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

let want: Want = {
  bundleName: "com.example.myapp",
  abilityName: "MyAbility"
};

class MyStaticSubscriberExtensionAbility extends StaticSubscriberExtensionAbility {
  onReceiveEvent(event: commonEventManager.CommonEventData) {
    console.info(`onReceiveEvent, event: ${JSON.stringify(event)}`);
    try {
      this.context.startAbility(want)
        .then(() => {
          // 执行正常业务
          console.info('startAbility succeed');
        })
        .catch((error: BusinessError) => {
          // 处理业务逻辑错误
          console.error(`startAbility failed, error.code: ${JSON.stringify(error.code)}, error.message: ${JSON.stringify(error.message)}.`);
        });
    } catch (paramError) {
      // 处理入参错误异常
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`startAbility failed, error.code: ${JSON.stringify(code)}, error.message: ${JSON.stringify(message)}.`);
    }
  }
}
  ```

ArkTS-Sta示例：
  ```ts
import { commonEventManager, BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

let want: Want = {
  bundleName: "com.example.myapp",
  abilityName: "MyAbility"
};

class MyStaticSubscriberExtensionAbility extends StaticSubscriberExtensionAbility {
  onReceiveEvent(event: commonEventManager.CommonEventData) {
    console.info(`onReceiveEvent, event: ${JSON.stringify(event)}`);
    try {
      this.context.startAbility(want)
        .then(() => {
          // 执行正常业务
          console.info('startAbility succeed');
        })
        .catch((error) => {
          // 处理业务逻辑错误
          console.error(`startAbility failed, error.code: ${(error.code)}, error.message: ${(error.message)}.`);
        });
    } catch (paramError) {
      // 处理入参错误异常
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`startAbility failed, error.code: ${JSON.stringify(code)}, error.message: ${JSON.stringify(message)}.`);
    }
  }
}
  ```

## 使用@ohos.transfer进行StaticSubscriberExtensionContext类型转换

ArkTS-Dyn中使用ArkTS-Sta的StaticSubscriberExtensionContext对象。

**示例：**

- 在ArkTS-Sta模块中将ArkTS-Sta StaticSubscriberExtensionContext转换成ArkTS-Dyn StaticSubscriberExtensionContext，传入到ArkTS-Dyn子模块`library`中。

  ArkTS-Sta示例：
  ```TypeScript
  'use static'
  import { transfer } from '@kit.ArkTS';
  import { StaticSubscriberExtensionContextStaticToDynamic } from 'library';
  import { commonEventManager, BusinessError, StaticSubscriberExtensionAbility } from '@kit.BasicServicesKit';

  class MyStaticSubscriberExtensionAbility extends StaticSubscriberExtensionAbility {
    onReceiveEvent(event: commonEventManager.CommonEventData) {
      console.info(`onReceiveEvent, event: ${JSON.stringify(event)}`);
      try {
        let dynamicContext = transfer.transferDynamic(this.context, 'CommonEventManager.StaticSubscriberExtensionContext');
        StaticSubscriberExtensionContextStaticToDynamic(dynamicContext);
      } catch (paramError) {
        // 处理入参错误异常
        let code = (paramError as BusinessError).code;
        let message = (paramError as BusinessError).message;
        console.error(`startAbility failed, error.code: ${JSON.stringify(code)}, error.message: ${JSON.stringify(message)}.`);
      }
    }
  }
  ```

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn StaticSubscriberExtensionContext的方法。

  ArkTS-Dyn示例：
  ```TypeScript
  import { commonEventManager, BusinessError, StaticSubscriberExtensionContext } from '@kit.BasicServicesKit';
  import { Want } from '@kit.AbilityKit';

  let want: Want = {
    bundleName: "com.example.myapp",
    abilityName: "MyAbility"
  };
  export function StaticSubscriberExtensionContextStaticToDynamic(context_: any) {
    try {
      let context: StaticSubscriberExtensionContext = context_ as StaticSubscriberExtensionContext;
      this.context.startAbility(want)
        .then(() => {
          // 执行正常业务
          console.info('startAbility succeed');
        })
        .catch((error) => {
          // 处理业务逻辑错误
          console.error(`startAbility failed, error.code: ${(error.code)}, error.message: ${(error.message)}.`);
        });
    } catch (paramError) {
      // 处理入参错误异常
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`startAbility failed, error.code: ${JSON.stringify(code)}, error.message: ${JSON.stringify(message)}.`);
    }
  }
  ```

ArkTS-Sta中使用ArkTS-Dyn的StaticSubscriberExtensionContext对象。

**示例：**

- 在ArkTS-Dyn模块创建得到ArkTS-Dyn StaticSubscriberExtensionContext对象，传到ArkTS-Sta子模块`library`中。

  ArkTS-Dyn示例：
  ```TypeScript
  import { commonEventManager, BusinessError, StaticSubscriberExtensionAbility } from '@kit.BasicServicesKit';
  import { StaticSubscriberExtensionContextDynamicToStatic } from 'library';

  class MyStaticSubscriberExtensionAbility extends StaticSubscriberExtensionAbility {
    onReceiveEvent(event: commonEventManager.CommonEventData) {
      console.info(`onReceiveEvent, event: ${JSON.stringify(event)}`);
      try {
        StaticSubscriberExtensionContextDynamicToStatic(this.context);
      } catch (paramError) {
        // 处理入参错误异常
        let code = (paramError as BusinessError).code;
        let message = (paramError as BusinessError).message;
        console.error(`startAbility failed, error.code: ${JSON.stringify(code)}, error.message: ${JSON.stringify(message)}.`);
      }
    }
  }
  ```

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn StaticSubscriberExtensionContext的方法。

  ArkTS-Sta示例：
  ```TypeScript
  'use static'
  import { commonEventManager, BusinessError, StaticSubscriberExtensionContext } from '@kit.BasicServicesKit';
  import { Want } from '@kit.AbilityKit';

  let want: Want = {
    bundleName: "com.example.myapp",
    abilityName: "MyAbility"
  };
  export function StaticSubscriberExtensionContextDynamicToStatic(dynObject: Object | undefined | null) {
    try {
      let staticContext: StaticSubscriberExtensionContext = transfer.transferStatic(dynObject, 'CommonEventManager.StaticSubscriberExtensionContext') as StaticSubscriberExtensionContext;
      staticContext.startAbility(want)
        .then(() => {
          // 执行正常业务
          console.info('startAbility succeed');
        })
        .catch((error) => {
          // 处理业务逻辑错误
          console.error(`startAbility failed, error.code: ${(error.code)}, error.message: ${(error.message)}.`);
        });
    } catch (paramError) {
      // 处理入参错误异常
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`startAbility failed, error.code: ${JSON.stringify(code)}, error.message: ${JSON.stringify(message)}.`);
    }
  }
  ```