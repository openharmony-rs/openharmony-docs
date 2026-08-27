# inputmethod_inputmethod_proxy_capi.h

## 概述

输入法代理的头文件，提供应用主动向输入法服务发送请求和通知的方法，包括显示/隐藏键盘、通知选区变更、通知光标更新、通知配置变更、发送私有命令等。InputMethodProxy实例由OH_InputMethodController_Attach返回，不可自行创建，在Detach之前保持有效。

**引用文件：** <inputmethod/inputmethod_inputmethod_proxy_capi.h>

**库：** libohinputmethod.so

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**起始版本：** 12

**相关模块：** [InputMethod](capi-inputmethod.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) | InputMethod_InputMethodProxy | 应用与输入法服务之间的交互代理对象，应用可通过此对象调用输入法服务的相关接口，并接收输入法服务的事件回调。该结构体为不透明类型（opaque type），调用者不可直接访问其内部成员，仅可通过本模块提供的函数接口进行操作。<br><br>用途<br><br>InputMethod_InputMethodProxy是应用端与输入法服务交互的核心代理对象，用于向输入法服务发送请求和通知。通过此代理对象，应用可以控制键盘的显示与隐藏、通知编辑框的文本选区变化和配置变化、更新光标位置、以及发送私有命令数据。<br><br>生命周期管理<br><br>- 创建方式：由[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)函数创建并作为输出参数返回，调用者不可手动创建此对象。<br>- 销毁方式：不可手动销毁。当调用[OH_InputMethodController_Detach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_detach)解除绑定后，InputMethod_InputMethodProxy对象将由系统自动释放并失效。<br>- 有效性：InputMethod_InputMethodProxy仅在Attach与Detach之间有效。Detach后，所有通过此对象调用的函数将返回IME_ERR_DETACHED错误码，不可再使用。<br>- 重复创建/销毁：不支持重复销毁。每次Attach会产生一个新的InputMethod_InputMethodProxy实例，对应的Detach会使其失效。<br><br>使用注意事项<br><br>- 调用任何InputMethod_InputMethodProxy相关函数前，必须确保已通过[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)成功获取该对象，且尚未调用Detach。<br>- inputMethodProxy指针不可为NULL，传入NULL指针将导致IME_ERR_NULL_POINTER错误码。示例：调用前未判空即调用函数时触发，应在调用前判断指针是否为NULL，若为NULL则先通过Attach获取有效对象或终止调用。<br>- Detach后不可再使用已获取的inputMethodProxy指针，所有操作将返回IME_ERR_DETACHED。示例：在Detach后调用任何接口时返回该码，应检查生命周期状态，仅在Attach与Detach之间使用该对象，否则重新Attach。此对象为不透明类型，不可直接访问内部成员或进行内存操作（如malloc/free）。<br>- 非线程安全，不建议在多线程环境下同时操作同一个inputMethodProxy对象，如需多线程访问请自行加锁保护。<br><br>相关函数：<br><br>以下为可通过InputMethod_InputMethodProxy对象调用的操作函数：<br> \| 函数 \| 描述 \| \| -- \| -- \| \| [OH_InputMethodProxy_ShowKeyboard](capi-inputmethod-inputmethod-proxy-capi-h.md#oh_inputmethodproxy_showkeyboard) \| 显示键盘。 \| \| [OH_InputMethodProxy_ShowTextInput](capi-inputmethod-inputmethod-proxy-capi-h.md#oh_inputmethodproxy_showtextinput) \| 显示文本输入框。 \| \| [OH_InputMethodProxy_HideKeyboard](capi-inputmethod-inputmethod-proxy-capi-h.md#oh_inputmethodproxy_hidekeyboard) \| 隐藏键盘。 \| \| [OH_InputMethodProxy_NotifySelectionChange](capi-inputmethod-inputmethod-proxy-capi-h.md#oh_inputmethodproxy_notifyselectionchange) \| 通知文本框选区变化。 \| \| [OH_InputMethodProxy_NotifyConfigurationChange](capi-inputmethod-inputmethod-proxy-capi-h.md#oh_inputmethodproxy_notifyconfigurationchange) \| 通知输入框配置变化。 \| \| [OH_InputMethodProxy_NotifyCursorUpdate](capi-inputmethod-inputmethod-proxy-capi-h.md#oh_inputmethodproxy_notifycursorupdate) \| 通知光标位置变化。 \| \| [OH_InputMethodProxy_SendPrivateCommand](capi-inputmethod-inputmethod-proxy-capi-h.md#oh_inputmethodproxy_sendprivatecommand) \| 发送私有数据命令。 \|<br><br>关联关系:<br>- 与TextEditorProxy的关系：[InputMethod_TextEditorProxy](capi-inputmethod-inputmethod-texteditorproxy.md)负责接收输入法应用的请求和通知，InputMethod_InputMethodProxy负责向输入法服务发送请求和通知。两者在Attach时同时建立关联，构成双向通信通道。<br>- 与AttachOptions的关系：[InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md)在Attach时传入，用于配置绑定选项（如是否显示键盘、请求键盘原因等），Attach成功后生成InputMethod_InputMethodProxy实例。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [InputMethod_ErrorCode OH_InputMethodProxy_ShowKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)](#oh_inputmethodproxy_showkeyboard) | 显示键盘。调用此函数后，系统将请求输入法应用弹出软键盘界面，用于文本输入。<br><br>使用场景：当应用需要主动拉起键盘以便用户进行文本输入时调用此函数，例如编辑框获得焦点后需要显示键盘的场景。<br><br>使用后效果：调用成功后，输入法应用将弹出软键盘界面；调用失败后，返回对应的错误码，需根据错误码进行处理。<br><br>前置条件：必须先调用[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)获取inputMethodProxy实例，且当前处于已绑定（Attached）状态。<br><br>生命周期管理：inputMethodProxy由[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)创建输出，不可手动销毁。当调用[OH_InputMethodController_Detach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_detach)解除绑定后，inputMethodProxy将失效，此后再调用此函数将返回IME_ERR_DETACHED错误码。<br><br>调用顺序：OH_InputMethodController_Attach → OH_InputMethodProxy_ShowKeyboard →OH_InputMethodProxy_HideKeyboard → OH_InputMethodController_Detach<br><br>线程安全：此函数非线程安全，不建议在多线程环境下同时操作同一个inputMethodProxy对象，如需多线程访问请自行加锁保护。 |
| [InputMethod_ErrorCode OH_InputMethodProxy_ShowTextInput(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_AttachOptions *options)](#oh_inputmethodproxy_showtextinput) | 显示文本输入框。与ShowKeyboard不同，此接口可通过AttachOptions指定请求键盘输入的原因，系统根据原因决定是否弹出键盘。<br><br>使用场景：当应用需要在特定场景下（如主动切换输入框、恢复输入等）请求显示文本输入界面时调用此函数，特别适用于需要携带RequestKeyboardReason的场景。<br><br>使用后效果：调用成功后，系统将根据options中的RequestKeyboardReason决定是否弹出键盘并激活文本输入；调用失败后，返回对应的错误码。<br><br>前置条件：必须先调用[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)获取inputMethodProxy实例，且当前处于已绑定（Attached）状态。options参数需先通过[OH_AttachOptions_Create](capi-inputmethod-attach-options-capi-h.md#oh_attachoptions_create)创建。<br><br>生命周期管理：inputMethodProxy由[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)创建输出，不可手动销毁。Detach后失效。options的生命周期由调用者管理，使用完毕后需调用[OH_AttachOptions_Destroy](capi-inputmethod-attach-options-capi-h.md#oh_attachoptions_destroy)销毁。<br><br>线程安全：此函数非线程安全，不建议在多线程环境下同时操作同一个inputMethodProxy对象。 |
| [InputMethod_ErrorCode OH_InputMethodProxy_HideKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)](#oh_inputmethodproxy_hidekeyboard) | 隐藏键盘。调用此函数后，系统将请求输入法应用关闭软键盘界面。<br><br>使用场景：当应用需要主动收起键盘时调用此函数，例如编辑框失去焦点、用户完成输入后需要隐藏键盘的场景。<br><br>使用后效果：调用成功后，输入法应用将收起软键盘界面；调用失败后，返回对应的错误码。<br><br>前置条件：必须先调用[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)获取inputMethodProxy实例，且当前处于已绑定（Attached）状态。<br><br>生命周期管理：inputMethodProxy由[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)创建输出，不可手动销毁。Detach后失效，再调用此函数将返回IME_ERR_DETACHED。<br><br>线程安全：此函数非线程安全，不建议在多线程环境下同时操作同一个inputMethodProxy对象。 |
| [InputMethod_ErrorCode OH_InputMethodProxy_NotifySelectionChange(InputMethod_InputMethodProxy *inputMethodProxy, char16_t text[], size_t length, int start, int end)](#oh_inputmethodproxy_notifyselectionchange) | 通知文本框选区变化。当输入框内文本内容、光标位置或选中文本发生变化时，通过此接口将变更信息通知给输入法应用，使输入法能够感知编辑框的文本状态。<br><br>使用场景：当编辑框中的文本内容被修改、光标位置发生移动、或用户选中文本发生变化时调用此函数，确保输入法应用与编辑框的文本状态保持同步。<br><br>使用后效果：调用成功后，输入法应用将接收到选区变更信息，并据此更新输入法内部状态（如候选词、联想等）；调用失败后，返回对应的错误码。<br><br>前置条件：必须先调用[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)获取inputMethodProxy实例，且当前处于已绑定（Attached）状态。<br><br>生命周期管理：inputMethodProxy由[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)创建输出，不可手动销毁。Detach后失效。<br><br>内存管理：text参数为输入指针，由调用者分配内存，函数内部仅读取该数据，不会修改或释放。调用者负责text数组内存的生命周期管理。<br><br>线程安全：此函数非线程安全，不建议在多线程环境下同时操作同一个inputMethodProxy对象。 |
| [InputMethod_ErrorCode OH_InputMethodProxy_NotifyConfigurationChange(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_EnterKeyType enterKey, InputMethod_TextInputType textType)](#oh_inputmethodproxy_notifyconfigurationchange) | 通知输入框配置变化。当编辑框的回车键类型或输入类型发生变化时，通过此接口将新的配置信息通知给输入法应用，使输入法能够调整键盘布局和输入行为。<br><br>使用场景：当编辑框的输入类型（如从文本模式切换为数字模式）或回车键类型（如从"完成"切换为"搜索"）发生变化时调用此函数。<br><br>使用后效果：调用成功后，输入法应用将根据新的配置调整键盘布局和回车键显示；调用失败后，返回对应的错误码。<br><br>前置条件：必须先调用[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)获取inputMethodProxy实例，且当前处于已绑定（Attached）状态。<br><br>生命周期管理：inputMethodProxy由[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)创建输出，不可手动销毁。Detach后失效。<br><br>线程安全：此函数非线程安全，不建议在多线程环境下同时操作同一个inputMethodProxy对象。 |
| [InputMethod_ErrorCode OH_InputMethodProxy_NotifyCursorUpdate(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_CursorInfo *cursorInfo)](#oh_inputmethodproxy_notifycursorupdate) | 通知光标位置变化。当编辑框中光标位置发生变化时，通过此接口将新的光标信息通知给输入法应用，使输入法能够根据光标位置调整候选词窗口的显示位置。<br><br>使用场景：当编辑框中光标位置发生移动时调用此函数，例如用户点击编辑框中不同位置、代码主动移动光标等场景。<br><br>使用后效果：调用成功后，输入法应用将接收到新的光标信息，并据此调整候选词窗口的定位；调用失败后，返回对应的错误码。<br><br>前置条件：必须先调用[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)获取inputMethodProxy实例。cursorInfo需先通过[OH_CursorInfo_Create](capi-inputmethod-cursor-info-capi-h.md#oh_cursorinfo_create)创建并设置相关属性。<br><br>生命周期管理：inputMethodProxy由Attach创建输出，不可手动销毁，Detach后失效。cursorInfo的生命周期由调用者管理，使用完毕后需调用[OH_CursorInfo_Destroy](capi-inputmethod-cursor-info-capi-h.md#oh_cursorinfo_destroy)销毁。<br><br>线程安全：此函数非线程安全，不建议在多线程环境下同时操作同一个inputMethodProxy对象。 |
| [InputMethod_ErrorCode OH_InputMethodProxy_SendPrivateCommand(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_PrivateCommand *privateCommand[], size_t size)](#oh_inputmethodproxy_sendprivatecommand) | 发送私有数据命令。应用通过此接口向输入法应用发送自定义的私有命令数据，用于实现应用与输入法之间的私有通信协议。<br><br>使用场景：当应用需要向输入法应用传递自定义的私有数据（如业务特定的指令、配置参数等）时调用此函数，适用于应用与输入法之间有私有通信协议的场景。<br><br>使用后效果：调用成功后，输入法应用将通过[OH_TextEditorProxy_ReceivePrivateCommandFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_receiveprivatecommandfunc)回调接收到私有命令数据；调用失败后，返回对应的错误码。<br><br>前置条件：必须先调用[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)获取inputMethodProxy实例，且当前处于已绑定（Attached）状态。<br><br>生命周期管理：inputMethodProxy由Attach创建输出，不可手动销毁，Detach后失效。privateCommand数组中每个元素的生命周期由调用者管理，使用完毕后需调用[OH_PrivateCommand_Destroy](capi-inputmethod-private-command-capi-h.md#oh_privatecommand_destroy)逐个销毁。<br><br>性能建议：privateCommand数组最多包含5个命令对象（size最大为5），超出此限制将返回IME_ERR_PARAMCHECK。单个命令对象最大大小为32KB，超出限制可能导致数据传输失败。<br><br>线程安全：此函数非线程安全，不建议在多线程环境下同时操作同一个inputMethodProxy对象。 |

## 函数说明

### OH_InputMethodProxy_ShowKeyboard()

```c
InputMethod_ErrorCode OH_InputMethodProxy_ShowKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)
```

**描述**

显示键盘。调用此函数后，系统将请求输入法应用弹出软键盘界面，用于文本输入。<br><br>使用场景：当应用需要主动拉起键盘以便用户进行文本输入时调用此函数，例如编辑框获得焦点后需要显示键盘的场景。<br><br>使用后效果：调用成功后，输入法应用将弹出软键盘界面；调用失败后，返回对应的错误码，需根据错误码进行处理。<br><br>前置条件：必须先调用[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)获取inputMethodProxy实例，且当前处于已绑定（Attached）状态。<br><br>生命周期管理：inputMethodProxy由[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)创建输出，不可手动销毁。当调用[OH_InputMethodController_Detach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_detach)解除绑定后，inputMethodProxy将失效，此后再调用此函数将返回IME_ERR_DETACHED错误码。<br><br>调用顺序：OH_InputMethodController_Attach → OH_InputMethodProxy_ShowKeyboard →OH_InputMethodProxy_HideKeyboard → OH_InputMethodController_Detach<br><br>线程安全：此函数非线程安全，不建议在多线程环境下同时操作同一个inputMethodProxy对象，如需多线程访问请自行加锁保护。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | 输入指针，表示指向[InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md)实例的指针。inputMethodProxy由调用[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)获取。该指针不可为NULL，若传入NULL指针将返回IME_ERR_NULL_POINTER错误码。Detach后该指针失效，不可再用于调用任何InputMethodProxy相关函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功，键盘已请求显示。      <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法客户端错误，可能是客户端内部异常。      <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法服务错误，可能是输入法管理服务不可用。      <br>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 未绑定输入法，表示已调用Detach，需重新Attach后再使用。      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针，传入的inputMethodProxy为NULL。      <br>具体错误码可以参考[InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_InputMethodProxy_ShowTextInput()

```c
InputMethod_ErrorCode OH_InputMethodProxy_ShowTextInput(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_AttachOptions *options)
```

**描述**

显示文本输入框。与ShowKeyboard不同，此接口可通过AttachOptions指定请求键盘输入的原因，系统根据原因决定是否弹出键盘。<br><br>使用场景：当应用需要在特定场景下（如主动切换输入框、恢复输入等）请求显示文本输入界面时调用此函数，特别适用于需要携带RequestKeyboardReason的场景。<br><br>使用后效果：调用成功后，系统将根据options中的RequestKeyboardReason决定是否弹出键盘并激活文本输入；调用失败后，返回对应的错误码。<br><br>前置条件：必须先调用[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)获取inputMethodProxy实例，且当前处于已绑定（Attached）状态。options参数需先通过[OH_AttachOptions_Create](capi-inputmethod-attach-options-capi-h.md#oh_attachoptions_create)创建。<br><br>生命周期管理：inputMethodProxy由[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)创建输出，不可手动销毁。Detach后失效。options的生命周期由调用者管理，使用完毕后需调用[OH_AttachOptions_Destroy](capi-inputmethod-attach-options-capi-h.md#oh_attachoptions_destroy)销毁。<br><br>线程安全：此函数非线程安全，不建议在多线程环境下同时操作同一个inputMethodProxy对象。

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | 输入指针，表示指向[InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md)实例的指针。inputMethodProxy由调用[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)获取。该指针不可为NULL，若传入NULL指针将返回IME_ERR_NULL_POINTER错误码。Detach后该指针失效。 |
| InputMethod_AttachOptions *options | 输入指针，表示指向[InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md)实例的指针，用于获取配置选项。该指针不可为NULL，若传入NULL指针将返回IME_ERR_NULL_POINTER错误码。此接口中只需关注[InputMethod_RequestKeyboardReason](capi-inputmethod-types-capi-h.md#inputmethod_requestkeyboardreason)属性，表示请求键盘输入的原因。AttachOptions中的ShowKeyboard属性在此接口中始终为true，无需额外关注。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功。      <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法客户端错误。      <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法服务错误。      <br>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 未绑定输入法，已Detach需重新Attach。      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针，inputMethodProxy或options为NULL。      <br>具体错误码可以参考[InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_InputMethodProxy_HideKeyboard()

```c
InputMethod_ErrorCode OH_InputMethodProxy_HideKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)
```

**描述**

隐藏键盘。调用此函数后，系统将请求输入法应用关闭软键盘界面。<br><br>使用场景：当应用需要主动收起键盘时调用此函数，例如编辑框失去焦点、用户完成输入后需要隐藏键盘的场景。<br><br>使用后效果：调用成功后，输入法应用将收起软键盘界面；调用失败后，返回对应的错误码。<br><br>前置条件：必须先调用[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)获取inputMethodProxy实例，且当前处于已绑定（Attached）状态。<br><br>生命周期管理：inputMethodProxy由[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)创建输出，不可手动销毁。Detach后失效，再调用此函数将返回IME_ERR_DETACHED。<br><br>线程安全：此函数非线程安全，不建议在多线程环境下同时操作同一个inputMethodProxy对象。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | 输入指针，表示指向[InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md)实例的指针。inputMethodProxy由调用[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)获取。该指针不可为NULL，若传入NULL指针将返回IME_ERR_NULL_POINTER错误码。Detach后该指针失效。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功，键盘已请求隐藏。      <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法客户端错误。      <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法服务错误。      <br>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 未绑定输入法，已Detach需重新Attach。      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针。      <br>具体错误码可以参考[InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_InputMethodProxy_NotifySelectionChange()

```c
InputMethod_ErrorCode OH_InputMethodProxy_NotifySelectionChange(InputMethod_InputMethodProxy *inputMethodProxy, char16_t text[], size_t length, int start, int end)
```

**描述**

通知文本框选区变化。当输入框内文本内容、光标位置或选中文本发生变化时，通过此接口将变更信息通知给输入法应用，使输入法能够感知编辑框的文本状态。<br><br>使用场景：当编辑框中的文本内容被修改、光标位置发生移动、或用户选中文本发生变化时调用此函数，确保输入法应用与编辑框的文本状态保持同步。<br><br>使用后效果：调用成功后，输入法应用将接收到选区变更信息，并据此更新输入法内部状态（如候选词、联想等）；调用失败后，返回对应的错误码。<br><br>前置条件：必须先调用[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)获取inputMethodProxy实例，且当前处于已绑定（Attached）状态。<br><br>生命周期管理：inputMethodProxy由[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)创建输出，不可手动销毁。Detach后失效。<br><br>内存管理：text参数为输入指针，由调用者分配内存，函数内部仅读取该数据，不会修改或释放。调用者负责text数组内存的生命周期管理。<br><br>线程安全：此函数非线程安全，不建议在多线程环境下同时操作同一个inputMethodProxy对象。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | 输入指针，表示指向[InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md)实例的指针。inputMethodProxy由调用[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)获取。该指针不可为NULL，若传入NULL指针将返回IME_ERR_NULL_POINTER错误码。Detach后该指针失效。 |
| char16_t text[] | 输入指针，整个输入文本，采用UTF-16编码。由调用者分配内存，函数仅读取该数据。该指针不可为NULL。长度最大限制为8K（8192个char16_t字符，对应16384字节），超出此限制将返回IME_ERR_PARAMCHECK。 |
| size_t length | 输入参数，text参数的字符数量（单位：char16_t字符个数）。取值范围：大于0且不超过8192。超过8192将返回IME_ERR_PARAMCHECK错误码。 |
| int start | 输入参数，所选文本的起始位置（单位：字符偏移量，从0开始计数）。取值范围：大于等于0且小于等于end。取值原则：start应小于等于end，且不超过text的实际长度。 |
| int end | 输入参数，所选文本的结束位置（单位：字符偏移量，从0开始计数）。取值范围：大于等于start且小于等于text的实际长度。取值原则：当无选中文本时，start与end相等，表示光标位置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功。      <br>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 参数错误，可能是length超过8K限制、start/end范围不合法等，请检查参数值是否在有效范围  内。      <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法客户端错误。      <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法服务错误。      <br>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 未绑定输入法，已Detach需重新Attach。      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针，inputMethodProxy为NULL。      <br>具体错误码可以参考[InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_InputMethodProxy_NotifyConfigurationChange()

```c
InputMethod_ErrorCode OH_InputMethodProxy_NotifyConfigurationChange(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_EnterKeyType enterKey, InputMethod_TextInputType textType)
```

**描述**

通知输入框配置变化。当编辑框的回车键类型或输入类型发生变化时，通过此接口将新的配置信息通知给输入法应用，使输入法能够调整键盘布局和输入行为。<br><br>使用场景：当编辑框的输入类型（如从文本模式切换为数字模式）或回车键类型（如从"完成"切换为"搜索"）发生变化时调用此函数。<br><br>使用后效果：调用成功后，输入法应用将根据新的配置调整键盘布局和回车键显示；调用失败后，返回对应的错误码。<br><br>前置条件：必须先调用[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)获取inputMethodProxy实例，且当前处于已绑定（Attached）状态。<br><br>生命周期管理：inputMethodProxy由[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)创建输出，不可手动销毁。Detach后失效。<br><br>线程安全：此函数非线程安全，不建议在多线程环境下同时操作同一个inputMethodProxy对象。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | 输入指针，表示指向[InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md)实例的指针。inputMethodProxy由调用[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)获取。该指针不可为NULL，若传入NULL指针将返回IME_ERR_NULL_POINTER错误码。Detach后该指针失效。 |
| [InputMethod_EnterKeyType](capi-inputmethod-types-capi-h.md#inputmethod_enterkeytype) enterKey | 输入参数，回车键类型。取值范围：[InputMethod_EnterKeyType](capi-inputmethod-types-capi-h.md#inputmethod_enterkeytype)枚举值，如IME_ENTER_KEY_UNSPECIFIED、IME_ENTER_KEY_GO、IME_ENTER_KEY_SEARCH等。使用后效果：输入法将据此调整回车键的显示标签和功能。 |
| [InputMethod_TextInputType](capi-inputmethod-types-capi-h.md#inputmethod_textinputtype) textType | 输入参数，输入框类型。取值范围：[InputMethod_TextInputType](capi-inputmethod-types-capi-h.md#inputmethod_textinputtype)枚举值，如IME_TEXT_INPUT_TYPE_UNSPECIFIED、IME_TEXT_INPUT_TYPE_TEXT、IME_TEXT_INPUT_TYPE_NUMBER等。使用后效果：输入法将据此切换键盘布局（如数字键盘、文本键盘等）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功。      <br>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 参数错误，可能是enterKey或textType值不合法，请检查枚举值是否在有效范围内。      <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法客户端错误。      <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法服务错误。      <br>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 未绑定输入法，已Detach需重新Attach。      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针。      <br>具体错误码可以参考[InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_InputMethodProxy_NotifyCursorUpdate()

```c
InputMethod_ErrorCode OH_InputMethodProxy_NotifyCursorUpdate(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_CursorInfo *cursorInfo)
```

**描述**

通知光标位置变化。当编辑框中光标位置发生变化时，通过此接口将新的光标信息通知给输入法应用，使输入法能够根据光标位置调整候选词窗口的显示位置。<br><br>使用场景：当编辑框中光标位置发生移动时调用此函数，例如用户点击编辑框中不同位置、代码主动移动光标等场景。<br><br>使用后效果：调用成功后，输入法应用将接收到新的光标信息，并据此调整候选词窗口的定位；调用失败后，返回对应的错误码。<br><br>前置条件：必须先调用[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)获取inputMethodProxy实例。cursorInfo需先通过[OH_CursorInfo_Create](capi-inputmethod-cursor-info-capi-h.md#oh_cursorinfo_create)创建并设置相关属性。<br><br>生命周期管理：inputMethodProxy由Attach创建输出，不可手动销毁，Detach后失效。cursorInfo的生命周期由调用者管理，使用完毕后需调用[OH_CursorInfo_Destroy](capi-inputmethod-cursor-info-capi-h.md#oh_cursorinfo_destroy)销毁。<br><br>线程安全：此函数非线程安全，不建议在多线程环境下同时操作同一个inputMethodProxy对象。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | 输入指针，表示指向[InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md)实例的指针。inputMethodProxy由调用{@link OH_InputMethodController_Attach}获取。该指针不可为NULL，若传入NULL指针将返回IME_ERR_NULL_POINTER错误码。Detach后该指针失效。 |
| [InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md) *cursorInfo | 输入指针，指向[InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md)实例的指针，表示光标信息。该指针不可为NULL，若传入NULL指针将返回IME_ERR_NULL_POINTER错误码。cursorInfo由调用者通过[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)创建，函数仅读取其内部数据，不会修改或释放。使用完毕后调用者需调用[OH_CursorInfo_Destroy](capi-inputmethod-cursor-info-capi-h.md#oh_cursorinfo_destroy)释放cursorInfo。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功。      <br>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 参数错误，可能是cursorInfo内部数据不合法，请检查光标信息参数。      <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法客户端错误。      <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法服务错误。      <br>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 未绑定输入法，已Detach需重新Attach。      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针，inputMethodProxy或cursorInfo为NULL。      <br>具体错误码可以参考[InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_InputMethodProxy_SendPrivateCommand()

```c
InputMethod_ErrorCode OH_InputMethodProxy_SendPrivateCommand(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_PrivateCommand *privateCommand[], size_t size)
```

**描述**

发送私有数据命令。应用通过此接口向输入法应用发送自定义的私有命令数据，用于实现应用与输入法之间的私有通信协议。<br><br>使用场景：当应用需要向输入法应用传递自定义的私有数据（如业务特定的指令、配置参数等）时调用此函数，适用于应用与输入法之间有私有通信协议的场景。<br><br>使用后效果：调用成功后，输入法应用将通过[OH_TextEditorProxy_ReceivePrivateCommandFunc](capi-inputmethod-text-editor-proxy-capi-h.md#oh_texteditorproxy_receiveprivatecommandfunc)回调接收到私有命令数据；调用失败后，返回对应的错误码。<br><br>前置条件：必须先调用[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)获取inputMethodProxy实例，且当前处于已绑定（Attached）状态。<br><br>生命周期管理：inputMethodProxy由Attach创建输出，不可手动销毁，Detach后失效。privateCommand数组中每个元素的生命周期由调用者管理，使用完毕后需调用[OH_PrivateCommand_Destroy](capi-inputmethod-private-command-capi-h.md#oh_privatecommand_destroy)逐个销毁。<br><br>性能建议：privateCommand数组最多包含5个命令对象（size最大为5），超出此限制将返回IME_ERR_PARAMCHECK。单个命令对象最大大小为32KB，超出限制可能导致数据传输失败。<br><br>线程安全：此函数非线程安全，不建议在多线程环境下同时操作同一个inputMethodProxy对象。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | 输入指针，表示指向[InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md)实例的指针。inputMethodProxy由调用[OH_InputMethodController_Attach](capi-inputmethod-controller-capi-h.md#oh_inputmethodcontroller_attach)获取。该指针不可为NULL，若传入NULL指针将返回IME_ERR_NULL_POINTER错误码。Detach后该指针失效。 |
| InputMethod_PrivateCommand *privateCommand[] | 输入指针，私有命令数组，每个元素为指向InputMethod_PrivateCommand实例的指针。由调用者创建并分配内存，函数仅读取数据。该指针不可为NULL。单个命令对象最大大小为32KB（包含key和value的总大小），超出可能导致传输失败。数组最大长度为5（即size参数最大为5）。 |
| size_t size | 输入参数，私有命令数组的元素个数。取值范围：大于0且不超过5。超过5将返回IME_ERR_PARAMCHECK错误码。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。      <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功，私有命令已发送。      <br>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 参数错误，可能是size超过5、privateCommand为NULL、或单个命令超过32KB，请检查参数值。      <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法客户端错误。      <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法服务错误。      <br>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 未绑定输入法，已Detach需重新Attach。      <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针，inputMethodProxy或privateCommand为NULL。      <br>具体错误码可以参考[InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |


