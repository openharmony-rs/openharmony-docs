# TrustedPairedDevices（系统接口）

```TypeScript
interface TrustedPairedDevices
```

云设备列表。

**起始版本：** 15

<!--Device-connection-interface TrustedPairedDevices--><!--Device-connection-interface TrustedPairedDevices-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## trustedPairedDevices

```TypeScript
trustedPairedDevices: Array<TrustedPairedDevice>
```

表示云设备列表。

**类型：** Array&lt;[TrustedPairedDevice](arkts-connectivity-connection-trustedpaireddevice-i-sys.md)&gt;

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TrustedPairedDevices-trustedPairedDevices: Array<TrustedPairedDevice>--><!--Device-TrustedPairedDevices-trustedPairedDevices: Array<TrustedPairedDevice>-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。
