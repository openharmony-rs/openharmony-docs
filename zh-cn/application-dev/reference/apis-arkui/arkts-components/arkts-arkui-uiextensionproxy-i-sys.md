# UIExtensionProxy(System API)（系统接口）

该接口用于向UIExtensionAbility发送数据。<br/> 当UIExtensionAbility连接成功时，<br/> 它从UIExtensionComponent的onRemoteReady回调中返回。

**起始版本：** 10

<!--Device-unnamed-declare interface UIExtensionProxy--><!--Device-unnamed-declare interface UIExtensionProxy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## off('asyncReceiverRegister')

```TypeScript
off(type: 'asyncReceiverRegister', callback?: Callback<UIExtensionProxy>): void
```

注销监听UIExtensionAbility注册异步数据接收回调的监听器。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionProxy-off(type: 'asyncReceiverRegister', callback?: Callback<UIExtensionProxy>): void--><!--Device-UIExtensionProxy-off(type: 'asyncReceiverRegister', callback?: Callback<UIExtensionProxy>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'asyncReceiverRegister' | 是 | 事件类型，取值为'asyncReceiverRegister'，表示取消订阅扩展Ability发生异步注册回调。 |
| callback | Callback&lt;[UIExtensionProxy](arkts-arkui-uiextensionproxy-i-sys.md)&gt; | 否 | 回调函数。为空代表取消订阅所有扩展Ability异步注册后触发回调；非空代表取消订阅对应的异步注册回调。<br>**起始版本：** 18 |

## off('syncReceiverRegister')

```TypeScript
off(type: 'syncReceiverRegister', callback?: Callback<UIExtensionProxy>): void
```

注销监听UIExtensionAbility注册同步数据接收回调的监听器。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionProxy-off(type: 'syncReceiverRegister', callback?: Callback<UIExtensionProxy>): void--><!--Device-UIExtensionProxy-off(type: 'syncReceiverRegister', callback?: Callback<UIExtensionProxy>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'syncReceiverRegister' | 是 | 事件类型，取值为'syncReceiverRegister'，表示取消订阅扩展Ability发生同步注册回调。 |
| callback | Callback&lt;[UIExtensionProxy](arkts-arkui-uiextensionproxy-i-sys.md)&gt; | 否 | 回调函数。为空代表取消订阅所有扩展Ability同步注册后触发回调；非空代表取消订阅对应的同步注册回调。<br>**起始版本：** 18 |

## on('asyncReceiverRegister')

```TypeScript
on(type: 'asyncReceiverRegister', callback: Callback<UIExtensionProxy>): void
```

注册监听器，用于监听UIExtensionAbility注册异步数据接收回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionProxy-on(type: 'asyncReceiverRegister', callback: Callback<UIExtensionProxy>): void--><!--Device-UIExtensionProxy-on(type: 'asyncReceiverRegister', callback: Callback<UIExtensionProxy>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'asyncReceiverRegister' | 是 | 事件类型，取值为'asyncReceiverRegister'，表示订阅扩展Ability发生异步注册回调。 |
| callback | Callback&lt;[UIExtensionProxy](arkts-arkui-uiextensionproxy-i-sys.md)&gt; | 是 | 回调函数。扩展Ability注册setReceiveDataCallback后触发的回调。<br>**起始版本：** 18 |

## on('syncReceiverRegister')

```TypeScript
on(type: 'syncReceiverRegister', callback: Callback<UIExtensionProxy>): void
```

注册监听器，用于监听UIExtensionAbility注册同步数据接收回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionProxy-on(type: 'syncReceiverRegister', callback: Callback<UIExtensionProxy>): void--><!--Device-UIExtensionProxy-on(type: 'syncReceiverRegister', callback: Callback<UIExtensionProxy>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'syncReceiverRegister' | 是 | 事件类型，取值为'syncReceiverRegister'，表示订阅扩展Ability发生同步注册回调。 |
| callback | Callback&lt;[UIExtensionProxy](arkts-arkui-uiextensionproxy-i-sys.md)&gt; | 是 | 回调函数。扩展Ability注册setReceiveDataForResultCallback后触发的回调。<br>**起始版本：** 18 |

## send

```TypeScript
send(data: Record<string, Object>): void
```

该接口用于向UIExtensionAbility发送数据。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionProxy-send(data: Record<string, Object>): void--><!--Device-UIExtensionProxy-send(data: Record<string, Object>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | 是 | 异步发送给被拉起的UIExtensionAbility的数据。 API version 18之前的版本，data的类型为Object。<br>**起始版本：** 18 |

## sendSync

```TypeScript
sendSync(data: Record<string, Object>): Record<string, Object>
```

该接口用于向UIExtensionAbility发送数据，并以阻塞方式等待结果。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionProxy-sendSync(data: Record<string, Object>): Record<string, Object>--><!--Device-UIExtensionProxy-sendSync(data: Record<string, Object>): Record<string, Object>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | 是 | 发送给UIExtensionAbility的数据。<br>**起始版本：** 18 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| object | data - 从UIExtensionAbility传输回来的数据<br>**适用版本：** 11 - 17 |
| Record&lt;string, Object&gt; | data - 从UIExtensionAbility传输回来的数据。<br>**适用版本：** 18+ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100011](../errorcode-uiextension.md#100011-未注册同步回调) | 没有注册响应该请求的回调。 |
| [100012](../errorcode-uiextension.md#100012-数据发送失败) | 传输数据失败。 |

