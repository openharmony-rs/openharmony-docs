# TlsOptions

```TypeScript
export type TlsOptions = 'system' | TlsConfig
```

TLS配置。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-http-export type TlsOptions = 'system' | TlsConfig--><!--Device-http-export type TlsOptions = 'system' | TlsConfig-End-->

**系统能力：** SystemCapability.Communication.NetStack

| 类型 | 说明 |
| --- | --- |
| 'system' | 表示使用系统的TLS版本，是未进行TLS设置的默认值，值固定为'system'字符串。 |
| TlsConfig | 表示使用自定义的TLS版本号和加密套件。 |

