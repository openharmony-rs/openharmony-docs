# File

```TypeScript
class File extends UnifiedRecord
```

Represents the file data. It is a child class of [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md) and a base class of the data of the file type. You are advised to use the child class of **File**, for example, [Image](arkts-arkdata-unifieddatachannel-image-c.md), [Video](arkts-arkdata-unifieddatachannel-video-c.md), and [Folder](arkts-arkdata-unifieddatachannel-folder-c.md), to describe data.

**Inheritance/Implementation:** File extends [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md)

**Since:** 10

<!--Device-unifiedDataChannel-class File extends UnifiedRecord--><!--Device-unifiedDataChannel-class File extends UnifiedRecord-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## details

```TypeScript
details?: Record<string, string>
```

A dictionary type object, where both the key and value are of the string type and are used to describe file information. For example, a data object with the following content can be created to describe a file:

{

"name":"File name",

"type":"File type"

}

The default value is an empty dictionary object.

**Type:** Record&lt;string, string&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-File-details?: Record<string, string>--><!--Device-File-details?: Record<string, string>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## uri

```TypeScript
get uri(): string
```

Indicates the uri of file

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-File-get uri(): string--><!--Device-File-get uri(): string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set uri(value: string)
```

Indicates the uri of file

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-File-set uri(value: string)--><!--Device-File-set uri(value: string)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## uriAuthorizationPolicies

```TypeScript
set uriAuthorizationPolicies(value: Array<UriPermission> | undefined)
```

Defines URI authorization policies for drag intention.

**Type:** Array&lt;[UriPermission](arkts-arkdata-unifieddatachannel-uripermission-e.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-File-set uriAuthorizationPolicies(value: Array<UriPermission> | undefined)--><!--Device-File-set uriAuthorizationPolicies(value: Array<UriPermission> | undefined)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
