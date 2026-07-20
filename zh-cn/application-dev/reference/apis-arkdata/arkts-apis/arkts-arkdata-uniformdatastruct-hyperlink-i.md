# Hyperlink

超链接类型数据，用于描述和管理超链接信息。创建Hyperlink对象后，可用于拖拽、分享等场景，实现跨应用的超链接数据传递和跳转。

**起始版本：** 12

<!--Device-uniformDataStruct-interface Hyperlink--><!--Device-uniformDataStruct-interface Hyperlink-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## description

```TypeScript
description?: string
```

链接内容描述，非必填字段。当需要为超链接提供文字描述时传入此参数（如用于可访问性、链接预览等场景），不传入时默认值为空字符串，不提供描述信息。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Hyperlink-description?: string--><!--Device-Hyperlink-description?: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## details

```TypeScript
details?: Record<string, string>
```

字典类型对象，key和value均为string类型，用于描述Hyperlink的详细属性内容。非必填字段，默认值为空字典对象。例如，可生成一个details内容为

{

"title":"标题",

"content":"内容"

}

的数据对象。当需要存储额外的超链接属性信息时传入此参数，不传入时默认值为空字典对象，不提供额外属性。

**类型：** Record&lt;string, string&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Hyperlink-details?: Record<string, string>--><!--Device-Hyperlink-details?: Record<string, string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## uniformDataType

```TypeScript
readonly uniformDataType: 'general.hyperlink'
```

统一数据类型标识为超链接类型数据，固定为“general.hyperlink”，数据类型描述信息见[UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)。

**类型：** 'general.hyperlink'

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Hyperlink-readonly uniformDataType: 'general.hyperlink'--><!--Device-Hyperlink-readonly uniformDataType: 'general.hyperlink'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## url

```TypeScript
url: string
```

链接URL地址，支持http、https等协议，需符合标准URL格式。例如：`https://www.example.com`或`file:///path/to/file`。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Hyperlink-url: string--><!--Device-Hyperlink-url: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

