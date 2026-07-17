# CertBlob（系统接口）

证书信息。

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [CertBlob](arkts-mdm-securitymanager-certblob-i.md)

<!--Device-deviceSettings-export interface CertBlob--><!--Device-deviceSettings-export interface CertBlob-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
```

## alias

```TypeScript
alias: string
```

证书别名，别名长度小于40个字符。

**类型：** string

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** alias

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CertBlob-alias: string--><!--Device-CertBlob-alias: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## inData

```TypeScript
inData: Uint8Array
```

证书的二进制内容。

**类型：** Uint8Array

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** inData

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CertBlob-inData: Uint8Array--><!--Device-CertBlob-inData: Uint8Array-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

