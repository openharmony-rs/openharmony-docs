# setValueSync

## Modules to Import

```TypeScript
import { settings } from '@kit.BasicServicesKit';
```

## setValueSync

```TypeScript
function setValueSync(dataAbilityHelper: DataAbilityHelper, name: string, value: string): boolean
```

Set settingsdata value(synchronous method)

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setValueSync](arkts-basicservices-settings-setvaluesync-f.md)

**Required permissions:** ohos.permission.MANAGE_SETTINGS

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Applications.Settings.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataAbilityHelper | [DataAbilityHelper](../../apis-ability-kit/arkts-apis/arkts-ability-dataabilityhelper-dataabilityhelper-i.md) | Yes | Indicates dataAbilityHelper instance. |
| name | string | Yes | Indicates the name of the character string. |
| value | string | Yes | Indicates the value of the character string. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the operation is successful; returns `false` otherwise. |

**Examples**

```TypeScript
import featureAbility from '@ohos.ability.featureAbility';

// Update the value of SCREEN_BRIGHTNESS_STATUS. (As this data item exists in the database, the setValueSync API will update its value.)
let uri:string = settings.getUriSync(settings.display.SCREEN_BRIGHTNESS_STATUS);
let helper = featureAbility.acquireDataAbilityHelper(uri);
let ret:string = settings.setValueSync(helper, settings.display.SCREEN_BRIGHTNESS_STATUS, '100');
```


<a id="setvaluesync-1"></a>

## setValueSync

```TypeScript
function setValueSync(context: Context, name: string, value: string): boolean
```

Set settingsdata value(synchronous method)

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_SETTINGS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Applications.Settings.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Application context. Only UIAbilityContext and ExtensionContext are supported. |
| name | string | Yes | Indicates the name of the character string. |
| value | string | Yes | Indicates the value of the character string. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the operation is successful; returns `false` otherwise. |

**Examples**

```TypeScript
import { settings } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Update the value of SCREEN_BRIGHTNESS_STATUS. (As this data item exists in the database, the setValueSync API will update its value.)
// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let ret = settings.setValueSync(context, settings.display.SCREEN_BRIGHTNESS_STATUS, '100');
```


<a id="setvaluesync-2"></a>

## setValueSync

```TypeScript
function setValueSync(context: Context, name: string, value: string, domainName: string): boolean
```

Set settingsdata value(synchronous method). [DEVICE_SHARED, USER_PROPERTY] domain need ohos.permission.MANAGE_SETTINGS permission. [USER_SECURE] domain need ohos.permission.MANAGE_SECURE_SETTINGS permission.

**Since:** 11

**Required permissions:** ohos.permission.MANAGE_SECURE_SETTINGS or ohos.permission.MANAGE_SETTINGS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Applications.Settings.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Application context. Only UIAbilityContext and ExtensionContext are supported. |
| name | string | Yes | Indicates the name of the character string. |
| value | string | Yes | Indicates the value of the character string. |
| domainName | string | Yes | Indicates the name of the domain name to set. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the operation is successful; returns `false` otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

```TypeScript
import { settings } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Update the value of SCREEN_BRIGHTNESS_STATUS. (As this data item exists in the database, the setValueSync API will update its value.)
// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let ret = settings.setValueSync(context, settings.display.SCREEN_BRIGHTNESS_STATUS, '100', settings.domainName.DEVICE_SHARED);
```
