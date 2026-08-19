# KnowledgeContent（系统接口）

支持的MIME类型。

**起始版本：** 23

<!--Device-photoAccessHelper-class KnowledgeContent--><!--Device-photoAccessHelper-class KnowledgeContent-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## getRelatedEntity

```TypeScript
static getRelatedEntity (topic: string, context: ContextMap, option?: Options): Promise<Entity[]>
```

返回Smartlabel推荐标签

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KnowledgeContent-static getRelatedEntity (topic: string, context: ContextMap, option?: Options): Promise<Entity[]>--><!--Device-KnowledgeContent-static getRelatedEntity (topic: string, context: ContextMap, option?: Options): Promise<Entity[]>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| topic | string | 是 | Searching topic string. |
| context | [ContextMap](arkts-medialibrary-photoaccesshelper-contextmap-i-sys.md) | 是 | Context Map indicates topic filed. |
| option | Options | 否 | Options for getRelatedEntity. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Entity[]&gt; | 返回推荐标签内容 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by nonsystem application |

## getSearchResult

```TypeScript
static getSearchResult(query: SearchQuery): Promise<SearchResult>
```

根据提供的查询搜索媒资。该接口使用promise返回结果。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KnowledgeContent-static getSearchResult(query: SearchQuery): Promise<SearchResult>--><!--Device-KnowledgeContent-static getSearchResult(query: SearchQuery): Promise<SearchResult>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [SearchQuery](arkts-medialibrary-photoaccesshelper-searchquery-i-sys.md) | 是 | 搜索查询配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;SearchResult&gt; | Promise用于返回包含匹配资产的搜索结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. Possible causes: <br>1. IPC timeout; <br>2. System exception. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. Invalid input data format. <br>2. The length of **queryString** or **param** in **SearchQuery** exceeds 16KB. |

## getSearchSuggestion

```TypeScript
static getSearchSuggestion( searchSuggestionTypes: Array<SearchSuggestionType>): Promise<Array<SearchSuggestionResult>>
```

获取搜索推荐词

**起始版本：** 26.0.0

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KnowledgeContent-static getSearchSuggestion( searchSuggestionTypes: Array<SearchSuggestionType>): Promise<Array<SearchSuggestionResult>>--><!--Device-KnowledgeContent-static getSearchSuggestion( searchSuggestionTypes: Array<SearchSuggestionType>): Promise<Array<SearchSuggestionResult>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| searchSuggestionTypes | Array&lt;[SearchSuggestionType](arkts-medialibrary-photoaccesshelper-searchsuggestiontype-e-sys.md)&gt; | 是 | 搜索推荐词场景类型列表 <br>最大长度为7且不能为空。 <br>The maximum length is 7 and cannot be empty. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[SearchSuggestionResult](arkts-medialibrary-photoaccesshelper-searchsuggestionresult-i-sys.md)&gt;&gt; | 搜索推荐词结果 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by nonsystem application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Scenario parameters fail to pass the verification.Possible causes: <br>1. The searchSuggestionTypes list is empty. <br>2. The searchSuggestionTypes error. |

