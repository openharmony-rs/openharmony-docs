# genPrivacyTarget

## 导入模块

```TypeScript
```

## genPrivacyTarget

```TypeScript
function genPrivacyTarget(targetElement: TargetElement, privacyProtocol: PrivacyProtocol): Promise<Uint8Array>
```

为给定元素生成隐私目标。隐私目标是加密的表示的搜索元素，可以用于保护隐私的搜索，而不会泄露原始数据。

**起始版本：** 26.1.0

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetElement | [TargetElement](arkts-dataprotection-privacycomputation-targetelement-i.md) | 是 | 要搜索的元素，包括其原始数据和可选的散列算法。 |
| privacyProtocol | [PrivacyProtocol](arkts-dataprotection-privacycomputation-privacyprotocol-i.md) | 是 | 隐私协议配置，包括数据集大小和协议类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise用于返回加密结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24000006](../../apis-asset-store-kit/errorcode-asset.md#24000006-系统内存不足) | Insufficient memory. |
| [24000018](../../apis-asset-store-kit/errorcode-asset.md#24000018-参数校验失败) | Parameter verification failed. |
