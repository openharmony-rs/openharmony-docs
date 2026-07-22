# ToneAttrs（系统接口）

管理铃声属性。在调用ToneAttrs<sup>12+</sup>的接口前，需要先通过[createCustomizedToneAttrs](arkts-audio-systemsoundmanager-createcustomizedtoneattrs-f-sys.md#createcustomizedtoneattrs)或[getDefaultRingtoneAttrs](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#getdefaultringtoneattrs)、[getRingtoneAttrList](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#getringtoneattrlist)等方法获取实例。

**起始版本：** 12

<!--Device-systemSoundManager-interface ToneAttrs--><!--Device-systemSoundManager-interface ToneAttrs-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { systemSoundManager } from '@kit.AudioKit';
```

## getCategory

```TypeScript
getCategory(): number
```

获取铃声类别。

**起始版本：** 12

<!--Device-ToneAttrs-getCategory(): int--><!--Device-ToneAttrs-getCategory(): int-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 铃声类别，取值参考[铃声类别的常量](#常量)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

**示例：**

```TypeScript
toneAttrs.getCategory();

```

## getCustomizedType

```TypeScript
getCustomizedType(): ToneCustomizedType
```

获取铃声自定义类型。

**起始版本：** 12

<!--Device-ToneAttrs-getCustomizedType(): ToneCustomizedType--><!--Device-ToneAttrs-getCustomizedType(): ToneCustomizedType-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ToneCustomizedType](arkts-audio-systemsoundmanager-tonecustomizedtype-e-sys.md) | 定制铃音类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

**示例：**

```TypeScript
toneAttrs.getCustomizedType();

```

## getFileName

```TypeScript
getFileName(): string
```

获取铃声文件名。

**起始版本：** 12

<!--Device-ToneAttrs-getFileName(): string--><!--Device-ToneAttrs-getFileName(): string-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 文件名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

**示例：**

```TypeScript
toneAttrs.getFileName();

```

## getMediaType

```TypeScript
getMediaType():MediaType
```

获取铃声类型。

**起始版本：** 20

<!--Device-ToneAttrs-getMediaType():MediaType--><!--Device-ToneAttrs-getMediaType():MediaType-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaType](../../apis-media-kit/arkts-apis/arkts-media-multimedia-media-mediatype-e.md) | 媒体类型，如果应用未调用过setMediaType设置mediatype，则此函数返回的默认值为AUDIO。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

**示例：**

```TypeScript
toneAttrs.getMediaType();

```

## getTitle

```TypeScript
getTitle(): string
```

获取铃声标题。

**起始版本：** 12

<!--Device-ToneAttrs-getTitle(): string--><!--Device-ToneAttrs-getTitle(): string-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 标题。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

**示例：**

```TypeScript
toneAttrs.getTitle();

```

## getUri

```TypeScript
getUri(): string
```

获取铃声资源路径。

**起始版本：** 12

<!--Device-ToneAttrs-getUri(): string--><!--Device-ToneAttrs-getUri(): string-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | uri（如：'/data/storage/el2/base/RingTone/alarms/test.ogg'）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

**示例：**

```TypeScript
toneAttrs.getUri();

```

## setCategory

```TypeScript
setCategory(category: number): void
```

设置铃声类别。

**起始版本：** 12

<!--Device-ToneAttrs-setCategory(category: int): void--><!--Device-ToneAttrs-setCategory(category: int): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| category | number | 是 | 铃声类别，取值参考[铃声类别的常量](#常量)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

```TypeScript
let toneAttrs = systemSoundManager.createCustomizedToneAttrs();
let categoryValue = systemSoundManager.TONE_CATEGORY_ALARM; // 需更改为实际所需类型常量。
toneAttrs.setCategory(categoryValue);

```

## setFileName

```TypeScript
setFileName(name: string): void
```

设置铃声文件名。

**起始版本：** 12

<!--Device-ToneAttrs-setFileName(name: string): void--><!--Device-ToneAttrs-setFileName(name: string): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 铃声的文件名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

```TypeScript
let toneAttrs = systemSoundManager.createCustomizedToneAttrs();
let fileName = 'textFileName';
toneAttrs.setFileName(fileName);

```

## setMediaType

```TypeScript
setMediaType(type:MediaType):void
```

设置铃声类型。

**起始版本：** 20

<!--Device-ToneAttrs-setMediaType(type:MediaType):void--><!--Device-ToneAttrs-setMediaType(type:MediaType):void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [MediaType](../../apis-media-kit/arkts-apis/arkts-media-multimedia-media-mediatype-e.md) | 是 | 媒体类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

**示例：**

```TypeScript
let type: systemSoundManager.MediaType = systemSoundManager.MediaType.VIDEO; // 需更改为实际所需类型。
let toneAttrs = systemSoundManager.createCustomizedToneAttrs();
toneAttrs.setMediaType(type);

```

## setTitle

```TypeScript
setTitle(title: string): void
```

设置铃声标题。

**起始版本：** 12

<!--Device-ToneAttrs-setTitle(title: string): void--><!--Device-ToneAttrs-setTitle(title: string): void-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| title | string | 是 | 铃声的标题。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

```TypeScript
let toneAttrs = systemSoundManager.createCustomizedToneAttrs();
let title = 'text';
toneAttrs.setTitle(title);

```

