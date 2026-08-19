# Normalizer

提供文本标准化的能力。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-i18n-export class Normalizer--><!--Device-i18n-export class Normalizer-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
```

## getInstance

```TypeScript
static getInstance(mode: NormalizerMode): Normalizer
```

获取文本标准化对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Normalizer-static getInstance(mode: NormalizerMode): Normalizer--><!--Device-Normalizer-static getInstance(mode: NormalizerMode): Normalizer-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [NormalizerMode](arkts-na-i18n-normalizermode-e.md) | 是 | 文本标准化范式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Normalizer](arkts-na-i18n-normalizer-c.md) | 返回指定范式的文本标准化对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

## normalize

```TypeScript
normalize(text: string): string
```

对字符串进行标准化处理。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Normalizer-normalize(text: string): string--><!--Device-Normalizer-normalize(text: string): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 输入文本。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 标准化处理后的字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

