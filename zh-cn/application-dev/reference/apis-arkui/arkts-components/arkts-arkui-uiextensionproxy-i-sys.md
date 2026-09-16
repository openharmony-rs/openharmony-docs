# UIExtensionProxy（系统接口）

用于在双方建立连接成功后，组件使用方将数据发送给被拉起的Ability，并订阅和取消订阅扩展Ability的注册事件。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## off('asyncReceiverRegister')

```TypeScript
off(type: 'asyncReceiverRegister', callback?: Callback<UIExtensionProxy>): void
```

用于在双方建立连接成功后，组件使用方取消订阅被拉起的Ability发生异步注册的场景。本方法与on('asyncReceiverRegister')配合使用，用于取消通过on('asyncReceiverRegister')注册的订阅。当不再需要监听异步注册事件时（如组件销毁前），应调用本方法取消订阅，避免回调无法释放。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'asyncReceiverRegister' | 是 | 事件类型，取值为'asyncReceiverRegister'，表示取消订阅扩展Ability发生异步注册回调。 |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;[UIExtensionProxy](arkts-arkui-uiextensionproxy-i-sys.md)&gt; | 否 | 回调函数。为空代表取消订阅所有扩展Ability异步注册后触发回调；非空代表取消订阅对应的异步注册回调。<br>**适用版本：** 18 |

## off('syncReceiverRegister')

```TypeScript
off(type: 'syncReceiverRegister', callback?: Callback<UIExtensionProxy>): void
```

用于在双方建立连接成功后，组件使用方取消订阅被拉起的Ability发生异步注册的场景。本方法与on('asyncReceiverRegister')配合使用，用于取消通过on('asyncReceiverRegister')注册的订阅。当不再需要监听异步注册事件时（如组件销毁前），应调用本方法取消订阅，避免回调无法释放。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'syncReceiverRegister' | 是 | 事件类型，取值为'asyncReceiverRegister'，表示取消订阅扩展Ability发生异步注册回调。 |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;[UIExtensionProxy](arkts-arkui-uiextensionproxy-i-sys.md)&gt; | 否 | 回调函数。为空代表取消订阅所有扩展Ability同步注册后触发回调；非空代表取消订阅对应的同步注册回调。<br>**适用版本：** 18 |

## on('asyncReceiverRegister')

```TypeScript
on(type: 'asyncReceiverRegister', callback: Callback<UIExtensionProxy>): void
```

用于在双方建立连接成功后，组件使用方订阅被拉起的Ability发生异步注册的场景。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'asyncReceiverRegister' | 是 | 事件类型，取值为'asyncReceiverRegister'，表示订阅扩展Ability发生异步注册回调。 |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;[UIExtensionProxy](arkts-arkui-uiextensionproxy-i-sys.md)&gt; | 是 | 回调函数。订阅扩展Ability注册setReceiveDataCallback后触发的回调。<br>**适用版本：** 18 |

## on('syncReceiverRegister')

```TypeScript
on(type: 'syncReceiverRegister', callback: Callback<UIExtensionProxy>): void
```

用于在双方建立连接成功后，组件使用方订阅被拉起的Ability发生异步注册的场景。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'syncReceiverRegister' | 是 | 事件类型，取值为'asyncReceiverRegister'，表示订阅扩展Ability发生异步注册回调。 |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;[UIExtensionProxy](arkts-arkui-uiextensionproxy-i-sys.md)&gt; | 是 | 回调函数。订阅扩展Ability注册setReceiveDataCallback后触发的回调。<br>**适用版本：** 18 |

## send

```TypeScript
send(data: Record<string, Object>): void
```

用于在双方建立连接成功后，组件使用方将数据发送给被拉起的Ability的场景，提供异步发送数据。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | 是 | 异步发送给被拉起的UIExtensionAbility的数据。API version 18之前的版本，data的类型为Object。 |

## sendSync

```TypeScript
sendSync(data: Record<string, Object>): Record<string, Object>
```

用于在双方建立连接成功后，组件使用方将数据发送给被拉起的Ability的场景，提供同步发送数据。以下错误码的详细介绍请参见UIExtension错误码。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | 是 | 同步发送给被拉起的UIExtensionAbility的数据。API version 18之前的版本，data的类型为Object。<br>**适用版本：** 18 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| object | 扩展Ability回复的数据。<br>**适用版本：** 11 - 17 |
| Record&lt;string, Object&gt; | 扩展Ability回复的数据。<br>**适用版本：** 18 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100011](../errorcode-uiextension.md#100011-未注册同步回调) | No callback has been registered to respond to this request. |
| [100012](../errorcode-uiextension.md#100012-数据发送失败) | Transferring data failed. |
