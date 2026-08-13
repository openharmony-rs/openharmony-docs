# CmsKeyAgreeRecipientInfo

CMS封装数据的KeyAgree接收方信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-cert-interface CmsKeyAgreeRecipientInfo--><!--Device-cert-interface CmsKeyAgreeRecipientInfo-End-->

**系统能力：** SystemCapability.Security.Cert

## cert

```TypeScript
cert: X509Cert
```

EC证书。

**类型：** [X509Cert](arkts-devicecertificate-cert-x509cert-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CmsKeyAgreeRecipientInfo-cert: X509Cert--><!--Device-CmsKeyAgreeRecipientInfo-cert: X509Cert-End-->

**系统能力：** SystemCapability.Security.Cert

## digestAlgorithm

```TypeScript
digestAlgorithm?: CmsKeyAgreeRecipientDigestAlgorithm
```

KDF摘要算法，默认为SHA256。

**类型：** [CmsKeyAgreeRecipientDigestAlgorithm](arkts-devicecertificate-cert-cmskeyagreerecipientdigestalgorithm-e.md)

**默认值：** CmsKeyAgreeRecipientDigestAlgorithm.SHA256

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CmsKeyAgreeRecipientInfo-digestAlgorithm?: CmsKeyAgreeRecipientDigestAlgorithm--><!--Device-CmsKeyAgreeRecipientInfo-digestAlgorithm?: CmsKeyAgreeRecipientDigestAlgorithm-End-->

**系统能力：** SystemCapability.Security.Cert

