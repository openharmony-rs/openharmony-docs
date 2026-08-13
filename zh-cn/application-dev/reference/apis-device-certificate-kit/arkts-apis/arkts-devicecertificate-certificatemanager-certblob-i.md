# CertBlob

表示证书文件数据。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-certificateManager-export interface CertBlob--><!--Device-certificateManager-export interface CertBlob-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## certData

```TypeScript
certData: Uint8Array
```

表示证书文件数据。当certFormat传入PEM_DER，最大长度为8KB。当certFormat传入P7B，最大长度为300KB。

**类型：** Uint8Array

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CertBlob-certData: Uint8Array--><!--Device-CertBlob-certData: Uint8Array-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## certFormat

```TypeScript
certFormat? : CertFileFormat
```

表示证书文件格式。 默认值：PEM_DER。

**类型：** [CertFileFormat](arkts-devicecertificate-certificatemanager-certfileformat-e.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CertBlob-certFormat? : CertFileFormat--><!--Device-CertBlob-certFormat? : CertFileFormat-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## certScope

```TypeScript
certScope? : CertScope
```

表示用户CA证书的存储位置。 默认值：CURRENT_USER。

**类型：** [CertScope](arkts-devicecertificate-certificatemanager-certscope-e.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CertBlob-certScope? : CertScope--><!--Device-CertBlob-certScope? : CertScope-End-->

**系统能力：** SystemCapability.Security.CertificateManager

