# setDarkMode（系统接口）

## setDarkMode

```TypeScript
function setDarkMode(mode: DarkMode, callback: AsyncCallback<void>): void
```

设置系统深色模式。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-uiAppearance-function setDarkMode(mode: DarkMode, callback: AsyncCallback<void>): void--><!--Device-uiAppearance-function setDarkMode(mode: DarkMode, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.UiAppearance

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [DarkMode](arkts-na-uiappearance-darkmode-e.md) | 是 | indicates the dark-mode to set |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | the callback of setDarkMode |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |
| [500001](../../apis-arkui/errorcode-uiappearance.md#500001-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |


## setDarkMode

```TypeScript
function setDarkMode(mode: DarkMode): Promise<void>
```

设置系统深色模式。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-uiAppearance-function setDarkMode(mode: DarkMode): Promise<void>--><!--Device-uiAppearance-function setDarkMode(mode: DarkMode): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.UiAppearance

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [DarkMode](arkts-na-uiappearance-darkmode-e.md) | 是 | indicates the dark-mode to set |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |
| [500001](../../apis-arkui/errorcode-uiappearance.md#500001-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

