# CertificateScope

表示安装证书的使用范围。

**起始版本：** 14

<!--Device-certificateManagerDialog-export enum CertificateScope--><!--Device-certificateManagerDialog-export enum CertificateScope-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## NOT_SPECIFIED

```TypeScript
NOT_SPECIFIED = 0
```

不指定使用范围，用户可在证书安装界面选择。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CertificateScope-NOT_SPECIFIED = 0--><!--Device-CertificateScope-NOT_SPECIFIED = 0-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## CURRENT_USER

```TypeScript
CURRENT_USER = 1
```

当前用户。表示证书仅对当前登录用户可用。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CertificateScope-CURRENT_USER = 1--><!--Device-CertificateScope-CURRENT_USER = 1-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## GLOBAL_USER

```TypeScript
GLOBAL_USER = 2
```

所有用户。表示证书对设备的所有用户可见。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CertificateScope-GLOBAL_USER = 2--><!--Device-CertificateScope-GLOBAL_USER = 2-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

