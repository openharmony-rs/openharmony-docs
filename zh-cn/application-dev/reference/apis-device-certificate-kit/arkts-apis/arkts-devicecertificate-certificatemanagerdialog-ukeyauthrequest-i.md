# UkeyAuthRequest

USB Key PIN码认证请求。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-certificateManagerDialog-export interface UkeyAuthRequest--><!--Device-certificateManagerDialog-export interface UkeyAuthRequest-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## keyUri

```TypeScript
keyUri: string
```

表示USB Key证书凭据的唯一标识符，长度限制256字节以内。 该参数值可通过调用[openAuthorizeDialog]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口返回的CertReference中获取。

**类型：** string

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UkeyAuthRequest-keyUri: string--><!--Device-UkeyAuthRequest-keyUri: string-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

