# CmsRecipientInfo

```TypeScript
interface CmsRecipientInfo
```

Represents recipient information for the CMS message.

> **NOTE:** 
> 
> At least one recipient needs to be set.

**Since:** 22

<!--Device-cert-interface CmsRecipientInfo--><!--Device-cert-interface CmsRecipientInfo-End-->

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## keyAgreeInfo

```TypeScript
keyAgreeInfo?: CmsKeyAgreeRecipientInfo
```

KeyAgree recipient information.

**Type:** [CmsKeyAgreeRecipientInfo](arkts-devicecertificate-cert-cmskeyagreerecipientinfo-i.md)

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-CmsRecipientInfo-keyAgreeInfo?: CmsKeyAgreeRecipientInfo--><!--Device-CmsRecipientInfo-keyAgreeInfo?: CmsKeyAgreeRecipientInfo-End-->

**System capability:** SystemCapability.Security.Cert

## keyTransInfo

```TypeScript
keyTransInfo?: CmsKeyTransRecipientInfo
```

KeyTrans recipient information.

**Type:** [CmsKeyTransRecipientInfo](arkts-devicecertificate-cert-cmskeytransrecipientinfo-i.md)

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-CmsRecipientInfo-keyTransInfo?: CmsKeyTransRecipientInfo--><!--Device-CmsRecipientInfo-keyTransInfo?: CmsKeyTransRecipientInfo-End-->

**System capability:** SystemCapability.Security.Cert
