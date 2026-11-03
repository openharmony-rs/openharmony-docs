# HTML

```TypeScript
interface HTML
```

Defines the HTML typed data, which is used to describe HyperText Markup Language data. After an HTML object is created, it can be used to transfer rich text content in scenarios such as drag-and-drop and copy-paste, support cross-application HTML format data interaction, and control the URI authorization policy through **uriAuthorizationPolicies**.

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

Object of dictionary type, where both the key and value are of string type, used to describe the detailed attribute content of the HTML. This is an optional field, and the default value is an empty dictionary object. For example, a data object can be generated with the details content as

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

Content text in HTML format, supporting standard HTML tags. It can be a complete HTML document or an HTML fragment. The length limit is 20 MB. UTF-8 encoding is recommended. For example: \<div>\<p> title &lt;\/p&gt;&lt;\/div&gt;.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-HTML-htmlContent: string--><!--Device-HTML-htmlContent: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## plainContent

```TypeScript
plainContent?: string
```

Plain text content after removing HTML tags. This is an optional field. Pass this parameter when a plain text version of the HTML content is required (for example, for text search, display in environments without HTML rendering, and other scenarios). If not passed, the default value is an empty string, and no plain text version is provided.

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

URI authorization policy for drag-and-drop scenarios. The default value is READ (read-only authorization), which takes effect only in scenarios such as the img tag. It applies only to a single record and has the highest priority. For details about the policy, see [UriPermission](arkts-arkdata-unifieddatachannel-uripermission-e.md).

**Type:** Array&lt;number&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-HTML-uriAuthorizationPolicies?: Array<int>--><!--Device-HTML-uriAuthorizationPolicies?: Array<int>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
