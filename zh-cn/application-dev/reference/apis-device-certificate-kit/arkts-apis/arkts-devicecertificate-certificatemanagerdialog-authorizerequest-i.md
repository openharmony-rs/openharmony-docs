# AuthorizeRequest

证书凭据授权请求信息。

**起始版本：** 22

<!--Device-certificateManagerDialog-export interface AuthorizeRequest--><!--Device-certificateManagerDialog-export interface AuthorizeRequest-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## 导入模块

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## certPurpose

```TypeScript
certPurpose?: certificateManager.CertificatePurpose
```

表示证书用途。若certTypes参数中存在CertificateType.CREDENTIAL_UKEY类型，则certPurpose参数生效，表示根据指定的证书用途筛选USB Key的证书凭据。

**类型：** certificateManager.CertificatePurpose

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthorizeRequest-certPurpose?: certificateManager.CertificatePurpose--><!--Device-AuthorizeRequest-certPurpose?: certificateManager.CertificatePurpose-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## certTypes

```TypeScript
certTypes: Array<CertificateType>
```

表示证书类型的列表。

**类型：** Array<CertificateType>

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthorizeRequest-certTypes: Array<CertificateType>--><!--Device-AuthorizeRequest-certTypes: Array<CertificateType>-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## issuers

```TypeScript
issuers?: Array<Uint8Array>
```

表示以DER格式编码的证书颁发者，用于筛选凭据授权对话框中的证书列表，仅显示匹配的证书。

如果issuers数组中存在长度为0的元素，则issuers筛选器不会生效。

数组最大长度为20。

26.0.0

**类型：** Array<Uint8Array>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthorizeRequest-issuers?: Array<Uint8Array>--><!--Device-AuthorizeRequest-issuers?: Array<Uint8Array>-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## keyAlgIDs

```TypeScript
keyAlgIDs?: Array<string>
```

表示证书公钥的算法类型，用于筛选凭据授权对话框中的证书列表，仅显示匹配的证书。支持的取值为RSA、EC或ECDSA（区分大小写）。若不传此参数，则不按算法类型筛选证书。若 keyAlgIDs包含不支持的算法，则该筛选器无效。最大长度为20，26.0.0。

**类型：** Array<string>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthorizeRequest-keyAlgIDs?: Array<string>--><!--Device-AuthorizeRequest-keyAlgIDs?: Array<string>-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## uri

```TypeScript
uri?: string
```

该URI在授权对话框中进行显示，用于为用户提供更多有关申请授权使用证书凭据的上下文。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthorizeRequest-uri?: string--><!--Device-AuthorizeRequest-uri?: string-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

