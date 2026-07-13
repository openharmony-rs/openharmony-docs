# inputmethod_inputmethod_proxy_capi.h

## 概述

提供使用输入法的方法，可以向输入法应用发送请求和通知，适用于需要控制输入法显示、隐藏、配置变更通知等功能的应用开发场景。

**库：** libohinputmethod.so

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**起始版本：** 12

**相关模块：** [InputMethod](capi-inputmethod.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) | InputMethod_InputMethodProxy | 应用与输入法服务之间的交互代理对象，应用可通过此对象调用输入法服务的相关接口，并接收输入法服务的事件回调。该结构体为不透明类型（opaque type），调用者不可直接访问其内部成员，仅可通过本模块提供的函数接口进行操作。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [InputMethod_ErrorCode OH_InputMethodProxy_ShowKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)](#oh_inputmethodproxy_showkeyboard) | 显示键盘。调用此函数后，系统将请求输入法应用弹出软键盘界面，用于文本输入。 |
| [InputMethod_ErrorCode OH_InputMethodProxy_ShowTextInput(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_AttachOptions *options)](#oh_inputmethodproxy_showtextinput) | 显示文本输入框。与ShowKeyboard不同，此接口可通过AttachOptions指定请求键盘输入的原因，系统根据原因决定是否弹出键盘。 |
| [InputMethod_ErrorCode OH_InputMethodProxy_HideKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)](#oh_inputmethodproxy_hidekeyboard) | 隐藏键盘。调用此函数后，系统将请求输入法应用关闭软键盘界面。 |
| [InputMethod_ErrorCode OH_InputMethodProxy_NotifySelectionChange(InputMethod_InputMethodProxy *inputMethodProxy, char16_t text[], size_t length, int start, int end)](#oh_inputmethodproxy_notifyselectionchange) | 通知文本框选区变化。当输入框内文本内容、光标位置或选中文本发生变化时，通过此接口将变更信息通知给输入法应用，使输入法能够感知编辑框的文本状态。 |
| [InputMethod_ErrorCode OH_InputMethodProxy_NotifyConfigurationChange(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_EnterKeyType enterKey, InputMethod_TextInputType textType)](#oh_inputmethodproxy_notifyconfigurationchange) | 通知输入框配置变化。当编辑框的回车键类型或输入类型发生变化时，通过此接口将新的配置信息通知给输入法应用，使输入法能够调整键盘布局和输入行为。 |
| [InputMethod_ErrorCode OH_InputMethodProxy_NotifyCursorUpdate(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_CursorInfo *cursorInfo)](#oh_inputmethodproxy_notifycursorupdate) | 通知光标位置变化。当编辑框中光标位置发生变化时，通过此接口将新的光标信息通知给输入法应用，使输入法能够根据光标位置调整候选词窗口的显示位置。 |
| [InputMethod_ErrorCode OH_InputMethodProxy_SendPrivateCommand(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_PrivateCommand *privateCommand[], size_t size)](#oh_inputmethodproxy_sendprivatecommand) | 发送私有数据命令。应用通过此接口向输入法应用发送自定义的私有命令数据，用于实现应用与输入法之间的私有通信协议。 |

## 函数说明

### OH_InputMethodProxy_ShowKeyboard()

```c
InputMethod_ErrorCode OH_InputMethodProxy_ShowKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)
```

**描述**

显示键盘。调用此函数后，系统将请求输入法应用弹出软键盘界面，用于文本输入。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | 输入指针，表示指向[InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md)实例的指针。inputMethodProxy由调用{@link OH_InputMethodController_Attach}获取。该指针不可为NULL，若传入NULL指针将返回IME_ERR_NULL_POINTER错误码。Detach后该指针失效，不可再用于调用任何InputMethodProxy相关函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<br>     <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功，键盘已请求显示。<br>     <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法客户端错误，可能是客户端内部异常。<br>     <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法服务错误，可能是输入法管理服务不可用。<br>     <br>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 未绑定输入法，表示已调用Detach，需重新Attach后再使用。<br>     <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针，传入的inputMethodProxy为NULL。<br>     <br>具体错误码可以参考[InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_InputMethodProxy_ShowTextInput()

```c
InputMethod_ErrorCode OH_InputMethodProxy_ShowTextInput(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_AttachOptions *options)
```

**描述**

显示文本输入框。与ShowKeyboard不同，此接口可通过AttachOptions指定请求键盘输入的原因，系统根据原因决定是否弹出键盘。

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | 输入指针，表示指向[InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md)实例的指针。inputMethodProxy由调用{@link OH_InputMethodController_Attach}获取。该指针不可为NULL，若传入NULL指针将返回IME_ERR_NULL_POINTER错误码。Detach后该指针失效。 |
| [InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md) *options | 输入指针，表示指向[InputMethod_AttachOptions](capi-inputmethod-inputmethod-attachoptions.md)实例的指针，用于获取配置选项。该指针不可为NULL，若传入NULL指针将返回IME_ERR_NULL_POINTER错误码。此接口中只需关注[InputMethod_RequestKeyboardReason](capi-inputmethod-types-capi-h.md#inputmethod_requestkeyboardreason)属性，表示请求键盘输入的原因。AttachOptions中的ShowKeyboard属性在此接口中始终为true，无需额外关注。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<br>     <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功。<br>     <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法客户端错误。<br>     <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法服务错误。<br>     <br>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 未绑定输入法，已Detach需重新Attach。<br>     <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针，inputMethodProxy或options为NULL。<br>     <br>具体错误码可以参考[InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_InputMethodProxy_HideKeyboard()

```c
InputMethod_ErrorCode OH_InputMethodProxy_HideKeyboard(InputMethod_InputMethodProxy *inputMethodProxy)
```

**描述**

隐藏键盘。调用此函数后，系统将请求输入法应用关闭软键盘界面。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | 输入指针，表示指向[InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md)实例的指针。inputMethodProxy由调用{@link OH_InputMethodController_Attach}获取。该指针不可为NULL，若传入NULL指针将返回IME_ERR_NULL_POINTER错误码。Detach后该指针失效。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<br>     <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功，键盘已请求隐藏。<br>     <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法客户端错误。<br>     <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法服务错误。<br>     <br>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 未绑定输入法，已Detach需重新Attach。<br>     <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针。<br>     <br>具体错误码可以参考[InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_InputMethodProxy_NotifySelectionChange()

```c
InputMethod_ErrorCode OH_InputMethodProxy_NotifySelectionChange(InputMethod_InputMethodProxy *inputMethodProxy, char16_t text[], size_t length, int start, int end)
```

**描述**

通知文本框选区变化。当输入框内文本内容、光标位置或选中文本发生变化时，通过此接口将变更信息通知给输入法应用，使输入法能够感知编辑框的文本状态。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | 输入指针，表示指向[InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md)实例的指针。inputMethodProxy由调用{@link OH_InputMethodController_Attach}获取。该指针不可为NULL，若传入NULL指针将返回IME_ERR_NULL_POINTER错误码。Detach后该指针失效。 |
| char16_t text[] | The whole input text. |
| size_t length | 输入参数，text参数的字符数量（单位：char16_t字符个数）。取值范围：大于0且不超过8192。超过8192将返回IME_ERR_PARAMCHECK错误码。 |
| int start | 输入参数，所选文本的起始位置（单位：字符偏移量，从0开始计数）。取值范围：大于等于0且小于等于end。取值原则：start应小于等于end，且不超过text的实际长度。 |
| int end | 输入参数，所选文本的结束位置（单位：字符偏移量，从0开始计数）。取值范围：大于等于start且小于等于text的实际长度。取值原则：当无选中文本时，start与end相等，表示光标位置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<br>     <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功。<br>     <br>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 参数错误，可能是length超过8K限制、start/end范围不合法等，请检查参数值是否在有效范围内。<br>     <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法客户端错误。<br>     <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法服务错误。<br>     <br>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 未绑定输入法，已Detach需重新Attach。<br>     <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针，inputMethodProxy为NULL。<br>     <br>具体错误码可以参考[InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_InputMethodProxy_NotifyConfigurationChange()

```c
InputMethod_ErrorCode OH_InputMethodProxy_NotifyConfigurationChange(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_EnterKeyType enterKey, InputMethod_TextInputType textType)
```

**描述**

通知输入框配置变化。当编辑框的回车键类型或输入类型发生变化时，通过此接口将新的配置信息通知给输入法应用，使输入法能够调整键盘布局和输入行为。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | 输入指针，表示指向[InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md)实例的指针。inputMethodProxy由调用{@link OH_InputMethodController_Attach}获取。该指针不可为NULL，若传入NULL指针将返回IME_ERR_NULL_POINTER错误码。Detach后该指针失效。 |
| [InputMethod_EnterKeyType](capi-inputmethod-types-capi-h.md#inputmethod_enterkeytype) enterKey | 输入参数，回车键类型。取值范围：[InputMethod_EnterKeyType](capi-inputmethod-types-capi-h.md#inputmethod_enterkeytype)枚举值，如IME_ENTER_KEY_UNSPECIFIED、IME_ENTER_KEY_GO、IME_ENTER_KEY_SEARCH等。使用后效果：输入法将据此调整回车键的显示标签和功能。 |
| [InputMethod_TextInputType](capi-inputmethod-types-capi-h.md#inputmethod_textinputtype) textType | 输入参数，输入框类型。取值范围：[InputMethod_TextInputType](capi-inputmethod-types-capi-h.md#inputmethod_textinputtype)枚举值，如IME_TEXT_INPUT_TYPE_UNSPECIFIED、IME_TEXT_INPUT_TYPE_TEXT、IME_TEXT_INPUT_TYPE_NUMBER等。使用后效果：输入法将据此切换键盘布局（如数字键盘、文本键盘等）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<br>     <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功。<br>     <br>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 参数错误，可能是enterKey或textType值不合法，请检查枚举值是否在有效范围内。<br>     <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法客户端错误。<br>     <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法服务错误。<br>     <br>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 未绑定输入法，已Detach需重新Attach。<br>     <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针。<br>     <br>具体错误码可以参考[InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_InputMethodProxy_NotifyCursorUpdate()

```c
InputMethod_ErrorCode OH_InputMethodProxy_NotifyCursorUpdate(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_CursorInfo *cursorInfo)
```

**描述**

通知光标位置变化。当编辑框中光标位置发生变化时，通过此接口将新的光标信息通知给输入法应用，使输入法能够根据光标位置调整候选词窗口的显示位置。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | 输入指针，表示指向[InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md)实例的指针。inputMethodProxy由调用{@link OH_InputMethodController_Attach}获取。该指针不可为NULL，若传入NULL指针将返回IME_ERR_NULL_POINTER错误码。Detach后该指针失效。 |
| InputMethod_CursorInfo *cursorInfo | 输入指针，指向[InputMethod_CursorInfo](capi-inputmethod-inputmethod-cursorinfo.md)实例的指针，表示光标信息。该指针不可为NULL，若传入NULL指针将返回IME_ERR_NULL_POINTER错误码。cursorInfo由调用者通过[OH_CursorInfo_Create](capi-inputmethod-cursor-info-capi-h.md#oh_cursorinfo_create)创建，函数仅读取其内部数据，不会修改或释放。使用完毕后调用者需调用[OH_CursorInfo_Destroy](capi-inputmethod-cursor-info-capi-h.md#oh_cursorinfo_destroy)释放cursorInfo。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<br>     <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功。<br>     <br>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 参数错误，可能是cursorInfo内部数据不合法，请检查光标信息参数。<br>     <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法客户端错误。<br>     <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法服务错误。<br>     <br>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 未绑定输入法，已Detach需重新Attach。<br>     <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针，inputMethodProxy或cursorInfo为NULL。<br>     <br>具体错误码可以参考[InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |

### OH_InputMethodProxy_SendPrivateCommand()

```c
InputMethod_ErrorCode OH_InputMethodProxy_SendPrivateCommand(InputMethod_InputMethodProxy *inputMethodProxy, InputMethod_PrivateCommand *privateCommand[], size_t size)
```

**描述**

发送私有数据命令。应用通过此接口向输入法应用发送自定义的私有命令数据，用于实现应用与输入法之间的私有通信协议。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md) *inputMethodProxy | 输入指针，表示指向[InputMethod_InputMethodProxy](capi-inputmethod-inputmethod-inputmethodproxy.md)实例的指针。inputMethodProxy由调用{@link OH_InputMethodController_Attach}获取。该指针不可为NULL，若传入NULL指针将返回IME_ERR_NULL_POINTER错误码。Detach后该指针失效。 |
| InputMethod_PrivateCommand *privateCommand[] | The private commands, which is defined in [InputMethod_PrivateCommand](capi-inputmethod-inputmethod-privatecommand.md). Max size 32KB. |
| size_t size | 输入参数，私有命令数组的元素个数。取值范围：大于0且不超过5。超过5将返回IME_ERR_PARAMCHECK错误码。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) | 返回一个特定的错误码。<br>     <br>[IME_ERR_OK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 表示成功，私有命令已发送。<br>     <br>[IME_ERR_PARAMCHECK](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 参数错误，可能是size超过5、privateCommand为NULL、或单个命令超过32KB，请检查参数值。<br>     <br>[IME_ERR_IMCLIENT](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法客户端错误。<br>     <br>[IME_ERR_IMMS](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 输入法服务错误。<br>     <br>[IME_ERR_DETACHED](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 未绑定输入法，已Detach需重新Attach。<br>     <br>[IME_ERR_NULL_POINTER](capi-inputmethod-types-capi-h.md#inputmethod_errorcode) - 非预期的空指针，inputMethodProxy或privateCommand为NULL。<br>     <br>具体错误码可以参考[InputMethod_ErrorCode](capi-inputmethod-types-capi-h.md#inputmethod_errorcode)。 |


