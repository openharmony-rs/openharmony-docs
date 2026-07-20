# PlainText

纯文本类型数据，用于描述和管理纯文本内容。创建PlainText对象后，可用于拖拽、复制粘贴等数据共享场景，实现跨应用的纯文本数据交互。

**起始版本：** 12

<!--Device-uniformDataStruct-interface PlainText--><!--Device-uniformDataStruct-interface PlainText-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## abstract

```TypeScript
abstract?: string
```

纯文本摘要，非必填字段。当需要为文本提供简短摘要时传入此参数（如用于预览、搜索结果展示等场景），不传入时默认值为空字符串，不提供摘要信息。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PlainText-abstract?: string--><!--Device-PlainText-abstract?: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## details

```TypeScript
details?: Record<string, string>
```

字典类型对象，key和value均为string类型，用于描述文本内容详细属性。非必填字段，默认值为空字典对象。例如，可生成一个details内容为

{

"title":"标题",

"content":"内容"

}

的数据对象。当需要存储额外的文本属性信息时传入此参数，不传入时默认值为空字典对象，不提供额外属性。

**类型：** Record&lt;string, string&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PlainText-details?: Record<string, string>--><!--Device-PlainText-details?: Record<string, string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## textContent

```TypeScript
textContent: string
```

纯文本内容。长度限制为20MB。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PlainText-textContent: string--><!--Device-PlainText-textContent: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## uniformDataType

```TypeScript
readonly uniformDataType: 'general.plain-text'
```

统一数据类型标识为纯文本类型数据，固定为“general.plain-text”，数据类型描述信息见[UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)。

**类型：** 'general.plain-text'

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PlainText-readonly uniformDataType: 'general.plain-text'--><!--Device-PlainText-readonly uniformDataType: 'general.plain-text'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

