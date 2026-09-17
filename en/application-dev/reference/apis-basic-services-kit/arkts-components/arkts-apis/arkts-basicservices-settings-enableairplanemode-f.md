# enableAirplaneMode

## Modules to Import

```TypeScript
import { settings } from '@kit.BasicServicesKit';
```

## enableAirplaneMode

```TypeScript
function enableAirplaneMode(enable: boolean, callback: AsyncCallback<void>): void
```

Enables or disables airplane mode.

**Since:** 7

**Deprecated since:** 26.0.0

**System capability:** SystemCapability.Applications.Settings.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Specifies whether to enable airplane mode. The value `true` means to enable airplane mode, and `false` means to disable airplane mode. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The callback of enableAirplaneMode result. |

**Examples**

```TypeScript
let isEnabled :boolean = true;
settings.enableAirplaneMode(isEnabled, (err:Error) => {
    if (err) {
        console.error('Failed to enable AirplaneMode.');
        return;
    }
    console.info('Return true if enable.');
})
```

```TypeScript
let isEnabled :boolean = true;
settings.enableAirplaneMode(isEnabled).then(() => {
  console.info('Succeeded in enabling AirplaneMode.');
}).catch((err:Error) => {
  console.error(`Failed to enable AirplaneMode. Cause: ${err}`);
})
```


## enableAirplaneMode

```TypeScript
function enableAirplaneMode(enable: boolean): Promise<void>
```

Enables or disables airplane mode.

**Since:** 7

**Deprecated since:** 26.0.0

**System capability:** SystemCapability.Applications.Settings.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Specifies whether to enable airplane mode. The value `true` means to enable airplane mode, and `false` means to disable airplane mode. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Return Promise. |

**Examples**

See [enableAirplaneMode](#enableairplanemode)
