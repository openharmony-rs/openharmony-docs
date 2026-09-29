# PlainText

```TypeScript
interface PlainText
```

Represents data of the plain text type.

**Since:** 12

<!--Device-uniformDataStruct-interface PlainText--><!--Device-uniformDataStruct-interface PlainText-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## abstract

```TypeScript
abstract?: string
```

Text abstract. It is an empty string by default.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-PlainText-abstract?: string--><!--Device-PlainText-abstract?: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## details

```TypeScript
details?: Record<string, string>
```

Object of the dictionary type used to describe the attributes of the text content. Both the key and value of the object are of the string type. For example, the following is a **details** object used to describe the properties of a file:

{

"title":"Title of the file",

"content":"Content of the file"

}

By default, it is an empty dictionary object.

**Type:** Record&lt;string, string&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-PlainText-details?: Record<string, string>--><!--Device-PlainText-details?: Record<string, string>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## textContent

```TypeScript
textContent: string
```

Plaintext content.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-PlainText-textContent: string--><!--Device-PlainText-textContent: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## uniformDataType

```TypeScript
readonly uniformDataType: 'general.plain-text'
```

Uniform data type, which has a fixed value of **general.plain-text**. For details, see [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md).

**Type:** 'general.plain-text'

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-PlainText-readonly uniformDataType: 'general.plain-text'--><!--Device-PlainText-readonly uniformDataType: 'general.plain-text'-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
