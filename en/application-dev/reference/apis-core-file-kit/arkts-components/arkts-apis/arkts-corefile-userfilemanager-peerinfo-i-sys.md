# PeerInfo (System API)

```TypeScript
interface PeerInfo
```

Defines information about a registered device.

**Since:** 9

**Deprecated since:** 26.0.0

<!--Device-userFileManager-interface PeerInfo--><!--Device-userFileManager-interface PeerInfo-End-->

**System capability:** SystemCapability.FileManagement.UserFileManager.DistributedCore

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { userFileManager } from '@kit.CoreFileKit';
```

## deviceName

```TypeScript
readonly deviceName: string
```

Name of the registered device.

**Type:** string

**Since:** 9

**Deprecated since:** 26.0.0

<!--Device-PeerInfo-readonly deviceName: string--><!--Device-PeerInfo-readonly deviceName: string-End-->

**System capability:** SystemCapability.FileManagement.UserFileManager.DistributedCore

**System API:** This is a system API.

## isOnline

```TypeScript
readonly isOnline: boolean
```

Whether the registered device is online. The value **true** means the registered device is online; the value **false** means the opposite.

**Type:** boolean

**Since:** 9

**Deprecated since:** 26.0.0

<!--Device-PeerInfo-readonly isOnline: boolean--><!--Device-PeerInfo-readonly isOnline: boolean-End-->

**System capability:** SystemCapability.FileManagement.UserFileManager.DistributedCore

**System API:** This is a system API.

## networkId

```TypeScript
readonly networkId: string
```

Network ID of the registered device.

**Type:** string

**Since:** 9

**Deprecated since:** 26.0.0

<!--Device-PeerInfo-readonly networkId: string--><!--Device-PeerInfo-readonly networkId: string-End-->

**System capability:** SystemCapability.FileManagement.UserFileManager.DistributedCore

**System API:** This is a system API.
