# connectSystemChannel（系统接口）

## connectSystemChannel

```TypeScript
function connectSystemChannel(): Promise<void>
```

连接面板和输入法之间的系统通道。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CONNECT_IME_ABILITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-inputMethodSystemPanelManager-function connectSystemChannel(): Promise<void>--><!--Device-inputMethodSystemPanelManager-function connectSystemChannel(): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 返回的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permissions check fails. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application. |
| [12800008](../../apis-ime-kit/errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible causes:a system error, such as null pointer, IPC exception. |
| [12800026](../../apis-ime-kit/errorcode-inputmethod-framework.md#12800026-输入法系统面板错误) | input method system panel error. Possible causes:1. the system panel not connected. 2. ipc failed due to the large amount of data transferred or other reasons.3. the caller is not system panel. |

