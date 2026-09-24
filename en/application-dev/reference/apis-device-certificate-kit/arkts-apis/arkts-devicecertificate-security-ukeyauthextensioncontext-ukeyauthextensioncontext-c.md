# UkeyAuthExtensionContext

```TypeScript
declare class UkeyAuthExtensionContext extends ExtensionContext
```

UkeyAuthExtensionContext is the context of a UkeyAuthExtensionAbility, providing only terminate, report-drawn-completed and color-mode capabilities. It inherits from [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md).

**Inheritance/Implementation:** UkeyAuthExtensionContext extends [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)

**Since:** 26.0.1

**System capability:** SystemCapability.Security.CertificateManagerDialog

## Modules to Import

```TypeScript
import { UkeyAuthExtensionContext } from '@kit.DeviceCertificateKit';
```

## terminateSelf

```TypeScript
terminateSelf(): Promise<void>
```

Destroys this UkeyAuthExtensionAbility and closes the corresponding window. This API uses a promise to return the result.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManagerDialog

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

## terminateSelfWithResult

```TypeScript
terminateSelfWithResult(parameter: AbilityResult): Promise<void>
```

Destroys this UkeyAuthExtensionAbility, closes the corresponding window, and returns the result to the caller of the UkeyAuthExtensionAbility (usually a system service). This API uses a promise to return the result.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManagerDialog

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parameter | [AbilityResult](../../apis-ability-kit/arkts-apis/arkts-ability-abilityresult-abilityresult-i.md) | Yes | Information returned to the caller of the UkeyAuthExtensionAbility. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |
