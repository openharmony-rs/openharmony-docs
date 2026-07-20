# ToneHapticsAttrs（系统接口）

系统铃音的振动属性。在调用ToneHapticsAttrs<sup>14+</sup>的接口前，需要先通过[getToneHapticsList](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#gettonehapticslist-1)或[getHapticsAttrsSyncedWithTone](arkts-audio-systemsoundmanager-systemsoundmanager-i-sys.md#gethapticsattrssyncedwithtone-1)方法获取实例。

**起始版本：** 14

<!--Device-systemSoundManager-interface ToneHapticsAttrs--><!--Device-systemSoundManager-interface ToneHapticsAttrs-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { systemSoundManager } from '@kit.AudioKit';
```

<a id="getfilename"></a>
## getFileName

```TypeScript
getFileName(): string
```

获取振动文件名。

**起始版本：** 14

<!--Device-ToneHapticsAttrs-getFileName(): string--><!--Device-ToneHapticsAttrs-getFileName(): string-End-->

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
toneHapticsAttrs.getFileName();

```

<a id="getgentlefilename"></a>
## getGentleFileName

```TypeScript
getGentleFileName(): string | null
```

获取柔和振动文件名。

**起始版本：** 22

<!--Device-ToneHapticsAttrs-getGentleFileName(): string | null--><!--Device-ToneHapticsAttrs-getGentleFileName(): string | null-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 柔和振动文件名，振动文件为Json格式。如果不存在柔和振动，则振动文件名为空。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

**示例：**

```TypeScript
toneHapticsAttrs.getGentleFileName();

```

<a id="getgentletitle"></a>
## getGentleTitle

```TypeScript
getGentleTitle(): string | null
```

获取柔和振动标题。

**起始版本：** 22

<!--Device-ToneHapticsAttrs-getGentleTitle(): string | null--><!--Device-ToneHapticsAttrs-getGentleTitle(): string | null-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 柔和振动的标题。如果不存在柔和振动，则振动标题为空。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

**示例：**

```TypeScript
toneHapticsAttrs.getGentleTitle();

```

<a id="getgentleuri"></a>
## getGentleUri

```TypeScript
getGentleUri(): string | null
```

获取柔和振动资源路径。

**起始版本：** 22

<!--Device-ToneHapticsAttrs-getGentleUri(): string | null--><!--Device-ToneHapticsAttrs-getGentleUri(): string | null-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 柔和振动的uri（如：'/data/storage/el2/base/haptics/synchronized/alarms/test.json'）。 如果不存在柔和振动，则uri为空。 柔和振动是指马达振动强度较标准较弱。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

**示例：**

```TypeScript
toneHapticsAttrs.getGentleUri();

```

<a id="gettitle"></a>
## getTitle

```TypeScript
getTitle(): string
```

获取振动标题。

**起始版本：** 14

<!--Device-ToneHapticsAttrs-getTitle(): string--><!--Device-ToneHapticsAttrs-getTitle(): string-End-->

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
toneHapticsAttrs.getTitle();

```

<a id="geturi"></a>
## getUri

```TypeScript
getUri(): string
```

获取振动资源路径。

**起始版本：** 14

<!--Device-ToneHapticsAttrs-getUri(): string--><!--Device-ToneHapticsAttrs-getUri(): string-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | uri（如：'/data/storage/el2/base/haptics/synchronized/alarms/test.json'）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

**示例：**

```TypeScript
toneHapticsAttrs.getUri();

```

