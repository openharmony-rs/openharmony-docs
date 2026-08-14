# showDialog

## showDialog

```TypeScript
function showDialog(options: ShowDialogOptions, callback: AsyncCallback<ShowDialogSuccessResponse>): void
```

创建并显示对话框，对话框响应结果使用callback异步回调返回。 > **说明：** > > - 从API version 9开始支持，从API version 18开始废弃，建议使用showDialog替代。 showDialog需先通过[UIContext](arkts-apis-uicontext-uicontext.md)中的 [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getPromptAction)方法获取[PromptAction](arkts-apis-uicontext-promptaction.md)对象， 然后通过该对象进行调用。且直接使用showDialog可能导致[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的问题。 > > - 从API version 10开始，可以通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的 [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getPromptAction)方法获取当前UI上下文关联的 [PromptAction](arkts-apis-uicontext-promptaction.md)对象。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 18

**替代接口：** showDialog

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-promptAction-function showDialog(options: ShowDialogOptions, callback: AsyncCallback<ShowDialogSuccessResponse>): void--><!--Device-promptAction-function showDialog(options: ShowDialogOptions, callback: AsyncCallback<ShowDialogSuccessResponse>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | ShowDialogOptions | 是 | 页面显示对话框信息描述。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;ShowDialogSuccessResponse&gt; | 是 | 回调函数。弹出对话框成功时，err为undefined， data为获取到的对话框响应结果；失败时，err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |


## showDialog

```TypeScript
function showDialog(options: ShowDialogOptions): Promise<ShowDialogSuccessResponse>
```

创建并显示对话框，对话框通过Promise返回结果。 > **说明：** > > - 从API version 9开始支持，从API version 18开始废弃，建议使用showDialog替代。 showDialog需先通过[UIContext](arkts-apis-uicontext-uicontext.md)中的 [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getPromptAction)方法获取[PromptAction](arkts-apis-uicontext-promptaction.md)对象， 然后通过该对象进行调用。且直接使用showDialog可能导致[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的问题。 > > - 从API version 10开始，可以通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的 [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getPromptAction)方法获取当前UI上下文关联的 [PromptAction](arkts-apis-uicontext-promptaction.md)对象。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 18

**替代接口：** showDialog

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-promptAction-function showDialog(options: ShowDialogOptions): Promise<ShowDialogSuccessResponse>--><!--Device-promptAction-function showDialog(options: ShowDialogOptions): Promise<ShowDialogSuccessResponse>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | ShowDialogOptions | 是 | 对话框选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ShowDialogSuccessResponse&gt; | Promise对象，返回对话框的响应结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

