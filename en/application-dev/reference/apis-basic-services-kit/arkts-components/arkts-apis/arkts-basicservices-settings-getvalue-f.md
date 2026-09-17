# getValue

## Modules to Import

```TypeScript
import { settings } from '@kit.BasicServicesKit';
```

## getValue

```TypeScript
function getValue(dataAbilityHelper: DataAbilityHelper, name: string, callback: AsyncCallback<object>): void
```

Obtains the value of a specified character string in the database.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** getValue

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Applications.Settings.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataAbilityHelper | [DataAbilityHelper](../../apis-ability-kit/arkts-apis/arkts-ability-dataabilityhelper-dataabilityhelper-i.md) | Yes | Indicates the [DataAbilityHelper](../../apis-ability-kit/arkts-apis/arkts-ability-dataabilityhelper-dataabilityhelper-i.md) used to access the database. |
| name | string | Yes | Indicates the name of the character string. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;object&gt; | Yes | The callback of getValue result. |

**Examples**

```TypeScript
import { settings } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
settings.getValue(context, settings.display.SCREEN_BRIGHTNESS_STATUS, (err, value) => {
  if (err) {
    console.error(`Failed to get the setting. ${err.message} `);
    return;
  }
  console.info(`callback:value -> ${value}`)
});
```

```TypeScript
import { settings } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
settings.getValue(context, settings.display.SCREEN_BRIGHTNESS_STATUS).then((value) => {
  console.info(`promise:value -> ${value}`)
});
```

```TypeScript
import { settings } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Update the value of SCREEN_BRIGHTNESS_STATUS. (As this data item exists in the database, the getValue API will update its value.)
// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
settings.getValue(context, settings.display.SCREEN_BRIGHTNESS_STATUS, settings.domainName.DEVICE_SHARED).then((value) => {
  console.info(`Promise:value -> ${value}`);
});
```

```TypeScript
import featureAbility from '@ohos.ability.featureAbility';

let uri:string = settings.getUriSync(settings.display.SCREEN_BRIGHTNESS_STATUS);
let helper = featureAbility.acquireDataAbilityHelper(uri);
settings.getValue(helper, settings.display.SCREEN_BRIGHTNESS_STATUS, (err:Error, value:string) => {
    if (err) {
        console.error(`Failed to get the setting. ${err.message} `);
        return;
    }
    console.info(`callback:value -> ${JSON.stringify(value)}`)
});
```

```TypeScript
import featureAbility from '@ohos.ability.featureAbility';

let uri:string = settings.getUriSync(settings.display.SCREEN_BRIGHTNESS_STATUS);
let helper = featureAbility.acquireDataAbilityHelper(uri);
settings.getValue(helper, settings.display.SCREEN_BRIGHTNESS_STATUS).then((value:string) => {
    console.info(`promise:value -> ${JSON.stringify(value)}`)
});
```


## getValue

```TypeScript
function getValue(dataAbilityHelper: DataAbilityHelper, name: string): Promise<object>
```

Obtains the value of a specified character string in the database.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** getValue

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Applications.Settings.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dataAbilityHelper | [DataAbilityHelper](../../apis-ability-kit/arkts-apis/arkts-ability-dataabilityhelper-dataabilityhelper-i.md) | Yes | Indicates the [DataAbilityHelper](../../apis-ability-kit/arkts-apis/arkts-ability-dataabilityhelper-dataabilityhelper-i.md) used to access the database. |
| name | string | Yes | Indicates the name of the character string. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;object&gt; | Returns the value of the character string in the domain if any is found; returns `null` otherwise. |

**Examples**

See [getValue](#getvalue)


## getValue

```TypeScript
function getValue(context: Context, name: string, callback: AsyncCallback<string>): void
```

Get value from settingsdata

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Applications.Settings.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Application context. Only UIAbilityContext and ExtensionContext are supported. |
| name | string | Yes | Indicates the name of the character string. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | The callback of getValue result. |

**Examples**

See [getValue](#getvalue)


## getValue

```TypeScript
function getValue(context: Context, name: string): Promise<string>
```

Get value from settingsdata

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Applications.Settings.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Application context. Only UIAbilityContext and ExtensionContext are supported. |
| name | string | Yes | Indicates the name of the character string. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Returns the value of the character string in the domain if any is found; returns `null` otherwise. |

**Examples**

See [getValue](#getvalue)


## getValue

```TypeScript
function getValue(context: Context, name: string, domainName: string): Promise<string>
```

Get value from settingsdata [USER_SECURE] domain need ohos.permission.MANAGE_SECURE_SETTINGS permission.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Applications.Settings.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Application context. Only UIAbilityContext and ExtensionContext are supported. |
| name | string | Yes | Indicates the name of the character string. |
| domainName | string | Yes | Indicates the name of the domain name to set. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Returns the value of the character string in the domain if any is found; returns `null` otherwise. |

**Examples**

See [getValue](#getvalue)
