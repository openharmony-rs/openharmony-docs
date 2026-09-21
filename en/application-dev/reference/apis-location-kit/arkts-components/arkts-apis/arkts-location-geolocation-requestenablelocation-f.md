# requestEnableLocation

## Modules to Import

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## requestEnableLocation

```TypeScript
function requestEnableLocation(callback: AsyncCallback<boolean>): void
```

Request enable location

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Indicates the callback for reporting the location switch status. |

**Examples**

```TypeScript
import geolocation from '@ohos.geolocation';
geolocation.requestEnableLocation((err, data) => {
    if (err) {
        console.info('requestEnableLocation: err=' + JSON.stringify(err));
    }
    if (data) {
        console.info('requestEnableLocation: data=' + JSON.stringify(data));
    }
});
```


<a id="requestenablelocation-1"></a>

## requestEnableLocation

```TypeScript
function requestEnableLocation(): Promise<boolean>
```

Request enable location

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | The promise returned by the function. |

**Examples**

```TypeScript
import geolocation from '@ohos.geolocation';
geolocation.requestEnableLocation().then((result) => {
    console.info('promise, requestEnableLocation: ' + JSON.stringify(result));
});
```
