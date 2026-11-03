# FileUri

```TypeScript
interface FileUri
```

Defines the file URI typed data, which is used to describe the URI address information of a file. After a FileUri object is created, it can be used in scenarios such as file drag-and-drop and file sharing, support controlling file access permissions through uriAuthorizationPolicies, and implement cross-application file data transfer and permission management.

**Since:** 15

<!--Device-uniformDataStruct-interface FileUri--><!--Device-uniformDataStruct-interface FileUri-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## details

```TypeScript
details?: Record<string, number | string | Uint8Array>
```

Dictionary type object. The key is of the string type, and the value can contain data of the number (numeric type), string (string type), or Uint8Array (binary byte array) type. This is an optional field, and the default value is an empty dictionary object.

**Type:** Record&lt;string, number &#124; string &#124; Uint8Array&gt;

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileUri-details?: Record<string, int | long | double | string | Uint8Array>--><!--Device-FileUri-details?: Record<string, int | long | double | string | Uint8Array>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## fileType

```TypeScript
fileType: string
```

The file type must be a standardized data type (that is, the UTD-ID corresponding to each type in the [Prebuilt UTDs](../../../database/uniform-data-type-list.md) or a custom UTD-ID). The maximum length limit of fileType is 1024 bytes. An exception is thrown when the limit is exceeded.

**Type:** string

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileUri-fileType: string--><!--Device-FileUri-fileType: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## oriUri

```TypeScript
oriUri: string
```

Original URI path of the file. Supports local file absolute paths, the file:// protocol, and http/https network URL formats. The length limit is 4096 bytes. For example: `/data/local/tmp/test.txt`, `file:///data/local/tmp/test.txt`, or `http://example.com/file.txt`.

**Type:** string

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileUri-oriUri: string--><!--Device-FileUri-oriUri: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## uniformDataType

```TypeScript
readonly uniformDataType: 'general.file-uri'
```

Uniform data type, which has a fixed value of **general.file-uri**. For details, see [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md).

**Type:** 'general.file-uri'

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileUri-readonly uniformDataType: 'general.file-uri'--><!--Device-FileUri-readonly uniformDataType: 'general.file-uri'-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## uriAuthorizationPolicies

```TypeScript
uriAuthorizationPolicies?: Array<number>
```

URI authorization policy used in drag-and-drop scenarios. The default value is **READ+WRITE+PERSIST** (read + write + persistent authorization). It applies only to a single record and has the highest priority. For details about the policies, see [UriPermission](arkts-arkdata-unifieddatachannel-uripermission-e.md).

**Type:** Array&lt;number&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileUri-uriAuthorizationPolicies?: Array<int>--><!--Device-FileUri-uriAuthorizationPolicies?: Array<int>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
