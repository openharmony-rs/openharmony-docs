# StaticSubscriberExtensionContext（系统接口）

StaticSubscriberExtensionContext模块是StaticSubscriberExtensionAbility的上下文环境，继承自ExtensionContext。

StaticSubscriberExtensionContext模块提供StaticSubscriberExtensionAbility具有的接口和能力。

**继承/实现关系：** StaticSubscriberExtensionContext extends [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md#ExtensionContext)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## startAbility

```TypeScript
startAbility(want: Want, callback: AsyncCallback<void>): void
```

拉起一个静态订阅所属的同应用的Ability。使用callback异步回调。

使用规则：

- 调用方应用位于后台时，使用该接口启动Ability需申请`ohos.permission.START_ABILITIES_FROM_BACKGROUND`权限
- 跨应用场景下，目标Ability的visible属性若配置为false，调用方应用需申请`ohos.permission.START_INVISIBLE_ABILITY`权限

**起始版本：** 10

**需要权限：** ohos.permission.START_ABILITIES_FROM_BACKGROUND

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动Ability的want信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | callback形式返回启动结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000009](../../errorcode-universal.md#16000009-An) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000053](../../errorcode-universal.md#16000053-The) | The ability is not on the top of the UI. |
| [16000055](../../errorcode-universal.md#16000055-Installationfree) | Installation-free timed out. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [16300003](../../errorcode-universal.md#16300003-The) | The target application is not the current application. |

**示例：**

```TypeScript
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
      this.context.startAbility(want, (error: BusinessError) => {
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

## startAbility

```TypeScript
startAbility(want: Want): Promise<void>
```

拉起一个静态订阅所属的同应用的Ability。使用Promise异步回调。

使用规则：

- 调用方应用位于后台时，使用该接口启动Ability需申请`ohos.permission.START_ABILITIES_FROM_BACKGROUND`权限
- 跨应用场景下，目标Ability的visible属性若配置为false，调用方应用需申请`ohos.permission.START_INVISIBLE_ABILITY`权限

**起始版本：** 10

**需要权限：** ohos.permission.START_ABILITIES_FROM_BACKGROUND

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动Ability的want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise形式返回启动结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000009](../../errorcode-universal.md#16000009-An) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000053](../../errorcode-universal.md#16000053-The) | The ability is not on the top of the UI. |
| [16000055](../../errorcode-universal.md#16000055-Installationfree) | Installation-free timed out. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |
| [16300003](../../errorcode-universal.md#16300003-The) | The target application is not the current application. |

**示例：**

```TypeScript
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

