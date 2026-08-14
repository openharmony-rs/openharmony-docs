# setFontScale（系统接口）

## setFontScale

```TypeScript
function setFontScale(fontScale: double): Promise<void>
```

设置系统字体大小。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-uiAppearance-function setFontScale(fontScale: double): Promise<void>--><!--Device-uiAppearance-function setFontScale(fontScale: double): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.UiAppearance

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fontScale | double | 是 | indicates the font-scale to set |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [500001](../../apis-arkui/errorcode-uiappearance.md#500001-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

