# InterfaceSharingStateInfo（系统接口）

唤醒在网络共享模式下的变化时的监听器。

**起始版本：** 23

<!--Device-sharing-export interface InterfaceSharingStateInfo--><!--Device-sharing-export interface InterfaceSharingStateInfo-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetSharing

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { sharing } from '@kit.NetworkKit';
```

## iface

```TypeScript
iface: string
```

指定的共享网络名称。

**类型：** string

**起始版本：** 23

<!--Device-InterfaceSharingStateInfo-iface: string--><!--Device-InterfaceSharingStateInfo-iface: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetSharing

**系统接口：** 此接口为系统接口。

## state

```TypeScript
state: SharingIfaceState
```

网卡共享状态。

**类型：** [SharingIfaceState](arkts-network-sharing-sharingifacestate-e-sys.md)

**起始版本：** 23

<!--Device-InterfaceSharingStateInfo-state: SharingIfaceState--><!--Device-InterfaceSharingStateInfo-state: SharingIfaceState-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetSharing

**系统接口：** 此接口为系统接口。

## type

```TypeScript
type: SharingIfaceType
```

网络共享类型。

**类型：** [SharingIfaceType](arkts-network-sharing-sharingifacetype-e-sys.md)

**起始版本：** 23

<!--Device-InterfaceSharingStateInfo-type: SharingIfaceType--><!--Device-InterfaceSharingStateInfo-type: SharingIfaceType-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetSharing

**系统接口：** 此接口为系统接口。

