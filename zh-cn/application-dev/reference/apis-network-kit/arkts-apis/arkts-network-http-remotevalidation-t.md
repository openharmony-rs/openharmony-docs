# RemoteValidation

```TypeScript
export type RemoteValidation = 'system' | 'skip' | ValidationCallback
```

验证远程服务器身份的方式。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-http-export type RemoteValidation = 'system' | 'skip' | ValidationCallback--><!--Device-http-export type RemoteValidation = 'system' | 'skip' | ValidationCallback-End-->

**系统能力：** SystemCapability.Communication.NetStack

| 类型 | 说明 |
| --- | --- |
| 'system' | 表示使用系统CA验证远端服务器身份，值固定为'system'字符串，是未配置时的默认值。 |
| 'skip' | 表示跳过验证远端服务器身份流程，值固定为'skip'字符串。 |
| ValidationCallback | 表示使用自定义验证方式验证远端服务器身份。 [since 26.0.0] |

