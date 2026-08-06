# HTML

HTML类型数据，用于描述超文本标记语言数据。创建HTML对象后，可在拖拽、复制粘贴等场景中传递富文本内容，支持跨应用的HTML格式数据交互，并可通过uriAuthorizationPolicies控制URI授权策略。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-uniformDataStruct-interface HTML--><!--Device-uniformDataStruct-interface HTML-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## details

```TypeScript
details?: Record<string, string>
```

字典类型对象，key和value均为string类型，用于描述HTML的详细属性内容。非必填字段，默认值为空字典对象。例如，可生成一个details内容为 { "title":"标题", "content":"内容" } 的数据对象。

**类型：** Record&lt;string, string&gt;

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HTML-details?: Record<string, string>--><!--Device-HTML-details?: Record<string, string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## htmlContent

```TypeScript
htmlContent: string
```

HTML格式的内容文本，支持标准HTML标签。可以是完整的HTML文档或HTML片段。长度限制为20MB。建议使用UTF-8编码。 例如：\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_标题\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_。

**类型：** string

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HTML-htmlContent: string--><!--Device-HTML-htmlContent: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## plainContent

```TypeScript
plainContent?: string
```

去除HTML标签后的纯文本内容，非必填字段。当需要提供HTML内容的纯文本版本时传入此参数（如用于文本搜索、无HTML渲染环境的展示等场景），不传入时默认值为空字符串，不提供纯文本版本。

**类型：** string

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HTML-plainContent?: string--><!--Device-HTML-plainContent?: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## uniformDataType

```TypeScript
readonly uniformDataType: 'general.html'
```

统一数据类型标识为html类型数据，固定为“general.html”，数据类型描述信息见 [UniformDataType]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**类型：** 'general.html'

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HTML-readonly uniformDataType: 'general.html'--><!--Device-HTML-readonly uniformDataType: 'general.html'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## uriAuthorizationPolicies

```TypeScript
uriAuthorizationPolicies?: Array<int>
```

用于拖拽场景的URI授权策略。默认值为READ（仅读授权），仅在img标签等场景下生效。只针对单个record使用，优先级最高，具体策略见 [UriPermission]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**类型：** Array&lt;int&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HTML-uriAuthorizationPolicies?: Array<int>--><!--Device-HTML-uriAuthorizationPolicies?: Array<int>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

