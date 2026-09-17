# CmsGeneratorOptions

Represents the configuration for generating a CMS message.

**Since:** 18

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## contentDataFormat

```TypeScript
contentDataFormat?: CmsContentDataFormat
```

Format of the content. The default value is **CmsContentDataFormat.BINARY**.

**Type:** [CmsContentDataFormat](arkts-devicecertificate-cert-cmscontentdataformat-e.md)

**Default:** CmsContentDataFormat.BINARY

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Security.Cert

## isDetached

```TypeScript
isDetached?: boolean
```

Whether the final CMS message does not contain the raw data. The default value is **false**. **true**: raw data is not contained; **false**: raw data is contained.

**Type:** boolean

**Default:** false

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Security.Cert

## outFormat

```TypeScript
outFormat?: CmsFormat
```

Format of the CMS message generated. The default value is **DER**.

**Type:** [CmsFormat](arkts-devicecertificate-cert-cmsformat-e.md)

**Default:** CmsFormat.DER

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Security.Cert
