# Transliterator

提供文本音译相关的能力，包括音译支持范围获取和文本音译等。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-i18n-export class Transliterator--><!--Device-i18n-export class Transliterator-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
```

## getAvailableIDs

```TypeScript
static getAvailableIDs(): string[]
```

获取音译支持的转换ID列表。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Transliterator-static getAvailableIDs(): string[]--><!--Device-Transliterator-static getAvailableIDs(): string[]-End-->

**系统能力：** SystemCapability.Global.I18n

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string[] | 音译支持的转换ID列表。 |

## getInstance

```TypeScript
static getInstance(id: string): Transliterator
```

创建指定转换ID的音译对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Transliterator-static getInstance(id: string): Transliterator--><!--Device-Transliterator-static getInstance(id: string): Transliterator-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 音译支持的转换ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Transliterator](arkts-na-i18n-transliterator-c.md) | 音译对象。 |

## transform

```TypeScript
transform(text: string): string
```

将输入文本从源格式转换为目标格式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Transliterator-transform(text: string): string--><!--Device-Transliterator-transform(text: string): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 输入文本。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 转换后的文本。 |

