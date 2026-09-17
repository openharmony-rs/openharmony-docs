# getSupportedFeatures (System API)

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getSupportedFeatures

```TypeScript
function getSupportedFeatures(): number
```

Obtains the features supported by this device.

<p>To check whether this device supports a specified feature.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getSupportedFeatures](arkts-connectivity-wifimanager-getsupportedfeatures-f-sys.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the features supported by this device. |
