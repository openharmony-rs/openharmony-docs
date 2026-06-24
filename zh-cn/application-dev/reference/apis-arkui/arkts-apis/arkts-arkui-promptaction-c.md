# PromptAction

创建并显示即时反馈、对话框、操作菜单以及自定义弹窗。

> **说明：**
>
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本Class首批接口从API version 10开始支持。
>
> - 以下API需先使用UIContext中的[getPromptAction()](arkts-arkui-uicontext-c.md#getPromptAction-1)方法获取到
PromptAction对象，再通过该对象调用对应方法。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## closeCustomDialog

```TypeScript
closeCustomDialog<T extends Object>(dialogContent: ComponentContent<T>): Promise<void>
```

关闭已弹出的dialogContent对应的自定义弹窗，使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

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
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [103301](../../errorcode-universal.md#103301-Dialog) | Dialog content error. The ComponentContent is incorrect. |
| [103303](../../errorcode-universal.md#103303-Dialog) | Dialog content not found. The ComponentContent cannot be found. |

## closeCustomDialog

```TypeScript
closeCustomDialog(dialogId: number): void
```

关闭自定义弹窗。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dialogId | number | 是 | openCustomDialog返回的对话框id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |

## closeMenu

```TypeScript
closeMenu<T extends Object>(content: ComponentContent<T>): Promise<void>
```

关闭content对应的Menu弹窗。使用Promise异步回调。

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

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
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [103301](../../errorcode-universal.md#103301-The) | The ComponentContent is incorrect. |
| [103303](../../errorcode-universal.md#103303-The) | The ComponentContent cannot be found. |

## closePopup

```TypeScript
closePopup<T extends Object>(content: ComponentContent<T>): Promise<void>
```

关闭content对应的Popup弹窗，使用Promise异步回调。

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

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
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [103301](../../errorcode-universal.md#103301-The) | The ComponentContent is incorrect. |
| [103303](../../errorcode-universal.md#103303-The) | The ComponentContent cannot be found. |

## closeToast

```TypeScript
closeToast(toastId: number): void
```

关闭即时反馈。

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| toastId | number | 是 | openToast返回的id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |
| [103401](../../errorcode-universal.md#103401-Cannot) | Cannot find the toast. |

## getBottomOrder

```TypeScript
getBottomOrder(): LevelOrder
```

获取最底层显示的弹窗的顺序，可以在下一个弹窗时指定期望的顺序。

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| LevelOrder | 返回弹窗层级信息。 |

## getTopOrder

```TypeScript
getTopOrder(): LevelOrder
```

返回最顶层显示的弹窗的顺序。

获取最顶层显示的弹窗的顺序，可以在下一个弹窗时指定期望的顺序。

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| LevelOrder | 返回弹窗层级信息。 |

## openCustomDialog

```TypeScript
openCustomDialog<T extends Object>(dialogContent: ComponentContent<T>, options?: promptAction.BaseDialogOptions): Promise<void>
```

创建并弹出dialogContent对应的自定义弹窗，使用Promise异步回调。通过该接口弹出的弹窗内容样式完全按照dialogContent中设置的样式显示，
即相当于customDialog设置customStyle为true时的显示效果。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dialogContent | ComponentContent&lt;T&gt; | 是 | 自定义弹窗中显示的组件内容。 |
| options | promptAction.BaseDialogOptions | 否 | 弹窗样式。<br/><br/>**说明：** 如果BaseDialogOptions中的[isModal](arkts-arkui-promptaction-basedialogoptions-i.md#BaseDialogOptions)<br/>与[showInSubWindow](arkts-arkui-promptaction-basedialogoptions-i.md#BaseDialogOptions)同时设置为true，则只生效showInSubWindow = true，<br/>此时为非模态弹出框且不会显示蒙层，并在子窗口中显示。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [103301](../../errorcode-universal.md#103301-Dialog) | Dialog content error. The ComponentContent is incorrect. |
| [103302](../../errorcode-universal.md#103302-Dialog) | Dialog content already exist. The ComponentContent has already been opened. |

## openCustomDialog

```TypeScript
openCustomDialog(options: promptAction.CustomDialogOptions): Promise<number>
```

创建并弹出自定义弹窗。使用Promise异步回调返回对话框的id，可供closeCustomDialog使用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | promptAction.CustomDialogOptions | 是 | 自定义弹窗的内容。<br/><br/>**说明：** 如果BaseDialogOptions中的[isModal](arkts-arkui-promptaction-basedialogoptions-i.md#BaseDialogOptions)与<br/>[showInSubWindow](arkts-arkui-promptaction-basedialogoptions-i.md#BaseDialogOptions)同时设置为true，则只生效showInSubWindow = true，<br/>此时为非模态弹出框且不会显示蒙层，并在子窗口中显示。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。返回对话框id，可供closeCustomDialog使用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |

## openCustomDialogWithController

```TypeScript
openCustomDialogWithController<T extends Object>(dialogContent: ComponentContent<T>, controller: promptAction.DialogController,
    options?: promptAction.BaseDialogOptions): Promise<void>
```

创建并弹出dialogContent对应的自定义弹窗，使用Promise异步回调。支持传入弹窗控制器与自定义弹窗绑定，后续可以通过控制器控制自定义弹窗。

通过该接口弹出的弹窗内容样式完全按照dialogContent中设置的样式显示，即相当于customDialog设置customStyle为true时的显示效果。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dialogContent | ComponentContent&lt;T&gt; | 是 | 自定义弹窗中显示的组件内容。 |
| controller | promptAction.DialogController | 是 | 自定义弹窗的控制器。 |
| options | promptAction.BaseDialogOptions | 否 | 自定义弹窗的样式。<br/><br/>**说明：** 如果BaseDialogOptions中的[isModal](arkts-arkui-promptaction-basedialogoptions-i.md#BaseDialogOptions)与<br/>[showInSubWindow](arkts-arkui-promptaction-basedialogoptions-i.md#BaseDialogOptions)同时设置为true，则只生效showInSubWindow = true，<br/>此时为非模态弹出框且不会显示蒙层，并在子窗口中显示。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [103301](../../errorcode-universal.md#103301-Dialog) | Dialog content error. The ComponentContent is incorrect. |
| [103302](../../errorcode-universal.md#103302-Dialog) | Dialog content already exist. The ComponentContent has already been opened. |

## openMenu

```TypeScript
openMenu<T extends Object>(content: ComponentContent<T>, target: TargetInfo, options?: MenuOptions): Promise<void>
```

创建并弹出以content作为内容的Menu弹窗。使用Promise异步回调。

> **说明：**
>
> - 使用该接口时，若未传入有效的target，则无法弹出menu弹窗。
>
> - 由于[updateMenu](arkts-arkui-promptaction-c.md#updateMenu-1)和[closeMenu](arkts-arkui-promptaction-c.md#closeMenu-1)依赖content去更新或者关闭指定的menu弹窗，开发者需自行维护传入的content。
>
> - 如果在wrapBuilder中包含其他组件（例如：[Popup](arkts-arkui-advanced-popup.md)、
[Chip](arkts-arkui-advanced-chip.md)组件），则
[ComponentContent](arkts-arkui-componentcontent-c.md#ComponentContent)应采用带有四个参数的构造函数constructor，
其中options参数应传递{ nestingBuilderSupported: true }。
>
> - 子窗弹窗里不能再弹出子窗弹窗，例如[openMenu](arkts-arkui-promptaction-c.md#openMenu-1)设置了showInSubWindow为true时，则不能再弹出另一个设置了
showInSubWindow为true的弹窗。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent&lt;T&gt; | 是 | menu弹窗中显示的组件内容。 |
| target | TargetInfo | 是 | 需要绑定组件的信息。 |
| options | MenuOptions | 否 | menu弹窗样式。<br/><br/>**说明：**<br/><br/>title属性不生效。<br/><br/>preview参数仅支持设置MenuPreviewMode类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [103301](../../errorcode-universal.md#103301-The) | The ComponentContent is incorrect. |
| [103302](../../errorcode-universal.md#103302-The) | The ComponentContent already exists. |
| [103304](../../errorcode-universal.md#103304-The) | The targetId does not exist. |
| [103305](../../errorcode-universal.md#103305-The) | The node of targetId is not in the component tree. |

## openPopup

```TypeScript
openPopup<T extends Object>(content: ComponentContent<T>, target: TargetInfo, options?: PopupCommonOptions): Promise<void>
```

创建并弹出以content作为内容的Popup弹窗，使用Promise异步回调。

> **说明：**
>
> - 使用该接口时，若未传入有效的target，则无法弹出popup弹窗。
>
> - 由于[updatePopup](arkts-arkui-promptaction-c.md#updatePopup-1)和[closePopup](arkts-arkui-promptaction-c.md#closePopup-1)依赖content去更新或者关闭指定的popup弹窗，开发者需自行维护传入的content。
>
> - 如果在wrapBuilder中包含其他组件（例如：[Popup](arkts-arkui-advanced-popup.md)、[Chip](arkts-arkui-advanced-chip.md)组件），则[ComponentContent](arkts-arkui-componentcontent-c.md#ComponentContent)应采用带有四个参数的构造函数constructor，其中options参数应传递{ nestingBuilderSupported: true }。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent&lt;T&gt; | 是 | popup弹窗中显示的组件内容。 |
| target | TargetInfo | 是 | 需要绑定组件的信息。 |
| options | PopupCommonOptions | 否 | popup弹窗样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [103301](../../errorcode-universal.md#103301-The) | The ComponentContent is incorrect. |
| [103302](../../errorcode-universal.md#103302-The) | The ComponentContent already exists. |
| [103304](../../errorcode-universal.md#103304-The) | The targetId does not exist. |
| [103305](../../errorcode-universal.md#103305-The) | The node of targetId is not in the component tree. |

## openToast

```TypeScript
openToast(options: promptAction.ShowToastOptions): Promise<number>
```

显示即时反馈。使用Promise异步回调返回即时反馈的id，可供closeToast使用。

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | promptAction.ShowToastOptions | 是 | Toast选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。返回即时反馈的id，可供closeToast使用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |

## presentCustomDialog

```TypeScript
presentCustomDialog(builder: CustomBuilder | CustomBuilderWithId, controller?: promptAction.DialogController,
    options?: promptAction.DialogOptions): Promise<number>
```

创建并弹出自定义弹窗。使用Promise异步回调返回对话框的id，可供closeCustomDialog使用。

支持在自定义弹窗内容中持有弹窗ID进行对应操作。支持传入弹窗控制器与自定义弹窗绑定，后续可以通过控制器控制自定义弹窗。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | CustomBuilder \| CustomBuilderWithId | 是 | 自定义弹窗的内容。 |
| controller | promptAction.DialogController | 否 | 自定义弹窗的控制器。 |
| options | promptAction.DialogOptions | 否 | 自定义弹窗的样式。<br/><br/>**说明：** 如果BaseDialogOptions中的[isModal](arkts-arkui-promptaction-basedialogoptions-i.md#BaseDialogOptions)与<br/>[showInSubWindow](arkts-arkui-promptaction-basedialogoptions-i.md#BaseDialogOptions)同时设置为true，则只生效showInSubWindow = true，<br/>此时为非模态弹出框且不会显示蒙层，并在子窗口中显示。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。返回自定义弹窗ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |

## showActionMenu

```TypeScript
showActionMenu(options: promptAction.ActionMenuOptions, callback: promptAction.ActionMenuSuccessResponse): void
```

创建并显示操作菜单，菜单响应结果使用callback异步回调返回。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [showActionMenu](arkts-arkui-promptaction-c.md#showActionMenu-1)

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | promptAction.ActionMenuOptions | 是 | 操作菜单选项。 |
| callback | promptAction.ActionMenuSuccessResponse | 是 | 回调函数，返回菜单的响应结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |

## showActionMenu

```TypeScript
showActionMenu(options: promptAction.ActionMenuOptions, callback: AsyncCallback<promptAction.ActionMenuSuccessResponse>): void
```

创建并显示操作菜单，菜单响应结果使用callback异步回调返回。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | promptAction.ActionMenuOptions | 是 | 操作菜单选项。 |
| callback | AsyncCallback&lt;promptAction.ActionMenuSuccessResponse&gt; | 是 | 回调函数。弹出操作菜单成功，err为undefined，<br/>data为获取到的操作菜单响应结果，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |

## showActionMenu

```TypeScript
showActionMenu(options: promptAction.ActionMenuOptions): Promise<promptAction.ActionMenuSuccessResponse>
```

创建并显示操作菜单，通过Promise异步回调获取菜单的响应结果。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | promptAction.ActionMenuOptions | 是 | 操作菜单选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;promptAction.ActionMenuSuccessResponse&gt; | callback - Promise对象，返回菜单的响应结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |

## showActionSheet

```TypeScript
showActionSheet(options: ActionSheetOptions): Promise<void>
```

显示操作列表。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | ActionSheetOptions | 是 | 操作列表的选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 函数返回的promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103306](../../errorcode-universal.md#103306-The) | The dialog cannot be opened due to the system pop-up window. |

## showAlertDialog

```TypeScript
showAlertDialog(options: AlertDialogParamWithConfirm | AlertDialogParamWithButtons | AlertDialogParamWithOptions): Promise<void>
```

显示告警对话框。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | AlertDialogParamWithConfirm \| AlertDialogParamWithButtons \| AlertDialogParamWithOptions | 是 | 告警对话框的选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 函数返回的promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103306](../../errorcode-universal.md#103306-The) | The dialog cannot be opened due to the system pop-up window. |

## showDialog

```TypeScript
showDialog(options: promptAction.ShowDialogOptions, callback: AsyncCallback<promptAction.ShowDialogSuccessResponse>): void
```

创建并显示对话框，对话框响应结果使用callback异步回调返回。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | promptAction.ShowDialogOptions | 是 | 页面显示对话框信息描述。 |
| callback | AsyncCallback&lt;promptAction.ShowDialogSuccessResponse&gt; | 是 | 回调函数。弹出对话框成功，err为undefined，<br/>data为获取到的对话框响应结果，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |

## showDialog

```TypeScript
showDialog(options: promptAction.ShowDialogOptions): Promise<promptAction.ShowDialogSuccessResponse>
```

创建并显示对话框，使用Promise异步回调获取对话框的响应结果。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

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
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |

## showToast

```TypeScript
showToast(options: promptAction.ShowToastOptions): void
```

创建并显示即时反馈。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | promptAction.ShowToastOptions | 是 | Toast选项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |

## updateCustomDialog

```TypeScript
updateCustomDialog<T extends Object>(dialogContent: ComponentContent<T>, options: promptAction.BaseDialogOptions): Promise<void>
```

更新已弹出的dialogContent对应的自定义弹窗的样式，使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

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
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [103301](../../errorcode-universal.md#103301-Dialog) | Dialog content error. The ComponentContent is incorrect. |
| [103303](../../errorcode-universal.md#103303-Dialog) | Dialog content not found. The ComponentContent cannot be found. |

## updateMenu

```TypeScript
updateMenu<T extends Object>(content: ComponentContent<T>, options: MenuOptions, partialUpdate?: boolean): Promise<void>
```

更新content对应的Menu弹窗的样式。使用Promise异步回调。

> **说明：**
>
> - 不支持更新showInSubWindow、preview、previewAnimationOptions、transition、onAppear、aboutToAppear、onDisappear、aboutToDisappear、onWillAppear、onDidAppear、onWillDisappear和onDidDisappear。
>
> - 支持mask通过设置[MenuMaskType](arkts-arkui-common-menumasktype-i.md#MenuMaskType)实现更新蒙层样式，不支持mask通过设置boolean实现蒙层从无到有或者从有到无的更新。

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent&lt;T&gt; | 是 | menu弹窗中显示的组件内容。 |
| options | MenuOptions | 是 | menu弹窗样式。<br/><br/>**说明：**<br/><br/>1. 不支持更新showInSubWindow、preview、previewAnimationOptions、transition、onAppear、aboutToAppear、onDisappear、<br/>aboutToDisappear、onWillAppear、onDidAppear、onWillDisappear和onDidDisappear。<br/><br/>2. 支持mask通过设置[MenuMaskType](arkts-arkui-common-menumasktype-i.md#MenuMaskType)实现更新蒙层样式，<br/>不支持mask通过设置boolean实现蒙层从无到有或者从有到无的更新。 |
| partialUpdate | boolean | 否 | menu弹窗更新方式，默认值为false。<br/><br/>**说明：**<br/><br/>1. true为增量更新，保留当前值，更新options中的指定属性。<br/><br/>2. false为全量更新，除options中的指定属性，其他属性恢复默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [103301](../../errorcode-universal.md#103301-The) | The ComponentContent is incorrect. |
| [103303](../../errorcode-universal.md#103303-The) | The ComponentContent cannot be found. |

## updatePopup

```TypeScript
updatePopup<T extends Object>(content: ComponentContent<T>, options: PopupCommonOptions, partialUpdate?: boolean): Promise<void>
```

更新content对应的Popup弹窗的样式，使用Promise异步回调。

> **说明：**
>
> 不支持更新showInSubWindow、focusable、onStateChange、onWillDismiss、transition。

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent&lt;T&gt; | 是 | popup弹窗中显示的组件内容。 |
| options | PopupCommonOptions | 是 | popup弹窗样式。<br/><br/>**说明：**<br/><br/>不支持更新showInSubWindow、focusable、onStateChange、onWillDismiss、transition。 |
| partialUpdate | boolean | 否 | popup弹窗更新方式，默认值为false。<br/><br/>**说明：**<br/><br/>true：增量更新，此时更新options中的指定属性，其它属性保留当前值。options中传入的属性为异常值或undefined时，不会对该属性进行更新。<br/>false：全量更新，此时更新options中的指定属性，并且其他属性恢复默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [103301](../../errorcode-universal.md#103301-The) | The ComponentContent is incorrect. |
| [103303](../../errorcode-universal.md#103303-The) | The ComponentContent cannot be found. |

