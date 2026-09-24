# UkeyAuthDialogInfo

```TypeScript
export interface UkeyAuthDialogInfo
```

需要打开的Ukey认证对话框信息。

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## 导入模块

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## abilityName

```TypeScript
abilityName: string
```

Ukey认证对话框的ability名称。最大长度为256字节，且不能为空。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## abilityType

```TypeScript
abilityType: AbilityType
```

Ukey认证对话框的ability类型。

**类型：** [AbilityType](arkts-devicecertificate-certificatemanagerdialog-abilitytype-e.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog
