# ToneHapticsAttrs

系统铃音的振动属性。在调用ToneHapticsAttrs\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_14+\_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_的接口前，需要先通过 [getToneHapticsList]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_或 [getHapticsAttrsSyncedWithTone]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_方法获取实例。

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-systemSoundManager-interface ToneHapticsAttrs--><!--Device-systemSoundManager-interface ToneHapticsAttrs-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

## getFileName

```TypeScript
getFileName(): string
```

获取振动文件名。

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-ToneHapticsAttrs-getFileName(): string--><!--Device-ToneHapticsAttrs-getFileName(): string-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

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

## getGentleFileName

```TypeScript
getGentleFileName(): string | null
```

获取柔和振动文件名。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-ToneHapticsAttrs-getGentleFileName(): string | null--><!--Device-ToneHapticsAttrs-getGentleFileName(): string | null-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

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

## getGentleTitle

```TypeScript
getGentleTitle(): string | null
```

获取柔和振动标题。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-ToneHapticsAttrs-getGentleTitle(): string | null--><!--Device-ToneHapticsAttrs-getGentleTitle(): string | null-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

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

## getGentleUri

```TypeScript
getGentleUri(): string | null
```

获取柔和振动资源路径。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-ToneHapticsAttrs-getGentleUri(): string | null--><!--Device-ToneHapticsAttrs-getGentleUri(): string | null-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 柔和振动的uri（如：'/data/storage/el2/base/haptics/synchronized/alarms/test.json'）。 如果不存在柔和振动， |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |

**示例：**

```TypeScript
toneHapticsAttrs.getGentleUri();
```

## getTitle

```TypeScript
getTitle(): string
```

获取振动标题。

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-ToneHapticsAttrs-getTitle(): string--><!--Device-ToneHapticsAttrs-getTitle(): string-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

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

## getUri

```TypeScript
getUri(): string
```

获取振动资源路径。

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-ToneHapticsAttrs-getUri(): string--><!--Device-ToneHapticsAttrs-getUri(): string-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

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

