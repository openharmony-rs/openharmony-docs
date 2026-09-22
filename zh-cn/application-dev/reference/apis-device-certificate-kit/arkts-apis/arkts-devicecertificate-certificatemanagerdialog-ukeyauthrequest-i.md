# UkeyAuthRequest

```TypeScript
export interface UkeyAuthRequest
```

USB Key PIN码认证请求。

**起始版本：** 22

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## 导入模块

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## customData

```TypeScript
customData?: Uint8Array
```

传入Ukey鉴权对话框的自定义数据。一般情况下，此字段只需要在调用openAuthDialogForUkeyProvider接口时提供。最大长度2048字节。

**类型：** Uint8Array

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## keyUri

```TypeScript
keyUri: string
```

表示USB Key证书凭据的唯一标识符，长度限制256字节以内。该参数值可通过调用[openAuthorizeDialog](arkts-devicecertificate-certificatemanagerdialog-openauthorizedialog-f.md)接口返回的CertReference中获取。

**类型：** string

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## timeoutDuration

```TypeScript
timeoutDuration?: number
```

Ukey认证对话框操作超时时间。单位为：秒。取值应为[180,600]内的整数。默认值：300。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog
