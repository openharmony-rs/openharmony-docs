# TlsV13CipherSuite

```TypeScript
export type TlsV13CipherSuite = TlsV12CipherSuite | TlsV13SpecificCipherSuite
```

TLS1.3的加密套件声明函数，支持TLS1.3版本，兼容TLS1.2版本。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-http-export type TlsV13CipherSuite = TlsV12CipherSuite | TlsV13SpecificCipherSuite--><!--Device-http-export type TlsV13CipherSuite = TlsV12CipherSuite | TlsV13SpecificCipherSuite-End-->

**系统能力：** SystemCapability.Communication.NetStack

| 类型 | 说明 |
| --- | --- |
| TlsV12CipherSuite | 表示值的类型为[TlsV11CipherSuite]{ |
| TlsV13SpecificCipherSuite | 表示值的类型为[TlsV13SpecificCipherSuite]{ |

