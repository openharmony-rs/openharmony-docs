# GeneralName

用于表示GeneralName。

**起始版本：** 12

<!--Device-cert-interface GeneralName--><!--Device-cert-interface GeneralName-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## name

```TypeScript
name?: Uint8Array
```

指定GeneralName的DER编码值。

**类型：** Uint8Array

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GeneralName-name?: Uint8Array--><!--Device-GeneralName-name?: Uint8Array-End-->

**系统能力：** SystemCapability.Security.Cert

## type

```TypeScript
type: GeneralNameType
```

GeneralName类型。

**类型：** GeneralNameType

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GeneralName-type: GeneralNameType--><!--Device-GeneralName-type: GeneralNameType-End-->

**系统能力：** SystemCapability.Security.Cert

