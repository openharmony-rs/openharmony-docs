# AutoFillExtensionContext (System API)

The AutoFillExtensionContext module provides the context environment for the AutoFillExtensionAbility. It inherits from [ExtensionContext](arkts-ability-extensioncontext-c.md).

**Inheritance/Implementation:** AutoFillExtensionContext extends [ExtensionContext](arkts-ability-extensioncontext-c.md)

**Since:** 11

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**System API:** This is a system API.

## reloadInModal

```TypeScript
reloadInModal(customData: CustomData): Promise<void>
```

Reload autoFillExtension in modal window.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| customData | [CustomData](arkts-ability-customdata-i-sys.md) | Yes | User defined data. When the modal window of AutoFillExtension needs to be raised again, pass this parameter to the application framework. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. Interface caller is not a system app. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | If the input parameter is not valid parameter. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
The autofill service is triggered when a user touches the account and password text box, and an account selection page is displayed in the onFillRequest lifecycle of the [AutoFillExtensionAbility](arkts-ability-app-ability-autofillextensionability-autofillextensionability-c-sys.md).

When an account is selected, reloadInModal is called to trigger the autofill service again, and a modal page is started in the onFillRequest lifecycle of the AutoFillExtensionAbility.
```

```TypeScript
When the user selects an account on the account selection page, the reloadInModal API is called.
```
