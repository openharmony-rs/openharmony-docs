# ServerAuthentication

HTTP服务器身份验证。

**起始版本：** 23

<!--Device-http-export interface ServerAuthentication--><!--Device-http-export interface ServerAuthentication-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { http } from '@kit.NetworkKit';
```

## authenticationType

```TypeScript
authenticationType?: AuthenticationType
```

服务器的认证类型。如果没有设置，需与服务器协商。

**类型：** [AuthenticationType](arkts-network-http-authenticationtype-t.md)

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ServerAuthentication-authenticationType?: AuthenticationType--><!--Device-ServerAuthentication-authenticationType?: AuthenticationType-End-->

**系统能力：** SystemCapability.Communication.NetStack

## credential

```TypeScript
credential: Credential
```

服务器的凭证。默认值为undefined。

**类型：** Credential

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ServerAuthentication-credential: Credential--><!--Device-ServerAuthentication-credential: Credential-End-->

**系统能力：** SystemCapability.Communication.NetStack

