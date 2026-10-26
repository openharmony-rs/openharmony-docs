# AddCredentialInfo

```TypeScript
export interface AddCredentialInfo
```

添加凭证信息

**起始版本：** 26.0.1

<!--Device-securityManager-export interface AddCredentialInfo--><!--Device-securityManager-export interface AddCredentialInfo-End-->

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

<!--Device-AddCredentialInfo-authToken?: Uint8Array--><!--Device-AddCredentialInfo-authToken?: Uint8Array-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## pluginInfo

```TypeScript
pluginInfo: string
```

认证插件信息。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AddCredentialInfo-pluginInfo: string--><!--Device-AddCredentialInfo-pluginInfo: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager
