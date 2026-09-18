# privacySearch

## 导入模块

```TypeScript
```

## privacySearch

```TypeScript
function privacySearch(privacyTarget: Uint8Array, elements: Element[], privacyProtocol: PrivacyProtocol):
        Promise<PrivacySearchResult>
```

执行隐私保护搜索。根据加密的隐私目标搜索给定的数据集元素而不向对方透露目标或数据集内容。

**起始版本：** 26.1.0

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| privacyTarget | Uint8Array | 是 | 用genPrivateTarget生成的加密隐私目标。 |
| elements | [Element](arkts-dataprotection-privacycomputation-element-i.md)[] | 是 | 要搜索的数据集元素。 |
| privacyProtocol | [PrivacyProtocol](arkts-dataprotection-privacycomputation-privacyprotocol-i.md) | 是 | 隐私协议配置，包括数据集大小和协议类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PrivacySearchResult](arkts-dataprotection-privacycomputation-privacysearchresult-i.md)&gt; | 用于返回隐私搜索结果的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24000006](../../apis-asset-store-kit/errorcode-asset.md#24000006-系统内存不足) | Insufficient memory. |
| [24000018](../../apis-asset-store-kit/errorcode-asset.md#24000018-参数校验失败) | Parameter verification failed. |
