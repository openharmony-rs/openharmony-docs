# getSearchResult

## 导入模块

```TypeScript
```

## getSearchResult

```TypeScript
function getSearchResult(privacySearchResult: PrivacySearchResult, privacyProtocol: PrivacyProtocol):
        Promise<SearchResult>
```

获取隐私搜索结果和最终搜索结果。解密搜索结果密文privateSearch返回，获取最终匹配结果和可选的附加值。

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| privacySearchResult | [PrivacySearchResult](arkts-dataprotection-privacycomputation-privacysearchresult-i.md) | 是 | 隐私搜索返回的结果。 |
| privacyProtocol | [PrivacyProtocol](arkts-dataprotection-privacycomputation-privacyprotocol-i.md) | 是 | 隐私协议配置，包括数据集大小和协议类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[SearchResult](arkts-dataprotection-privacycomputation-searchresult-i.md)&gt; | Promise用于返回searchResult。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24000006](../../apis-asset-store-kit/errorcode-asset.md#24000006-系统内存不足) | Insufficient memory. |
| [24000018](../../apis-asset-store-kit/errorcode-asset.md#24000018-参数校验失败) | Parameter verification failed. |
