# AVCastPickerHelper

投播半模态对象，可拉起半模态窗口，选择投播设备。在使用前，需要创建AVCastPickerHelper实例。

> **说明：**  
>  
> - 本Class首批接口从API version 14开始支持。  
>  
> - AVCastPickerHelper样式显示为半模态，实际会绑定  
> [全模态页面（bindContentCover）](../../apis-arkui/arkts-components/arkts-arkui-common-commonmethod-c.md#bindcontentcover-1)  
> 。

**起始版本：** 14

<!--Device-avSession-class AVCastPickerHelper--><!--Device-avSession-class AVCastPickerHelper-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## constructor

```TypeScript
constructor(context: Context)
```

创建AVCastPickerHelper对象，获取context请参考[getHostContext](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#gethostcontext-1)。

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastPickerHelper-constructor(context: Context)--><!--Device-AVCastPickerHelper-constructor(context: Context)-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文（仅支持[UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md)）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

## off('pickerStateChange')

```TypeScript
off(type: 'pickerStateChange', callback?: Callback<AVCastPickerState>) : void
```

取消半模态窗口变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastPickerHelper-off(type: 'pickerStateChange', callback?: Callback<AVCastPickerState>) : void--><!--Device-AVCastPickerHelper-off(type: 'pickerStateChange', callback?: Callback<AVCastPickerState>) : void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'pickerStateChange' | 是 | 取消对应的监听事件，支持事件`'pickerStateChange'`。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AVCastPickerState> | 否 | 回调函数，参数state是变化后的半模态窗口状态。<br>当监听事件取消成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

## on('pickerStateChange')

```TypeScript
on(type: 'pickerStateChange', callback: Callback<AVCastPickerState>) : void
```

设置半模态窗口变化的监听事件。

每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastPickerHelper-on(type: 'pickerStateChange', callback: Callback<AVCastPickerState>) : void--><!--Device-AVCastPickerHelper-on(type: 'pickerStateChange', callback: Callback<AVCastPickerState>) : void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'pickerStateChange' | 是 | 事件回调类型，支持事件`'pickerStateChange'`：当半模态窗口变化时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AVCastPickerState> | 是 | 回调函数，参数state是变化后的半模态窗口状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

## resetCommunicationDevice

```TypeScript
resetCommunicationDevice(): Promise<void>
```

将应用通话设备恢复至默认设备。例如，在语音通话场景下，手机设备的通话装置将恢复为听筒。使用Promise异步回调。

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastPickerHelper-resetCommunicationDevice(): Promise<void>--><!--Device-AVCastPickerHelper-resetCommunicationDevice(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

## select

```TypeScript
select(options?: AVCastPickerOptions): Promise<void>
```

通过选择模式拉起AVCastPicker界面，用户可以选择投播设备。接口采用Promise异步返回形式，传入可选参数AVCastPickerOptions对象，无返回结果。

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastPickerHelper-select(options?: AVCastPickerOptions): Promise<void>--><!--Device-AVCastPickerHelper-select(options?: AVCastPickerOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AVCastPickerOptions](arkts-avsession-avsession-avcastpickeroptions-i.md) | 否 | AVCastPicker选择选项。无此参数时，以AVCastPickerOptions默认值拉起。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。当命令发送成功，无返回结果，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |

