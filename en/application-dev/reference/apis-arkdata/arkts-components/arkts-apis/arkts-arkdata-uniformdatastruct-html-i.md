# HTML

```TypeScript
interface HTML
```

Represents data of the HTML type.

**Since:** 12

<!--Device-uniformDataStruct-interface HTML--><!--Device-uniformDataStruct-interface HTML-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## details

```TypeScript
details?: Record<string, string>
```

Object of the dictionary type used to describe the attributes of the HTML content. Both the key and value of the object are of the string type. For example, the following is a **details** object used to describe the properties of a file:

{

"title":"Title of the file",

"content":"Content of the file"

}

By default, it is an empty dictionary object.

**Type:** Record&lt;string, string&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-HTML-details?: Record<string, string>--><!--Device-HTML-details?: Record<string, string>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## htmlContent

```TypeScript
htmlContent: string
```

Content in HTML format.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-HTML-htmlContent: string--><!--Device-HTML-htmlContent: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## plainContent

```TypeScript
plainContent?: string
```

Plaintext without HTML tags. This parameter is optional. By default, it is an empty string.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-HTML-plainContent?: string--><!--Device-HTML-plainContent?: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## uniformDataType

```TypeScript
readonly uniformDataType: 'general.html'
```

Uniform data type, which has a fixed value of **general.html**. For details, see [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md).

**Type:** 'general.html'

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-HTML-readonly uniformDataType: 'general.html'--><!--Device-HTML-readonly uniformDataType: 'general.html'-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## uriAuthorizationPolicies

```TypeScript
uriAuthorizationPolicies?: Array<number>
```

Defines URI authorization policies for drag intention.

**Type:** Array&lt;number&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-HTML-uriAuthorizationPolicies?: Array<int>--><!--Device-HTML-uriAuthorizationPolicies?: Array<int>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
