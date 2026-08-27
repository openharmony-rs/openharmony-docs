# SslType

```TypeScript
export type SslType = 'TLS' | 'TLCP'
```

安全通信协议。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

| 类型 | 说明 |
| --- | --- |
| 'TLS' | 表示使用TLS安全通信协议，值固定为'TLS'字符串。 |
| 'TLCP' | 表示使用TLCP安全通信协议，值固定为'TLCP'字符串。  **说明**：  （1）证书支持字符串的规格：   - UTF8String（英文字符集）   - PrintableString   - IA5String  从API Version 22开始支持：   - TeletexString  （2）证书支持扩展的规格：   - BasicConstraints（OID 2.5.29.19）   - KeyUsage（OID2.5.29.15）   - SubjectKeyIdentifier（OID2.5.29.14）   - AuthorityKeyIdentifier（OID2.5.29.35）  从API Version 22开始支持：   - SubjectAltName（OID 2.5.29.17）   - ExtendedKeyUsage（OID 2.5.29.37） |
