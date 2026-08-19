# GeneralName

表示X.509 GeneralName，定义在RFC 5280中，可出现在Subject Alternative Name等扩展中。

**起始版本：** 23

<!--Device-cert-interface GeneralName--><!--Device-cert-interface GeneralName-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { certificateManager } from '@kit.DeviceCertificateKit';
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## name

```TypeScript
name?: Uint8Array
```

指定GeneralName的DER编码值。

**类型：** Uint8Array

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-GeneralName-name?: Uint8Array--><!--Device-GeneralName-name?: Uint8Array-End-->

**系统能力：** SystemCapability.Security.Cert

## type

```TypeScript
type: GeneralNameType
```

GeneralName类型。

**类型：** [GeneralNameType](arkts-devicecertificate-cert-generalnametype-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-GeneralName-type: GeneralNameType--><!--Device-GeneralName-type: GeneralNameType-End-->

**系统能力：** SystemCapability.Security.Cert

