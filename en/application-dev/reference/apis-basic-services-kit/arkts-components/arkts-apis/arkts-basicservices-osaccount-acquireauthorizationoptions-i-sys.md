# AcquireAuthorizationOptions (System API)

Defines the options for acquiring the authorization.

**Since:** 24

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## challenge

```TypeScript
challenge?: Uint8Array
```

Random challenge value, which prevents replay attacks. The value contains a maximum of 32 bytes. The default value is **undefined**.

**Type:** Uint8Array

**Default:** undefined

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## interactionContext

```TypeScript
interactionContext?: Context
```

User interaction context configuration. The default value is **undefined**.

- If no context is specified, the authorization dialog box is displayed in modal system mode.  
- If [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) or [UIExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiextensioncontext-c.md) is specified, the authorization dialog box is displayed in modal application mode.  
- If no valid context is provided, the authorization dialog box cannot be displayed.

Note: This parameter is valid only when **isInteractionAllowed** is set to **true**.

**Type:** [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)

**Default:** undefined, which means the authorization dialog will be displayed in modal system mode.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## isInteractionAllowed

```TypeScript
isInteractionAllowed?: boolean
```

Whether user interaction is allowed. The default value is **true**.

If the value is **true**, the authorization dialog box can be displayed in the interaction context. If the value is **false**, the authorization dialog box cannot be displayed.

Note: This option is valid only when the caller is in the foreground. If the caller is in the background, user interaction is not allowed.

**Type:** boolean

**Default:** true

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## isReuseNeeded

```TypeScript
isReuseNeeded?: boolean
```

Whether to reuse the previous authorization. The default value is **true**.

If the value is **true** and the authorization result is valid, the result will be reused. Otherwise, a new authorization will be executed.

**Type:** boolean

**Default:** true

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
