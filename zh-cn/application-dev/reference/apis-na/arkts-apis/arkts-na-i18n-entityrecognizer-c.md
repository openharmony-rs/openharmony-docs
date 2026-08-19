# EntityRecognizer

提供实体识别相关的能力，可以获取文本中实体的类型和起止位置。当前支持识别的实体包括电话号码和时间日期。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-i18n-export class EntityRecognizer--><!--Device-i18n-export class EntityRecognizer-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(locale?: string)
```

创建实体识别对象。该对象根据区域规则识别文本中的实体。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-EntityRecognizer-constructor(locale?: string)--><!--Device-EntityRecognizer-constructor(locale?: string)-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | string | 否 | [表示区域ID的字符串](../../../internationalization/i18n-locale-culture.md#实现原理)，由语言、脚本、国家地区 组成，例如zh-Hans-CN。 <br>默认值：系统当前区域ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [890001](../../apis-localization-kit/errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

## findEntityInfo

```TypeScript
findEntityInfo(text: string): Array<EntityInfoItem>
```

获取文本中的实体信息。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-EntityRecognizer-findEntityInfo(text: string): Array<EntityInfoItem>--><!--Device-EntityRecognizer-findEntityInfo(text: string): Array<EntityInfoItem>-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 输入文本。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[EntityInfoItem](arkts-na-i18n-entityinfoitem-i.md)&gt; | 文本中的实体信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

