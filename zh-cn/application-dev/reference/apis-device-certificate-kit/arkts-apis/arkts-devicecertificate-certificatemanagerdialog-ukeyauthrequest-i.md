# UkeyAuthRequest

USB Key PIN码认证请求。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-certificateManagerDialog-export interface UkeyAuthRequest--><!--Device-certificateManagerDialog-export interface UkeyAuthRequest-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## keyUri

```TypeScript
keyUri: string
```

表示USB Key证书凭据的唯一标识符，长度限制256字节以内。 该参数值可通过调用[openAuthorizeDialog](arkts-devicecertificate-certificatemanagerdialog-openauthorizedialog-f.md#openAuthorizeDialog)接口返回的CertReference中获取。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UkeyAuthRequest-keyUri: string--><!--Device-UkeyAuthRequest-keyUri: string-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

