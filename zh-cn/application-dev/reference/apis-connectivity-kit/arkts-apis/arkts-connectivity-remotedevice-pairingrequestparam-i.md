# PairingRequestParam

配对请求参数说明。

**起始版本：** 26.0.0

<!--Device-remoteDevice-interface PairingRequestParam--><!--Device-remoteDevice-interface PairingRequestParam-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address: string
```

设备地址。长度必须为17，由16进制数字和冒号组成，形如 "11:22:33:AA:BB:FF"。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PairingRequestParam-address: string--><!--Device-PairingRequestParam-address: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## pairingType

```TypeScript
pairingType: PairingType
```

配对类型。

**类型：** PairingType

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PairingRequestParam-pairingType: PairingType--><!--Device-PairingRequestParam-pairingType: PairingType-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## passkey

```TypeScript
passkey: string
```

设备配对的密钥。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PairingRequestParam-passkey: string--><!--Device-PairingRequestParam-passkey: string-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

