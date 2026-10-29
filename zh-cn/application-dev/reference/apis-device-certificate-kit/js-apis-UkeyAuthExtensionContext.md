# @ohos.security.UkeyAuthExtensionContext (UKey认证扩展能力上下文)

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @chaceli-->
<!--Designer: @chande-->
<!--Tester: @zhangzhi1995-->
<!--Adviser: @zengyawen-->

UkeyAuthExtensionContext是[UkeyAuthExtensionAbility](js-apis-UkeyAuthExtensionAbility.md)的上下文，继承自[ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md)，仅提供终止能力。

**起始版本：** 26.0.1

## 导入模块

```ts
import { UkeyAuthExtensionContext } from '@kit.DeviceCertificateKit';
```

## UkeyAuthExtensionContext

表示UkeyAuthExtensionAbility的上下文，提供终止UkeyAuthExtensionAbility等能力。

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Security.CertificateManagerDialog

### terminateSelf

terminateSelf(): Promise\<void>

销毁调用当前接口的UkeyAuthExtensionAbility并关闭相应窗口。使用Promise异步回调。

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Security.CertificateManagerDialog

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise\<void> | Promise对象，无返回结果。 |

**示例：**

```ts
import { UkeyAuthExtensionAbility } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class UkeyAuthExtension extends UkeyAuthExtensionAbility {
  onSessionCreate() {
    this.context.terminateSelf().then(() => {
      console.info('Succeeded in terminating UkeyAuthExtension.');
    }).catch((error: Error) => {
      let err = error as BusinessError;
      console.error(`Failed to terminate UkeyAuthExtension. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

### terminateSelfWithResult

terminateSelfWithResult(parameter: AbilityResult): Promise\<void>

销毁调用当前接口的UkeyAuthExtensionAbility，关闭相应窗口，并将结果返回给UkeyAuthExtensionAbility的调用方（通常为系统服务）。使用Promise异步回调。

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Security.CertificateManagerDialog

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| parameter | [AbilityResult](../apis-ability-kit/js-apis-inner-ability-abilityResult.md) | 是 | 返回给UkeyAuthExtensionAbility调用方的信息。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise\<void> | Promise对象，无返回结果。 |

**示例：**

```ts
import { common } from '@kit.AbilityKit';
import { UkeyAuthExtensionAbility } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class UkeyAuthExtension extends UkeyAuthExtensionAbility {
  onSessionCreate() {
    // 返回给调用方的AbilityResult信息，此处仅为示例
    let abilityResult: common.AbilityResult = {
      resultCode: 0,
      want: undefined
    };
    this.context.terminateSelfWithResult(abilityResult).then(() => {
      console.info('Succeeded in terminating UkeyAuthExtension.');
    }).catch((error: Error) => {
      let err = error as BusinessError;
      console.error(`Failed to terminate UkeyAuthExtension. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```