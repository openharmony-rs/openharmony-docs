# VerifyCredentialOptions

表示用于验证凭据的选项。

**起始版本：** 23

<!--Device-appAccount-interface VerifyCredentialOptions--><!--Device-appAccount-interface VerifyCredentialOptions-End-->

**系统能力：** SystemCapability.Account.AppAccount

## 导入模块

```TypeScript
import { appAccount } from '@kit.BasicServicesKit';
```

## credential

```TypeScript
credential?: string
```

凭据取值，默认为空。

**类型：** string

**起始版本：** 23

<!--Device-VerifyCredentialOptions-credential?: string--><!--Device-VerifyCredentialOptions-credential?: string-End-->

**系统能力：** SystemCapability.Account.AppAccount

## credentialType

```TypeScript
credentialType?: string
```

凭据类型，默认为空。

**类型：** string

**起始版本：** 23

<!--Device-VerifyCredentialOptions-credentialType?: string--><!--Device-VerifyCredentialOptions-credentialType?: string-End-->

**系统能力：** SystemCapability.Account.AppAccount

## parameters

```TypeScript
parameters?: Record<string, RecordData>
```

自定义参数对象，默认为空。

**类型：** Record&lt;string, [RecordData](arkts-basicservices-recorddata-t.md)&gt;

**起始版本：** 23

<!--Device-VerifyCredentialOptions-parameters?: Record<string, RecordData>--><!--Device-VerifyCredentialOptions-parameters?: Record<string, RecordData>-End-->

**系统能力：** SystemCapability.Account.AppAccount

