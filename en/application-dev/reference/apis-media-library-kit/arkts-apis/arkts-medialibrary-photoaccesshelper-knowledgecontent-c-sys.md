# KnowledgeContent (System API)

```TypeScript
class KnowledgeContent
```

Knowledge Content class, used for geting related entity.

**Since:** 23

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## getRelatedEntity

```TypeScript
static getRelatedEntity (topic: string, context: ContextMap, option?: Options): Promise<Entity[]>
```

Get Related Entities, Smart Label

**Since:** 23

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| topic | string | Yes | Searching topic string. |
| context | [ContextMap](arkts-medialibrary-photoaccesshelper-contextmap-i-sys.md) | Yes | Context Map indicates topic filed. |
| option | [Options](arkts-medialibrary-photoaccesshelper-options-i-sys.md) | No | Options for getRelatedEntity. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Entity](arkts-medialibrary-photoaccesshelper-entity-i-sys.md)[]&gt; | Returns Array of Related Entities |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by nonsystem application |
| 13900020 | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

## getSearchResult

```TypeScript
static getSearchResult(query: SearchQuery): Promise<SearchResult>
```

Searches media assets based on the provided query. This API uses a promise to return the result.

**Since:** 26.0.1

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| query | [SearchQuery](arkts-medialibrary-photoaccesshelper-searchquery-i-sys.md) | Yes | Search query configuration. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SearchResult](arkts-medialibrary-photoaccesshelper-searchresult-i-sys.md)&gt; | Promise used to return the search result containing matching assets. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes:<br>1. Invalid input data format. <br>2. The length of **queryString** or **param** in **SearchQuery** exceeds 16KB. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. Possible causes:<br>1. IPC timeout; <br>2. System exception. |

## getSearchSuggestion

```TypeScript
static getSearchSuggestion( searchSuggestionTypes: Array<SearchSuggestionType>): Promise<Array<SearchSuggestionResult>>
```

Get Search Suggestion.

**Since:** 26.0.0

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchSuggestionTypes | Array&lt;[SearchSuggestionType](arkts-medialibrary-photoaccesshelper-searchsuggestiontype-e-sys.md)&gt; | Yes | Array of search suggestion types<br>The maximum length is 7 and cannot be empty. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[SearchSuggestionResult](arkts-medialibrary-photoaccesshelper-searchsuggestionresult-i-sys.md)&gt;&gt; | Result of searching for recommended words |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by nonsystem application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Scenario parameters fail to pass the verification.Possible causes:<br>1. The searchSuggestionTypes list is empty. <br>2. The searchSuggestionTypes error. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
