# ContractRequestData（系统接口）

```TypeScript
export interface ContractRequestData
```

加密需要的信息。

**起始版本：** 20

<!--Device-eSIM-export interface ContractRequestData--><!--Device-eSIM-export interface ContractRequestData-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { eSIM } from '@kit.TelephonyKit';
```

## nonce

```TypeScript
nonce: string
```

随机数。

**类型：** string

**起始版本：** 20

<!--Device-ContractRequestData-nonce: string--><!--Device-ContractRequestData-nonce: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## pkid

```TypeScript
pkid: string
```

选择的公钥ID。

**类型：** string

**起始版本：** 20

<!--Device-ContractRequestData-pkid: string--><!--Device-ContractRequestData-pkid: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## publicKey

```TypeScript
publicKey: string
```

公钥。

**类型：** string

**起始版本：** 20

<!--Device-ContractRequestData-publicKey: string--><!--Device-ContractRequestData-publicKey: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。
