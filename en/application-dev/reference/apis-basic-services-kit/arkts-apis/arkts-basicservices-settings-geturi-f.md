# getURI

## Modules to Import

```TypeScript
import { settings } from '@kit.BasicServicesKit';
```

<a id="geturi1"></a>

## getURI

```TypeScript
function getURI(name: string, callback: AsyncCallback<object>): void
```

Constructs a URI for a specific name-value pair for monitoring data of the ability that uses the Data template.

**Since:** 7

**Deprecated since:** 9

<!--Device-settings-function getURI(name: string, callback: AsyncCallback<object>): void--><!--Device-settings-function getURI(name: string, callback: AsyncCallback<object>): void-End-->

**System capability:** SystemCapability.Applications.Settings.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Indicates the name of the setting to set. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;object&gt; | Yes | The callback of getURI result. |

**Examples**

```TypeScript
settings.getURI(settings.display.SCREEN_BRIGHTNESS_STATUS, (uri:string) => {
    console.info(`callback:uri -> ${JSON.stringify(uri)}`)
})
```


<a id="geturi2"></a>

## getURI

```TypeScript
function getURI(name: string): Promise<object>
```

Constructs a URI for a specific name-value pair for monitoring data of the ability that uses the Data template.

**Since:** 7

**Deprecated since:** 9

<!--Device-settings-function getURI(name: string): Promise<object>--><!--Device-settings-function getURI(name: string): Promise<object>-End-->

**System capability:** SystemCapability.Applications.Settings.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Indicates the name of the setting to set. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;object&gt; | Returns the corresponding URI; returns `null` if the URI does not exist. |

**Examples**

```TypeScript
settings.getURI(settings.display.SCREEN_BRIGHTNESS_STATUS).then((uri:string) => {
    console.info(`promise:uri -> ${JSON.stringify(uri)}`)
})
```
