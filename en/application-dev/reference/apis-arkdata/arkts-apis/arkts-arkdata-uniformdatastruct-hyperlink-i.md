# Hyperlink

```TypeScript
interface Hyperlink
```

Defines the hyperlink typed data, which is used to describe and manage hyperlink information. After a Hyperlink object is created, it can be used in scenarios such as drag-and-drop and sharing to implement cross-application hyperlink data transfer and redirection.

**Since:** 12

<!--Device-uniformDataStruct-interface Hyperlink--><!--Device-uniformDataStruct-interface Hyperlink-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## description

```TypeScript
description?: string
```

Description of the link content. This is an optional field. Pass this parameter when a text description needs to be provided for the hyperlink (for example, for accessibility, link preview, and other scenarios). If it is not passed, the default value is an empty string, and no description information is provided.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-Hyperlink-description?: string--><!--Device-Hyperlink-description?: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## details

```TypeScript
details?: Record<string, string>
```

Dictionary type object whose keys and values are all of the string type. It is used to describe the detailed attribute content of Hyperlink. This is an optional field, and the default value is an empty dictionary object. For example, a data object whose details content is

{

"title":"Title of the file",

"content":"Content of the file"

}

By default, it is an empty dictionary object.

**Type:** Record&lt;string, string&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-Hyperlink-details?: Record<string, string>--><!--Device-Hyperlink-details?: Record<string, string>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## uniformDataType

```TypeScript
readonly uniformDataType: 'general.hyperlink'
```

Uniform data type, which has a fixed value of **general.hyperlink**. For details, see [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md).

**Type:** 'general.hyperlink'

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-Hyperlink-readonly uniformDataType: 'general.hyperlink'--><!--Device-Hyperlink-readonly uniformDataType: 'general.hyperlink'-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## url

```TypeScript
url: string
```

URL of the link. It supports protocols such as http and https and must conform to the standard URL format. For example, `https://www.example.com` or `file:///path/to/file`.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-Hyperlink-url: string--><!--Device-Hyperlink-url: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
