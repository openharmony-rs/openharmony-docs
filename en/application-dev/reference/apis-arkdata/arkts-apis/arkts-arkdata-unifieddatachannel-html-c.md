# HTML

```TypeScript
class HTML extends Text
```

The HTML type data, a subclass of [Text](arkts-arkdata-unifieddatachannel-text-c.md), is used to describe HyperText Markup Language data.

**Inheritance/Implementation:** HTML extends [Text](arkts-arkdata-unifieddatachannel-text-c.md)

**Since:** 10

<!--Device-unifiedDataChannel-class HTML extends Text--><!--Device-unifiedDataChannel-class HTML extends Text-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## htmlContent

```TypeScript
get htmlContent(): string
```

Content in HTML format.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HTML-get htmlContent(): string--><!--Device-HTML-get htmlContent(): string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set htmlContent(value: string)
```

Content in HTML format.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HTML-set htmlContent(value: string)--><!--Device-HTML-set htmlContent(value: string)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## plainContent

```TypeScript
plainContent?: string
```

Plain text content after HTML tags are removed. This is an optional field, and the default value is an empty string.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HTML-plainContent?: string--><!--Device-HTML-plainContent?: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## uriAuthorizationPolicies

```TypeScript
set uriAuthorizationPolicies(value: Array<UriPermission> | undefined)
```

URI authorization policy used in drag-and-drop scenarios. The default value is READ (read-only authorization), which takes effect only in scenarios such as the img tag. It applies only to a single record and has the highest priority. For details about the policies, see [UriPermission](arkts-arkdata-unifieddatachannel-uripermission-e.md).

**Type:** Array&lt;[UriPermission](arkts-arkdata-unifieddatachannel-uripermission-e.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-HTML-set uriAuthorizationPolicies(value: Array<UriPermission> | undefined)--><!--Device-HTML-set uriAuthorizationPolicies(value: Array<UriPermission> | undefined)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
