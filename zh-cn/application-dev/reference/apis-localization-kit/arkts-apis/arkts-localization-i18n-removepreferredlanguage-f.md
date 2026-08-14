# removePreferredLanguage

## removePreferredLanguage

```TypeScript
export function removePreferredLanguage(index: int): boolean
```

从系统偏好语言列表中移除指定位置的偏好语言。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [removePreferredLanguage](arkts-localization-i18n-system-c-sys.md#removePreferredLanguage)

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-i18n-export function removePreferredLanguage(index: int): boolean--><!--Device-i18n-export function removePreferredLanguage(index: int): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待移除偏好语言在系统偏好语言列表中的位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示移除成功，false表示移除失败。 |

