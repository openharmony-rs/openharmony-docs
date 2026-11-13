# @ohos.security.UkeyAuthExtensionContext (UKey Authentication Extension Context)

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @chaceli-->
<!--Designer: @chande-->
<!--Tester: @zhangzhi1995-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=6030ecb49045fc8e69f33fa93227b138ef0bcd9f translatedAt=2026-10-30T06:47:47.871Z pushedAt=2026-10-30T09:30:11.516Z nl=1 -->

**UkeyAuthExtensionContext** is the context of [UkeyAuthExtensionAbility](js-apis-UkeyAuthExtensionAbility.md), which inherits from [ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md) and provides only the termination capability.

**Since:** 26.0.1

## Modules to Import

```ts
import { UkeyAuthExtensionContext } from '@kit.DeviceCertificateKit';
```

## UkeyAuthExtensionContext

Represents the context of **UkeyAuthExtensionAbility** and provides capabilities such as terminating **UkeyAuthExtensionAbility**.

**Since:** 26.0.1

**System capability**: SystemCapability.Security.CertificateManagerDialog

### terminateSelf

terminateSelf(): Promise\<void>

Destroys the **UkeyAuthExtensionAbility** that calls this API and closes the corresponding window. This API uses a promise to return the result.

**Since:** 26.0.1

**System capability**: SystemCapability.Security.CertificateManagerDialog

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type | Description |
| -------- | -------- |
| Promise\<void> | Promise that returns no value. |

**Example**

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

Destroys the **UkeyAuthExtensionAbility** that calls this API, closes the corresponding window, and returns the result to the caller of the **UkeyAuthExtensionAbility** (usually a system service). This API uses a promise to return the result asynchronously.

**Since:** 26.0.1

**System capability**: SystemCapability.Security.CertificateManagerDialog

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| parameter | [AbilityResult](../apis-ability-kit/js-apis-inner-ability-abilityResult.md) | Yes | Information returned to the caller of the **UkeyAuthExtensionAbility**. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise\<void> | Promise that returns no value. |

**Example**

```ts
import { common } from '@kit.AbilityKit';
import { UkeyAuthExtensionAbility } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class UkeyAuthExtension extends UkeyAuthExtensionAbility {
  onSessionCreate() {
    // AbilityResult information returned to the caller. This is only an example.
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