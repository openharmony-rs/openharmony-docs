# DialogPresenter

提供统一的对话框接口。

**起始版本：** 26.1.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.1.0。

<!--Device-unnamed-export class DialogPresenter--><!--Device-unnamed-export class DialogPresenter-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## dismiss

```TypeScript
dismiss(target: int | ComponentContent<Object>): Promise<void>
```

Dismisses a dialog box. Accepts either the dialog ID (returned by present) or the ComponentContent reference.

**起始版本：** 26.1.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DialogPresenter-dismiss(target: int | ComponentContent<Object>): Promise<void>--><!--Device-DialogPresenter-dismiss(target: int | ComponentContent<Object>): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | int \| ComponentContent&lt;Object&gt; | 是 | The dialog ID or ComponentContent to dismiss. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103301](../../apis-arkui/errorcode-promptAction.md#103301-自定义弹窗内容节点错误) | Dialog content error. The ComponentContent is incorrect. |
| [103303](../../apis-arkui/errorcode-promptAction.md#103303-无法找到内容节点对应的自定义弹窗) | Dialog content not found. The ComponentContent cannot be found. |

## present

```TypeScript
present(options?: dialog.DialogStyleOptions): Promise<DialogResult>
```

Presents a fixed-style dialog box.

**起始版本：** 26.1.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DialogPresenter-present(options?: dialog.DialogStyleOptions): Promise<DialogResult>--><!--Device-DialogPresenter-present(options?: dialog.DialogStyleOptions): Promise<DialogResult>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | dialog.DialogStyleOptions | 否 | Dialog options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[DialogResult](../../apis-arkui/arkts-apis/arkts-arkui-arkui-dialog-dialogresult-i.md)&gt; | Promise used to return the dialog result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103306](../../apis-arkui/errorcode-promptAction.md#103306-节点挂载失败导致无法打开弹出框) | The dialog cannot be opened due to node mount failure. |
| [103308](../../apis-arkui/errorcode-promptAction.md#103308-子窗口创建失败导致无法打开弹出框) | The dialog cannot be opened due to subwindow create failure. |

## present

```TypeScript
present(content: CustomBuilder | CustomBuilderWithId | ComponentContent<Object>, options?: dialog.DialogCustomOptions): Promise<DialogResult>
```

Presents a custom-style dialog box with the provided content. content参数支持CustomBuilder或ComponentContent联合类型： - CustomBuilder: Builder function for custom dialog content. - ComponentContent: ComponentContent supporting state-driven updates. isModal = true and showInSubWindow = true cannot be used at the same time.

**起始版本：** 26.1.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DialogPresenter-present(content: CustomBuilder | CustomBuilderWithId | ComponentContent<Object>, options?: dialog.DialogCustomOptions): Promise<DialogResult>--><!--Device-DialogPresenter-present(content: CustomBuilder | CustomBuilderWithId | ComponentContent<Object>, options?: dialog.DialogCustomOptions): Promise<DialogResult>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | CustomBuilder \| [CustomBuilderWithId](arkts-na-custombuilderwithid-t.md) \| ComponentContent&lt;Object&gt; | 是 | Custom dialog content. |
| options | dialog.DialogCustomOptions | 否 | Custom dialog options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[DialogResult](../../apis-arkui/arkts-apis/arkts-arkui-arkui-dialog-dialogresult-i.md)&gt; | Promise used to return the dialog result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103301](../../apis-arkui/errorcode-promptAction.md#103301-自定义弹窗内容节点错误) | Dialog content error. The ComponentContent is incorrect. |
| [103302](../../apis-arkui/errorcode-promptAction.md#103302-内容节点对应自定义弹窗已存在) | Dialog content already exist. The ComponentContent has already been opened. |
| [103306](../../apis-arkui/errorcode-promptAction.md#103306-节点挂载失败导致无法打开弹出框) | The dialog cannot be opened due to node mount failure. |
| [103308](../../apis-arkui/errorcode-promptAction.md#103308-子窗口创建失败导致无法打开弹出框) | The dialog cannot be opened due to subwindow create failure. |

## update

```TypeScript
update(content: ComponentContent<Object>, options?: dialog.DialogBaseOptions): Promise<void>
```

Updates a presented custom dialog box.

**起始版本：** 26.1.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DialogPresenter-update(content: ComponentContent<Object>, options?: dialog.DialogBaseOptions): Promise<void>--><!--Device-DialogPresenter-update(content: ComponentContent<Object>, options?: dialog.DialogBaseOptions): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent&lt;Object&gt; | 是 | The content used to identify the dialog. |
| options | dialog.DialogBaseOptions | 否 | Options to update. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103301](../../apis-arkui/errorcode-promptAction.md#103301-自定义弹窗内容节点错误) | Dialog content error. The ComponentContent is incorrect. |
| [103303](../../apis-arkui/errorcode-promptAction.md#103303-无法找到内容节点对应的自定义弹窗) | Dialog content not found. The ComponentContent cannot be found. |

