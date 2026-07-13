# preloadUIExtensionAbility（系统接口）

## preloadUIExtensionAbility

```TypeScript
function preloadUIExtensionAbility(want: Want): Promise<number>
```

预加载指定的[UIExtensionAbility](arkts-ability-uiextensionability-c.md)并返回预加载UIExtensionAbility实例
的ID。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.PRELOAD_UI_EXTENSION_ABILITY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 启动Ability的Want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回预加载的[UIExtensionAbility](arkts-ability-uiextensionability-c.md)的ID，用于后续清除或管理操作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1.Connect to system service failed;2.Send restart message to system service failed; 3.System service failed to communicate with dependency module.4.Preload UIExtensionAbility timeout. |

**示例：**

```TypeScript
import { abilityManager, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const preloadWant: Want = {
    bundleName: 'com.example.application',
    abilityName: 'EntryBackupAbility',
    moduleName: 'entry',
    parameters: {
      'ability.want.params.uiExtensionType': 'sys/commonUI'
    }
  };

  abilityManager.preloadUIExtensionAbility(preloadWant)
    .then((preloadId: number) => {
      console.info(`preloadUIExtensionAbility success, preloadId: ${preloadId}`);
    })
    .catch((err: BusinessError) => {
      console.error(`preloadUIExtensionAbility fail, err: ${JSON.stringify(err)}`);
    });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`preloadUIExtensionAbility failed, code is ${code}, message is ${message}`);
}

```

