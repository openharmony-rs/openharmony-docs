# @ohos.application.DistributedExtensionContext (协同Extension上下文)

<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedSched-->

DistributedExtensionContext模块是DistributedExtensionAbility的上下文环境，继承自ExtensionContext。

> **说明：**
>
> 本模块首批接口从API version 26开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块接口仅可在Stage模型下使用。

## 使用说明

在使用DistributedExtensionContext的功能前，需要通过DistributedExtensionAbility子类实例获取。

```ts
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';

export default class DistributedExtension extends DistributedExtensionAbility {
  onCreate() {
    let context = this.context; // 获取DistributedExtensionContext
  }
}
```

## DistributedExtensionContext.connectServiceExtensionAbility

connectServiceExtensionAbility(want: Want, options: ConnectOptions): number

连接远端ServiceExtensionAbility。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名  | 类型                                                         | 必填 | 说明                                                         |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| want    | [Want](../apis-ability-kit/js-apis-app-ability-want.md)      | 是   | Want类型参数，传入需要连接的远端ServiceExtensionAbility的信息，如ability名称、bundle名称、deviceId等。 |
| options | [ConnectOptions](../apis-ability-kit/js-apis-inner-ability-connectOptions.md) | 是   | ConnectOptions类型的回调函数，返回服务连接成功、断开或连接失败后的信息。 |

**返回值：**

| 类型   | 说明                                                         |
| ------ | ------------------------------------------------------------ |
| number | 返回连接ID，后续通过该ID断开连接。该ID由connectServiceExtensionAbility返回时分配，为递增数字。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode/errorcode-universal.md)和[Ability错误码](../apis-ability-kit/errorcode-ability.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled. |
| 16000013 | The application is controlled by EDM. |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

let connectionId: number = -1;

export default class DistributedExtension extends DistributedExtensionAbility {
    try {
      connectionId = this.context.connectServiceExtensionAbility(want, options);
      console.info(`connectServiceExtensionAbility success, connectionId: ${connectionId}`);
    } catch (err) {
      let error = err as BusinessError;
      console.error(`connectServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
    }
}
```



## DistributedExtensionContext.disconnectServiceExtensionAbility

disconnectServiceExtensionAbility(connection: number): Promise\<void\>

断开与远端ServiceExtensionAbility的连接。使用Promise异步回调。

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名     | 类型   | 必填 | 说明                                                     |
| ---------- | ------ | ---- | -------------------------------------------------------- |
| connection | number | 是   | 连接ID，即connectServiceExtensionAbility返回的number值。 |

**返回值：**

| 类型            | 说明                               |
| --------------- | ---------------------------------- |
| Promise\<void\> | Promise对象，无返回结果的Promise。 |

**错误码：**

以下错误码的详细介绍请参见[Ability错误码](../apis-ability-kit/errorcode-ability.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 16000003 | The connection id does not exist. |
| 16000011 | The ability has been destroyed. The context is no longer valid, meaning the context does not exist. |
| 16000050 | Internal error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';

// connectionId为connectServiceExtensionAbility返回的连接ID
let connectionId: number = -1;

export default class DistributedExtension extends DistributedExtensionAbility {
  disconnectRemoteService() {
    try {
      this.context.disconnectServiceExtensionAbility(connectionId)
        .then(() => {
          console.info('disconnectServiceExtensionAbility success');
        })
        .catch((err: BusinessError) => {
          console.error(`disconnectServiceExtensionAbility failed, error.code: ${err.code}, error.message: ${err.message}`);
        });
    } catch (err) {
      let error = err as BusinessError;
      console.error(`disconnectServiceExtensionAbility catch error, code: ${error.code}, message: ${error.message}`);
    }
  }
}
```