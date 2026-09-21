# sendCommand

## Modules to Import

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## sendCommand

```TypeScript
function sendCommand(command: LocationCommand, callback: AsyncCallback<boolean>): void
```

Send extended commands to location subsystem.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [sendCommand](arkts-location-geolocationmanager-sendcommand-f.md)

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| command | [LocationCommand](arkts-location-geolocation-locationcommand-i.md) | Yes | Indicates the extended Command Message Body. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Indicates the callback for reporting the send command result. |

**Examples**

```TypeScript
import geolocation from '@ohos.geolocation';
let requestInfo:geolocation.LocationCommand = {'scenario': 0x301, 'command': "command_1"};
geolocation.sendCommand(requestInfo, (err, result) => {
    if (err) {
        console.info('sendCommand: err=' + JSON.stringify(err));
    }
    if (result) {
        console.info('sendCommand: result=' + JSON.stringify(result));
    }
});
```


<a id="sendcommand-1"></a>

## sendCommand

```TypeScript
function sendCommand(command: LocationCommand): Promise<boolean>
```

Send extended commands to location subsystem.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [sendCommand](arkts-location-geolocationmanager-sendcommand-f.md)

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| command | [LocationCommand](arkts-location-geolocation-locationcommand-i.md) | Yes | Indicates the extended Command Message Body. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | The promise returned by the function. |

**Examples**

```TypeScript
import geolocation from '@ohos.geolocation';
let requestInfo:geolocation.LocationCommand = {'scenario': 0x301, 'command': "command_1"};
geolocation.sendCommand(requestInfo).then((result) => {
    console.info('promise, sendCommand: ' + JSON.stringify(result));
});
```
