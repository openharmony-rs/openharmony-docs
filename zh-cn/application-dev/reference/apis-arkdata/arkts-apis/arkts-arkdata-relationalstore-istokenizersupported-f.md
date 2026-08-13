# isTokenizerSupported

## isTokenizerSupported

```TypeScript
function isTokenizerSupported(tokenizer: Tokenizer): boolean
```

判断当前平台是否支持传入的分词器，此为同步接口。 如果当前平台支持传入的分词器时，此接口返回值为true；反之，返回值为false。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-relationalStore-function isTokenizerSupported(tokenizer: Tokenizer): boolean--><!--Device-relationalStore-function isTokenizerSupported(tokenizer: Tokenizer): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenizer | [Tokenizer](arkts-arkdata-relationalstore-tokenizer-e.md) | 是 | 需要被判断是否支持的分词器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示当前平台支持当前传入的分词器，false表示当前平台不支持当前传入的分词器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |

## 示例

```TypeScript
let customType = relationalStore.Tokenizer.CUSTOM_TOKENIZER;
let customTypeSupported = relationalStore.isTokenizerSupported(customType);
console.info("custom tokenizer supported on current platform: " + customTypeSupported);
```

