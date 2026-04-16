# @ohos.inputMethodSystemPanelManager (输入法系统面板管理器)(系统接口)
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->

本模块提供输入法系统面板管理功能，用于输入法系统面板和系统预置输入法应用之间的通信和状态同步。

**起始版本：** 26.0.0

> **说明：**
>
> 本模块接口为系统接口。
>
> 本模块仅支持Stage模型。

## 导入模块

```ts
import { inputMethodSystemPanelManager } from '@kit.IMEKit';
```

## SystemPanelStatus

系统面板状态信息。

系统面板状态信息用于描述当前系统面板的输入类型、面板标志、升起状态和功能按钮需求。当系统面板状态发生变化时，会通过[onSystemPanelStatusChange](#inputmethodsystempanelmanageronsystempanelstatuschange) 接口通知订阅者。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| inputType | [InputMethodInputType](#inputmethodinputtype) | 否 | 否 | 输入法的输入类型。 |
| panelFlag | [PanelFlag](js-apis-inputmethod-panel.md#panelflag) | 否 | 否 | 输入法软键盘面板的面板标志，表示面板的显示状态（固定态、悬浮态或候选词态）。 |
| isPanelRaised | boolean | 否 | 否 | 系统面板是否需要底部抬高，true表示面板需要底部抬高，false表示不需要。 |
| needFuncButton | boolean | 否 | 否 | 系统面板是否需要功能按钮，true表示面板需要显示功能按钮，false表示不需要。 |

## InputMethodInputType

输入类型枚举。

输入类型枚举用于标识系统面板支持的输入模式。不同的输入类型对应不同的输入场景和面板布局。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| NONE | -1 | 无输入类型，不在任何输入类型。 |
| CAMERA_INPUT | 0 | 相机输入类型，表示系统处于相机输入模式，通常用于拍摄输入等场景。 |
| SECURITY_INPUT | 1 | 安全输入类型，表示系统面板处于安全输入模式，用于密码等敏感信息输入。 |
| VOICE_INPUT | 2 | 语音输入类型，表示系统面板处于语音输入模式，用于语音转文字输入。 |
| FLOATING_VOICE_INPUT | 3 | 悬浮语音输入类型，表示系统面板处于悬浮语音输入模式，以悬浮窗口形式提供语音输入功能。 |

## CommandDataType

type CommandDataType = number | string | boolean

表示私有数据类型，接口参数具体类型根据其功能而定。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

| 类型 | 说明 |
| -------- | -------- |
| number | 数字类型。 |
| string | 字符串类型。 |
| boolean | 布尔类型。 |

## inputMethodSystemPanelManager.onSystemPrivateCommand

onSystemPrivateCommand(callback: Callback\<Record\<string, CommandDataType\>\>): void

订阅系统预置输入法应用发送私有数据命令的事件。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | Callback\<Record\<string, [CommandDataType](#commanddatatype)\>\> | 是 | 回调函数，当输入法应用或系统服务发送私有数据命令时触发。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 202 | not system application. |

**示例：**

```ts
try {
  inputMethodSystemPanelManager.onSystemPrivateCommand((data) => {
    console.info('Received private command: ' + JSON.stringify(data));
  });
} catch (err) {
  console.error(`Failed to subscribe to private command. Code: ${err.code}, Message: ${err.message}`);
}
```

## inputMethodSystemPanelManager.offSystemPrivateCommand

offSystemPrivateCommand(callback?: Callback\<Record\<string, CommandDataType\>\>): void

取消订阅系统预置输入法应用发送私有数据命令的事件。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | Callback\<Record\<string, [CommandDataType](#commanddatatype)\>\> | 否 | 回调函数，如果不填，则取消订阅所有回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 202 | not system application. |

**示例：**

```ts
try {
  inputMethodSystemPanelManager.offSystemPrivateCommand();
} catch (err) {
  console.error(`Failed to unsubscribe from private command. Code: ${err.code}, Message: ${err.message}`);
}
```

## inputMethodSystemPanelManager.onSystemPanelStatusChange

onSystemPanelStatusChange(callback: Callback\<SystemPanelStatus\>): void

订阅系统面板状态变化事件。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | Callback\<[SystemPanelStatus](#systempanelstatus)\> | 是 | 回调函数，当系统面板状态变化时触发。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 202 | not system application. |

**示例：**

```ts
try {
  inputMethodSystemPanelManager.onSystemPanelStatusChange((status) => {
    console.info('Panel status changed: ' + JSON.stringify(status));
  });
} catch (err) {
  console.error(`Failed to subscribe to panel status change. Code: ${err.code}, Message: ${err.message}`);
}
```

## inputMethodSystemPanelManager.offSystemPanelStatusChange

offSystemPanelStatusChange(callback?: Callback\<SystemPanelStatus\>): void

取消订阅系统面板状态变化事件。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | Callback\<[SystemPanelStatus](#systempanelstatus)\> | 否 | 回调函数，如果不填，则取消订阅所有回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 202 | not system application. |

**示例：**

```ts
try {
  inputMethodSystemPanelManager.offSystemPanelStatusChange();
} catch (err) {
  console.error(`Failed to unsubscribe from panel status change. Code: ${err.code}, Message: ${err.message}`);
}
```

## inputMethodSystemPanelManager.sendPrivateCommand

sendPrivateCommand(commandData: Record\<string, CommandDataType\>): Promise\<void\>

发送私有命令给系统预置输入法应用。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| commandData | Record\<string, [CommandDataType](#commanddatatype)\> | 是 | 要发送的命令数据，最大大小32KB，最多5条。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise\<void\> | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 202 | not system application. |
| 12800026 | input method system panel error. Possible causes: 1. system panel not connected. 2. ipc failed due to large amount of data transferred or other reasons. 3. the caller is not system panel. |

**示例：**

```ts
try {
  let commandData: Record<string, inputMethodSystemPanelManager.CommandDataType> = {
    'key1': 1,
    'key2': true,
    'key3': '123',
  };
  inputMethodSystemPanelManager.sendPrivateCommand(commandData).then(() => {
    console.info('Private command sent successfully');
  }).catch((e: BusinessError) => {
    console.error(`Failed to send private command. Code: ${e.code}, Message: ${e.message}`);
  })
} catch (e) {
  console.error(`Failed to send private command. Code: ${e.code}, Message: ${e.message}`);
}
```

## inputMethodSystemPanelManager.connectSystemChannel

connectSystemChannel(): Promise\<void\>

连接系统通道，用于输入法系统面板和系统预置输入法应用之间的通信。仅允许系统输入法面板调用。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.CONNECT_IME_ABILITY

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise\<void\> | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | permissions check fails. |
| 202 | not system application. |
| 12800008 | input method manager service error. Possible causes: a system error, such as null pointer, IPC exception. |
| 12800026  | input method system panel error. Possible causes: 1. the system panel not connected.2. ipc failed due to the large amount of data transferred or other reasons. 3. the caller is not system panel.|

**示例：**

```ts
try {
  inputMethodSystemPanelManager.connectSystemChannel().then(() => {
    console.info('System channel connected successfully');
  }).catch((e: BusinessError) => {
    console.error(`Failed to connect system channel. Code: ${e.code}, Message: ${e.message}`);
  })
} catch (e) {
  console.error(`Failed to connect system channel. Code: ${e.code}, Message: ${e.message}`);
}
```
