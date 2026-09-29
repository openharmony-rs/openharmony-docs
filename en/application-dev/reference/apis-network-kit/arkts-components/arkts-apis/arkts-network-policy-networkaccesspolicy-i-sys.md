# NetworkAccessPolicy (System API)

```TypeScript
export interface NetworkAccessPolicy
```

Network access policy.

**Since:** 12

<!--Device-policy-export interface NetworkAccessPolicy--><!--Device-policy-export interface NetworkAccessPolicy-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## allowCellular

```TypeScript
allowCellular?: boolean
```

Whether the application is allowed to access the cellular network. The value **true** indicates that the application is allowed to access the cellular network, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 12

<!--Device-NetworkAccessPolicy-allowCellular?: boolean--><!--Device-NetworkAccessPolicy-allowCellular?: boolean-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## allowWiFi

```TypeScript
allowWiFi?: boolean
```

Whether the application is allowed to access the Wi-Fi network. The value **true** indicates that the application is allowed to access the Wi-Fi network, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 12

<!--Device-NetworkAccessPolicy-allowWiFi?: boolean--><!--Device-NetworkAccessPolicy-allowWiFi?: boolean-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## alwaysAllowCellular

```TypeScript
alwaysAllowCellular?: boolean
```

Whether the application is always allowed to access the cellular network. The value **true** indicates that the application is always allowed to access the cellular network, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 18

<!--Device-NetworkAccessPolicy-alwaysAllowCellular?: boolean--><!--Device-NetworkAccessPolicy-alwaysAllowCellular?: boolean-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## alwaysAllowWiFi

```TypeScript
alwaysAllowWiFi?: boolean
```

Whether the application is always allowed to access the Wi-Fi network. The value **true** indicates that the application is always allowed to access the Wi-Fi network, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 18

<!--Device-NetworkAccessPolicy-alwaysAllowWiFi?: boolean--><!--Device-NetworkAccessPolicy-alwaysAllowWiFi?: boolean-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.
