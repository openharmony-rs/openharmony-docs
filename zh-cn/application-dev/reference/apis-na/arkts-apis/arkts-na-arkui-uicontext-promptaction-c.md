# PromptAction

创建并显示即时反馈、对话框、操作菜单以及自定义弹窗。 > **说明：** > > - 本Class首批接口从API version 10开始支持。 > > - 以下API需先使用UIContext中的[getPromptAction()](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#getPromptAction)方法获取到PromptAction对 > 象，再通过该对象调用对应方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class PromptAction--><!--Device-unnamed-export declare class PromptAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## closeCustomDialog

```TypeScript
closeCustomDialog<T extends Object>(dialogContent: ComponentContent<T>): Promise<void>
```

关闭已弹出的dialogContent对应的自定义弹窗，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptAction-closeCustomDialog<T extends Object>(dialogContent: ComponentContent<T>): Promise<void>--><!--Device-PromptAction-closeCustomDialog<T extends Object>(dialogContent: ComponentContent<T>): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dialogContent | ComponentContent&lt;T&gt; | 是 | 自定义弹窗中显示的组件内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |
| [103301](../../apis-arkui/errorcode-promptAction.md#103301-自定义弹窗内容节点错误) | The ComponentContent is incorrect. |
| [103303](../../apis-arkui/errorcode-promptAction.md#103303-无法找到内容节点对应的自定义弹窗) | The ComponentContent cannot be found. |

## closeCustomDialog

```TypeScript
closeCustomDialog(dialogId: int): void
```

关闭自定义弹窗。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptAction-closeCustomDialog(dialogId: int): void--><!--Device-PromptAction-closeCustomDialog(dialogId: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dialogId | int | 是 | openCustomDialog返回的对话框id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../../apis-arkui/errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

## closeMenu

```TypeScript
closeMenu<T extends Object>(content: ComponentContent<T>): Promise<void>
```

关闭content对应的Menu弹窗。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptAction-closeMenu<T extends Object>(content: ComponentContent<T>): Promise<void>--><!--Device-PromptAction-closeMenu<T extends Object>(content: ComponentContent<T>): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent&lt;T&gt; | 是 | menu弹窗中显示的组件内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |
| [103301](../../apis-arkui/errorcode-promptAction.md#103301-自定义弹窗内容节点错误) | The ComponentContent is incorrect. |
| [103303](../../apis-arkui/errorcode-promptAction.md#103303-无法找到内容节点对应的自定义弹窗) | The ComponentContent cannot be found. |

## closePopup

```TypeScript
closePopup<T extends Object>(content: ComponentContent<T>): Promise<void>
```

关闭content对应的Popup弹窗，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptAction-closePopup<T extends Object>(content: ComponentContent<T>): Promise<void>--><!--Device-PromptAction-closePopup<T extends Object>(content: ComponentContent<T>): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent&lt;T&gt; | 是 | popup弹窗中显示的组件内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |
| [103301](../../apis-arkui/errorcode-promptAction.md#103301-自定义弹窗内容节点错误) | The ComponentContent is incorrect. |
| [103303](../../apis-arkui/errorcode-promptAction.md#103303-无法找到内容节点对应的自定义弹窗) | The ComponentContent cannot be found. |

## closeToast

```TypeScript
closeToast(toastId: int): void
```

关闭即时反馈。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptAction-closeToast(toastId: int): void--><!--Device-PromptAction-closeToast(toastId: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| toastId | int | 是 | openToast返回的id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../../apis-arkui/errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |
| [103401](../../apis-arkui/errorcode-promptAction.md#103401-无法找到对应的文本提示框) | Cannot find the toast. |

## getBottomOrder

```TypeScript
getBottomOrder(): LevelOrder | undefined
```

获取最底层显示的弹窗的顺序，可以在下一个弹窗时指定期望的顺序。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptAction-getBottomOrder(): LevelOrder | undefined--><!--Device-PromptAction-getBottomOrder(): LevelOrder | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LevelOrder](arkts-na-promptaction-levelorder-c.md) | 返回弹窗层级信息。 |

## getTopOrder

```TypeScript
getTopOrder(): LevelOrder | undefined
```

返回最顶层显示的弹窗的顺序。 获取最顶层显示的弹窗的顺序，可以在下一个弹窗时指定期望的顺序。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptAction-getTopOrder(): LevelOrder | undefined--><!--Device-PromptAction-getTopOrder(): LevelOrder | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LevelOrder](arkts-na-promptaction-levelorder-c.md) | 返回弹窗层级信息。 |

## openCustomDialog

```TypeScript
openCustomDialog<T extends Object>(dialogContent: ComponentContent<T>, options?: promptAction.BaseDialogOptions): Promise<void>
```

创建并弹出dialogContent对应的自定义弹窗，使用Promise异步回调。 通过该接口弹出的弹窗内容样式完全按照dialogContent中设置的样式显示，即相当于customDialog设置customStyle为true时的显示效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptAction-openCustomDialog<T extends Object>(dialogContent: ComponentContent<T>, options?: promptAction.BaseDialogOptions): Promise<void>--><!--Device-PromptAction-openCustomDialog<T extends Object>(dialogContent: ComponentContent<T>, options?: promptAction.BaseDialogOptions): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dialogContent | ComponentContent&lt;T&gt; | 是 | 自定义弹窗中显示的组件内容。 |
| options | promptAction.BaseDialogOptions | 否 | 弹窗样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |
| [103301](../../apis-arkui/errorcode-promptAction.md#103301-自定义弹窗内容节点错误) | The ComponentContent is incorrect. |
| [103302](../../apis-arkui/errorcode-promptAction.md#103302-内容节点对应自定义弹窗已存在) | Dialog content already exists. |

## openCustomDialog

```TypeScript
openCustomDialog(options: promptAction.CustomDialogOptions): Promise<int>
```

打开自定义对话框。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptAction-openCustomDialog(options: promptAction.CustomDialogOptions): Promise<int>--><!--Device-PromptAction-openCustomDialog(options: promptAction.CustomDialogOptions): Promise<int>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | promptAction.CustomDialogOptions | 是 | 自定义弹窗的内容。 &lt;br&gt;**说明：** 如果BaseDialogOptions中的isModal 与showInSubWindow同时设置为true， 则只生效showInSubWindow = true，此时为非模态弹出框且不会显示蒙层，并在子窗口中显示。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象。返回对话框id，可供closeCustomDialog使用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../../apis-arkui/errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

## openCustomDialogWithController

```TypeScript
openCustomDialogWithController<T extends Object>(dialogContent: ComponentContent<T>, controller: promptAction.DialogController,
    options?: promptAction.BaseDialogOptions): Promise<void>
```

创建并弹出dialogContent对应的自定义弹窗，使用Promise异步回调。支持传入弹窗控制器与自定义弹窗绑定，后续可以通过控制器控制自定义弹窗。 通过该接口弹出的弹窗内容样式完全按照dialogContent中设置的样式显示，即相当于customDialog设置customStyle为true时的显示效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptAction-openCustomDialogWithController<T extends Object>(dialogContent: ComponentContent<T>, controller: promptAction.DialogController,    options?: promptAction.BaseDialogOptions): Promise<void>--><!--Device-PromptAction-openCustomDialogWithController<T extends Object>(dialogContent: ComponentContent<T>, controller: promptAction.DialogController,    options?: promptAction.BaseDialogOptions): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dialogContent | ComponentContent&lt;T&gt; | 是 | 自定义弹窗中显示的组件内容。 |
| controller | promptAction.DialogController | 是 | 自定义弹窗的控制器。 |
| options | promptAction.BaseDialogOptions | 否 | 自定义弹窗的样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |
| [103301](../../apis-arkui/errorcode-promptAction.md#103301-自定义弹窗内容节点错误) | The ComponentContent is incorrect. |
| [103302](../../apis-arkui/errorcode-promptAction.md#103302-内容节点对应自定义弹窗已存在) | Dialog content already exists. |

## openMenu

```TypeScript
openMenu<T extends Object>(content: ComponentContent<T>, target: TargetInfo, options?: MenuOptions): Promise<void>
```

创建并弹出以content作为内容的Menu弹窗。使用Promise异步回调。 > **说明：** > > - 使用该接口时，若未传入有效的target，则无法弹出menu弹窗。 > > - 由于[updateMenu](../../../reference/apis-arkui/arkts-apis-uicontext-promptaction copy.md#updateMenu)和 > [closeMenu](../../../reference/apis-arkui/arkts-apis-uicontext-promptaction copy.md#closeMenu)依赖content去更新或者关闭指定 > 的menu弹窗，开发者需自行维护传入的content。 > > - 如果在wrapBuilder中包含其他组件（例如：Popup、[Chip](arkts-na-arkui-advanced-chip-chip-f.md#Chip)组件），则 > [ComponentContent](arkts-na-componentcontent-c.md#ComponentContent)应采用带有四个参数的构造函数constructor，其中options参数应传递{ > nestingBuilderSupported: true }。 > > - 子窗弹窗里不能再弹出子窗弹窗，例如[openMenu](../../../reference/apis-arkui/arkts-apis-uicontext-promptaction copy.md#openMenu)设 > 置了showInSubWindow为true时，则不能再弹出另一个设置了showInSubWindow为true的弹窗。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptAction-openMenu<T extends Object>(content: ComponentContent<T>, target: TargetInfo, options?: MenuOptions): Promise<void>--><!--Device-PromptAction-openMenu<T extends Object>(content: ComponentContent<T>, target: TargetInfo, options?: MenuOptions): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent&lt;T&gt; | 是 | menu弹窗中显示的组件内容。 |
| target | [TargetInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-targetinfo-i.md) | 是 | 需要绑定组件的信息。 |
| options | [MenuOptions](arkts-na-common-menuoptions-i.md) | 否 | menu弹窗样式。&lt;br/&gt;**说明：**&lt;br/&gt;title属性不生效。&lt;br/&gt;preview参数仅支持设置MenuPreviewMode类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |
| [103301](../../apis-arkui/errorcode-promptAction.md#103301-自定义弹窗内容节点错误) | The content is incorrect. |
| [103302](../../apis-arkui/errorcode-promptAction.md#103302-内容节点对应自定义弹窗已存在) | The content already exists. |
| [103305](../../apis-arkui/errorcode-promptAction.md#103305-指定的targetid对应的节点未挂载在组件树上) | The target node is not in the component tree. |
| [103304](../../apis-arkui/errorcode-promptAction.md#103304-指定的targetid不存在) | The target does not exist. |

## openPopup

```TypeScript
openPopup<T extends Object>(content: ComponentContent<T>, target: TargetInfo, options?: PopupCommonOptions): Promise<void>
```

创建并弹出以content作为内容的Popup弹窗，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptAction-openPopup<T extends Object>(content: ComponentContent<T>, target: TargetInfo, options?: PopupCommonOptions): Promise<void>--><!--Device-PromptAction-openPopup<T extends Object>(content: ComponentContent<T>, target: TargetInfo, options?: PopupCommonOptions): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent&lt;T&gt; | 是 | popup弹窗中显示的组件内容。 |
| target | [TargetInfo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-targetinfo-i.md) | 是 | 需要绑定组件的信息。 |
| options | [PopupCommonOptions](arkts-na-common-popupcommonoptions-i.md) | 否 | popup弹窗样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |
| [103301](../../apis-arkui/errorcode-promptAction.md#103301-自定义弹窗内容节点错误) | The content is incorrect. |
| [103302](../../apis-arkui/errorcode-promptAction.md#103302-内容节点对应自定义弹窗已存在) | The content already exists. |
| [103305](../../apis-arkui/errorcode-promptAction.md#103305-指定的targetid对应的节点未挂载在组件树上) | The target node is not in the component tree. |
| [103304](../../apis-arkui/errorcode-promptAction.md#103304-指定的targetid不存在) | The target does not exist. |

## openToast

```TypeScript
openToast(options: promptAction.ShowToastOptions): Promise<int>
```

显示即时反馈。使用Promise异步回调返回即时反馈的id，可供closeToast使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptAction-openToast(options: promptAction.ShowToastOptions): Promise<int>--><!--Device-PromptAction-openToast(options: promptAction.ShowToastOptions): Promise<int>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | promptAction.ShowToastOptions | 是 | Toast选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象。返回即时反馈的id，可供closeToast使用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../../apis-arkui/errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

## presentCustomDialog

```TypeScript
presentCustomDialog(builder: CustomBuilder | CustomBuilderT<int>, controller?: promptAction.DialogController, options?: promptAction.DialogOptions): Promise<int>
```

创建并弹出自定义弹窗。使用Promise异步回调返回对话框的id，可供closeCustomDialog使用。支持在自定义弹窗内容中持有弹窗ID进行对应操作。支持传入弹窗控制器与自定义弹窗绑定，后续可以通过控制器控制自定义弹窗。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptAction-presentCustomDialog(builder: CustomBuilder | CustomBuilderT<int>, controller?: promptAction.DialogController, options?: promptAction.DialogOptions): Promise<int>--><!--Device-PromptAction-presentCustomDialog(builder: CustomBuilder | CustomBuilderT<int>, controller?: promptAction.DialogController, options?: promptAction.DialogOptions): Promise<int>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | CustomBuilder \| CustomBuilderT&lt;int&gt; | 是 | 自定义弹窗的内容。 |
| controller | promptAction.DialogController | 否 | 自定义弹窗的控制器。 |
| options | promptAction.DialogOptions | 否 | 自定义弹窗的样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象。返回自定义弹窗ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../../apis-arkui/errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

## showActionMenu

```TypeScript
showActionMenu(options: promptAction.ActionMenuOptions, callback: AsyncCallback<promptAction.ActionMenuSuccessResponse>): void
```

创建并显示操作菜单，菜单响应结果使用callback异步回调返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptAction-showActionMenu(options: promptAction.ActionMenuOptions, callback: AsyncCallback<promptAction.ActionMenuSuccessResponse>): void--><!--Device-PromptAction-showActionMenu(options: promptAction.ActionMenuOptions, callback: AsyncCallback<promptAction.ActionMenuSuccessResponse>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | promptAction.ActionMenuOptions | 是 | 操作菜单选项。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;promptAction.ActionMenuSuccessResponse&gt; | 是 | 回调函数。 弹出操作菜单成功，err为undefined，data为获取到的操作菜单响应结果，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../../apis-arkui/errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

## showActionMenu

```TypeScript
showActionMenu(options: promptAction.ActionMenuOptions): Promise<promptAction.ActionMenuSuccessResponse>
```

显示操作菜单。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptAction-showActionMenu(options: promptAction.ActionMenuOptions): Promise<promptAction.ActionMenuSuccessResponse>--><!--Device-PromptAction-showActionMenu(options: promptAction.ActionMenuOptions): Promise<promptAction.ActionMenuSuccessResponse>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | promptAction.ActionMenuOptions | 是 | 操作菜单选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;promptAction.ActionMenuSuccessResponse&gt; | Promise对象，返回菜单的响应结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../../apis-arkui/errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

## showDialog

```TypeScript
showDialog(options: promptAction.ShowDialogOptions, callback: AsyncCallback<promptAction.ShowDialogSuccessResponse>): void
```

创建并显示对话框，对话框响应结果使用callback异步回调返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptAction-showDialog(options: promptAction.ShowDialogOptions, callback: AsyncCallback<promptAction.ShowDialogSuccessResponse>): void--><!--Device-PromptAction-showDialog(options: promptAction.ShowDialogOptions, callback: AsyncCallback<promptAction.ShowDialogSuccessResponse>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | promptAction.ShowDialogOptions | 是 | 页面显示对话框信息描述。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;promptAction.ShowDialogSuccessResponse&gt; | 是 | 回调函数。 弹出对话框成功，err为undefined，data为获取到的对话框响应结果，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../../apis-arkui/errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

## showDialog

```TypeScript
showDialog(options: promptAction.ShowDialogOptions): Promise<promptAction.ShowDialogSuccessResponse>
```

弹出对话框。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptAction-showDialog(options: promptAction.ShowDialogOptions): Promise<promptAction.ShowDialogSuccessResponse>--><!--Device-PromptAction-showDialog(options: promptAction.ShowDialogOptions): Promise<promptAction.ShowDialogSuccessResponse>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | promptAction.ShowDialogOptions | 是 | 对话框选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;promptAction.ShowDialogSuccessResponse&gt; | Promise对象，返回对话框的响应结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../../apis-arkui/errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

## showToast

```TypeScript
showToast(options: promptAction.ShowToastOptions): void
```

创建并显示即时反馈。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptAction-showToast(options: promptAction.ShowToastOptions): void--><!--Device-PromptAction-showToast(options: promptAction.ShowToastOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | promptAction.ShowToastOptions | 是 | Toast选项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../../apis-arkui/errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

## updateCustomDialog

```TypeScript
updateCustomDialog<T extends Object>(dialogContent: ComponentContent<T>, options: promptAction.BaseDialogOptions): Promise<void>
```

更新已弹出的dialogContent对应的自定义弹窗的样式，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptAction-updateCustomDialog<T extends Object>(dialogContent: ComponentContent<T>, options: promptAction.BaseDialogOptions): Promise<void>--><!--Device-PromptAction-updateCustomDialog<T extends Object>(dialogContent: ComponentContent<T>, options: promptAction.BaseDialogOptions): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dialogContent | ComponentContent&lt;T&gt; | 是 | 自定义弹窗中显示的组件内容。 |
| options | promptAction.BaseDialogOptions | 是 | 弹窗样式，目前仅支持更新alignment、offset、autoCancel、maskColor。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |
| [103301](../../apis-arkui/errorcode-promptAction.md#103301-自定义弹窗内容节点错误) | The ComponentContent is incorrect. |
| [103303](../../apis-arkui/errorcode-promptAction.md#103303-无法找到内容节点对应的自定义弹窗) | The ComponentContent cannot be found. |

## updateMenu

```TypeScript
updateMenu<T extends Object>(content: ComponentContent<T>, options: MenuOptions, partialUpdate?: boolean): Promise<void>
```

更新content对应的Menu弹窗的样式。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptAction-updateMenu<T extends Object>(content: ComponentContent<T>, options: MenuOptions, partialUpdate?: boolean): Promise<void>--><!--Device-PromptAction-updateMenu<T extends Object>(content: ComponentContent<T>, options: MenuOptions, partialUpdate?: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent&lt;T&gt; | 是 | menu弹窗中显示的组件内容。 |
| options | [MenuOptions](arkts-na-common-menuoptions-i.md) | 是 | menu弹窗样式。 |
| partialUpdate | boolean | 否 | menu弹窗更新方式，默认值为false。 true为增量更新，保留当前值，更新options中的指定属性。 false为全量更新，除options中的指定属性，其他属性恢复默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |
| [103301](../../apis-arkui/errorcode-promptAction.md#103301-自定义弹窗内容节点错误) | The ComponentContent is incorrect. |
| [103303](../../apis-arkui/errorcode-promptAction.md#103303-无法找到内容节点对应的自定义弹窗) | The ComponentContent cannot be found. |

## updatePopup

```TypeScript
updatePopup<T extends Object>(content: ComponentContent<T>, options: PopupCommonOptions, partialUpdate?: boolean): Promise<void>
```

更新content对应的Popup弹窗的样式，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptAction-updatePopup<T extends Object>(content: ComponentContent<T>, options: PopupCommonOptions, partialUpdate?: boolean): Promise<void>--><!--Device-PromptAction-updatePopup<T extends Object>(content: ComponentContent<T>, options: PopupCommonOptions, partialUpdate?: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent&lt;T&gt; | 是 | popup弹窗中显示的组件内容。 |
| options | [PopupCommonOptions](arkts-na-common-popupcommonoptions-i.md) | 是 | popup弹窗样式。 |
| partialUpdate | boolean | 否 | popup弹窗更新方式，默认值为false。 true：增量更新，此时更新options中的指定属性，其它属性保留当前值。 false：全量更新，此时更新options中的指定属性，并且其他属性恢复默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |
| [103301](../../apis-arkui/errorcode-promptAction.md#103301-自定义弹窗内容节点错误) | The ComponentContent is incorrect. |
| [103303](../../apis-arkui/errorcode-promptAction.md#103303-无法找到内容节点对应的自定义弹窗) | The ComponentContent cannot be found. |

