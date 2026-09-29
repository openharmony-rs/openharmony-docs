# InterfaceStateInfo (System API)

```TypeScript
export interface InterfaceStateInfo
```

Listens for status changes of an Ethernet NIC.

**Since:** 11

<!--Device-ethernet-export interface InterfaceStateInfo--><!--Device-ethernet-export interface InterfaceStateInfo-End-->

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { ethernet } from '@kit.NetworkKit';
```

## active

```TypeScript
active: boolean
```

Whether the Ethernet NIC is activated. The value **true** indicates that the Ethernet NIC is activated, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 11

<!--Device-InterfaceStateInfo-active: boolean--><!--Device-InterfaceStateInfo-active: boolean-End-->

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.

## iface

```TypeScript
iface: string
```

Name of the Ethernet NIC.

**Type:** string

**Since:** 11

<!--Device-InterfaceStateInfo-iface: string--><!--Device-InterfaceStateInfo-iface: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**System API:** This is a system API.
