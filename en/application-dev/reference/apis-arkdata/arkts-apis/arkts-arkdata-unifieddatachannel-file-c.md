# File

```TypeScript
class File extends UnifiedRecord
```

The File type data is a subclass of [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md) and the base class of file type data. It is used to describe file type data. You are advised to use subclasses of File, such as [Image](arkts-arkdata-unifieddatachannel-image-c.md), [Video](arkts-arkdata-unifieddatachannel-video-c.md), and [Folder](arkts-arkdata-unifieddatachannel-folder-c.md), to describe data.

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

A dictionary object whose keys and values are both of the string type. It is used to describe file-related information. For example, you can create a data object with the following details to describe a file:

{

"name":"file name",

"type":"file type"

}.

This is an optional field, and the default value is an empty dictionary object.

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

URI of a local file or a network file. The URI of a local file can be obtained by calling [getUriFromPath](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md)

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-File-get uri(): string--><!--Device-File-get uri(): string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set uri(value: string)
```

URI of a local file or a network file. The URI of a local file can be obtained by calling [getUriFromPath](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md)

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-File-set uri(value: string)--><!--Device-File-set uri(value: string)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## uriAuthorizationPolicies

```TypeScript
set uriAuthorizationPolicies(value: Array<UriPermission> | undefined)
```

URI authorization policy used in drag-and-drop scenarios. The default value is READ+WRITE+PERSIST (read + write + persistent authorization). It applies only to a single record and has the highest priority. For details about the policies, see [UriPermission](arkts-arkdata-unifieddatachannel-uripermission-e.md).

**Type:** Array&lt;[UriPermission](arkts-arkdata-unifieddatachannel-uripermission-e.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-File-set uriAuthorizationPolicies(value: Array<UriPermission> | undefined)--><!--Device-File-set uriAuthorizationPolicies(value: Array<UriPermission> | undefined)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
