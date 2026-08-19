# AuthenticationType

```TypeScript
export type AuthenticationType = 'basic' | 'ntlm' | 'digest'
```

在会话中的服务器身份验证时可以设置使用不同的身份验证机制。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-http-export type AuthenticationType = 'basic' | 'ntlm' | 'digest'--><!--Device-http-export type AuthenticationType = 'basic' | 'ntlm' | 'digest'-End-->

**系统能力：** SystemCapability.Communication.NetStack

| 类型 | 说明 |
| --- | --- |
| 'basic' | 表示使用基本认证方式，值固定为'basic'字符串。 |
| 'ntlm' | 表示使用ntlm认证方式，值固定为'ntlm'字符串。 |
| 'digest' | 表示使用摘要认证方式，值固定为'digest'字符串。 |

