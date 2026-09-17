# setValue

## Modules to Import

```TypeScript
import { settings } from '@kit.BasicServicesKit';
```

## setValue

```TypeScript
function setValue(context: Context, name: string, value: string, callback: AsyncCallback<boolean>): void
```

Set settingsdata value.

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
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | The callback of setValue result. |

**Examples**

```TypeScript
import { settings } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Update the value of SCREEN_BRIGHTNESS_STATUS. (As this data item exists in the database, the setValue API will update its value.)
// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
settings.setValue(context, settings.display.SCREEN_BRIGHTNESS_STATUS, '100', (status) => {
  console.info('Callback return whether value is set.');
});
```

```TypeScript
import { settings } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Update the value of SCREEN_BRIGHTNESS_STATUS. (As this data item exists in the database, the setValue API will update its value.)
// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
settings.setValue(context, settings.display.SCREEN_BRIGHTNESS_STATUS, '100').then((status) => {
  console.info('Callback return whether value is set.');
});
```

```TypeScript
import { settings } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Update the value of SCREEN_BRIGHTNESS_STATUS. (As this data item exists in the database, the setValue API will update its value.)
// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
settings.setValue(context, settings.display.SCREEN_BRIGHTNESS_STATUS, '100', settings.domainName.DEVICE_SHARED).then((status) => {
  console.info(`callback:return whether value is set.`)
});
```


## setValue

```TypeScript
function setValue(context: Context, name: string, value: string): Promise<boolean>
```

Set settingsdata value.

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
| Promise&lt;boolean&gt; | Returns `true` if the operation is successful; returns `false` otherwise. |

**Examples**

See [setValue](#setvalue)


## setValue

```TypeScript
function setValue(context: Context, name: string, value: string, domainName: string): Promise<boolean>
```

Set settingsdata value. [DEVICE_SHARED, USER_PROPERTY] domain need ohos.permission.MANAGE_SETTINGS permission. [USER_SECURE] domain need ohos.permission.MANAGE_SECURE_SETTINGS permission.

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
| Promise&lt;boolean&gt; | Returns `true` if the operation is successful; returns `false` otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

See [setValue](#setvalue)
