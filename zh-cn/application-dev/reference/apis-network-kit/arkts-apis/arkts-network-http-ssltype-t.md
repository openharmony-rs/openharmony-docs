# SslType

```TypeScript
export type SslType = 'TLS' | 'TLCP'
```

安全通信协议。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-http-export type SslType = 'TLS' | 'TLCP'--><!--Device-http-export type SslType = 'TLS' | 'TLCP'-End-->

**系统能力：** SystemCapability.Communication.NetStack

| 类型 | 说明 |
| --- | --- |
| 'TLS' | 表示使用TLS安全通信协议，值固定为'TLS'字符串。 |
| 'TLCP' | 表示使用TLCP安全通信协议，值固定为'TLCP'字符串。 <br>**说明**： <br>（1）证书支持字符串的规格： <br> - UTF8String（英文字符集） <br> - PrintableString <br> - IA5String <br>从API Version 22开始支持： <br> - TeletexString <br>（2）证书支持扩展的规格： <br> - BasicConstraints（OID 2.5.29.19） <br> - KeyUsage（OID2.5.29.15） <br> - SubjectKeyIdentifier（OID2.5.29.14） <br> - AuthorityKeyIdentifier（OID2.5.29.35） <br>从API Version 22开始支持： <br> - SubjectAltName（OID 2.5.29.17） <br> - ExtendedKeyUsage（OID 2.5.29.37）<br/> |

