# generateRandomUUID

## 导入模块

```TypeScript
```

## generateRandomUUID

```TypeScript
function generateRandomUUID(entropyCache?: boolean): string
```

使用加密安全的随机数生成器生成随机的RFC 4122版本4 UUID。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-util-function generateRandomUUID(entropyCache?: boolean): string--><!--Device-util-function generateRandomUUID(entropyCache?: boolean): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| entropyCache | boolean | 否 | 是否使用缓存生成UUID。默认值：true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回表示此UUID的字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 参数错误。可能的原因：1.参数类型不正确。 |

