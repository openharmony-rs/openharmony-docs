# CmsRecipientInfo

Represents recipient information for the CMS message.

> **NOTE:** 
> 
> At least one recipient needs to be set.

**Since:** 22

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

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Security.Cert

## keyTransInfo

```TypeScript
keyTransInfo?: CmsKeyTransRecipientInfo
```

KeyTrans recipient information.

**Type:** [CmsKeyTransRecipientInfo](arkts-devicecertificate-cert-cmskeytransrecipientinfo-i.md)

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Security.Cert
