# CertBlob

证书信息。

**起始版本：** 12

<!--Device-securityManager-export interface CertBlob--><!--Device-securityManager-export interface CertBlob-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## alias

```TypeScript
alias: string
```

证书别名，别名长度小于40个字符。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CertBlob-alias: string--><!--Device-CertBlob-alias: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## inData

```TypeScript
inData: Uint8Array
```

证书的二进制内容。

**类型：** Uint8Array

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CertBlob-inData: Uint8Array--><!--Device-CertBlob-inData: Uint8Array-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

