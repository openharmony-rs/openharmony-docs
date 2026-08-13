# PrivateKeyInfo

表示私钥信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-cert-interface PrivateKeyInfo--><!--Device-cert-interface PrivateKeyInfo-End-->

**系统能力：** SystemCapability.Security.Cert

## key

```TypeScript
key: string | Uint8Array
```

未加密或加密的私钥，支持PEM或DER格式。

**类型：** string \| Uint8Array

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PrivateKeyInfo-key: string | Uint8Array--><!--Device-PrivateKeyInfo-key: string | Uint8Array-End-->

**系统能力：** SystemCapability.Security.Cert

## password

```TypeScript
password?: string
```

私钥的密码，如果私钥是加密的。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PrivateKeyInfo-password?: string--><!--Device-PrivateKeyInfo-password?: string-End-->

**系统能力：** SystemCapability.Security.Cert

