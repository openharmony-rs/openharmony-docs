# RemoveCredentialInfo

```TypeScript
export interface RemoveCredentialInfo
```

移除凭证信息

**起始版本：** 26.0.1

<!--Device-securityManager-export interface RemoveCredentialInfo--><!--Device-securityManager-export interface RemoveCredentialInfo-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## authToken

```TypeScript
authToken?: Uint8Array
```

认证令牌。

**类型：** Uint8Array

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RemoveCredentialInfo-authToken?: Uint8Array--><!--Device-RemoveCredentialInfo-authToken?: Uint8Array-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## credentialId

```TypeScript
credentialId: Uint8Array
```

凭据ID。

**类型：** Uint8Array

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RemoveCredentialInfo-credentialId: Uint8Array--><!--Device-RemoveCredentialInfo-credentialId: Uint8Array-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager
