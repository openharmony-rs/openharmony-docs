# isWlanSupported

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## isWlanSupported

```TypeScript
function isWlanSupported(): boolean
```

Query whether Wi-Fi is available

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.WiFi.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the Wi-Fi is available, returns `false` otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [2401000](../errorcode-wifi.md#2401000-sta-internal-error) | Operation failed. |
