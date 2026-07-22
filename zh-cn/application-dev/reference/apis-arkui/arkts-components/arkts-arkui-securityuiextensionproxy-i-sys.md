# SecurityUIExtensionProxy（系统接口）

该接口用于向UIExtensionAbility发送数据。<br/>当UIExtensionAbility连接成功时，<br/>它从UIExtensionComponent的onRemoteReady回调中返回。

**起始版本：** 26.0.0

<!--Device-unnamed-declare interface SecurityUIExtensionProxy--><!--Device-unnamed-declare interface SecurityUIExtensionProxy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## off('asyncReceiverRegister')

```TypeScript
off(type: 'asyncReceiverRegister', callback?: Callback<UIExtensionProxy>): void
```

注销监听器，该监听器监听UIExtensionAbility注册的异步数据接收回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionProxy-off(type: 'asyncReceiverRegister', callback?: Callback<UIExtensionProxy>): void--><!--Device-SecurityUIExtensionProxy-off(type: 'asyncReceiverRegister', callback?: Callback<UIExtensionProxy>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'asyncReceiverRegister' | 是 | 监听事件的类型。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;UIExtensionProxy&gt; | 否 | 监听事件的回调。 |

## off('syncReceiverRegister')

```TypeScript
off(type: 'syncReceiverRegister', callback?: Callback<UIExtensionProxy>): void
```

注销监听器，该监听器监听UIExtensionAbility注册的同步数据接收回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionProxy-off(type: 'syncReceiverRegister', callback?: Callback<UIExtensionProxy>): void--><!--Device-SecurityUIExtensionProxy-off(type: 'syncReceiverRegister', callback?: Callback<UIExtensionProxy>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'syncReceiverRegister' | 是 | 监听事件的类型。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;UIExtensionProxy&gt; | 否 | 监听事件的回调。 |

## on('asyncReceiverRegister')

```TypeScript
on(type: 'asyncReceiverRegister', callback: Callback<UIExtensionProxy>): void
```

注册监听器，监听UIExtensionAbility注册的异步数据接收回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionProxy-on(type: 'asyncReceiverRegister', callback: Callback<UIExtensionProxy>): void--><!--Device-SecurityUIExtensionProxy-on(type: 'asyncReceiverRegister', callback: Callback<UIExtensionProxy>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'asyncReceiverRegister' | 是 | 表示事件的类型。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;UIExtensionProxy&gt; | 是 | 监听事件的回调。 |

## on('syncReceiverRegister')

```TypeScript
on(type: 'syncReceiverRegister', callback: Callback<UIExtensionProxy>): void
```

注册监听器，监听UIExtensionAbility注册的同步数据接收回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionProxy-on(type: 'syncReceiverRegister', callback: Callback<UIExtensionProxy>): void--><!--Device-SecurityUIExtensionProxy-on(type: 'syncReceiverRegister', callback: Callback<UIExtensionProxy>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'syncReceiverRegister' | 是 | 表示事件的类型。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;UIExtensionProxy&gt; | 是 | 监听事件的回调。 |

## send

```TypeScript
send(data: Record<string, Object>): void
```

该接口用于向UIExtensionAbility发送数据。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionProxy-send(data: Record<string, Object>): void--><!--Device-SecurityUIExtensionProxy-send(data: Record<string, Object>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | 是 |  |

## sendSync

```TypeScript
sendSync(data: Record<string, Object>): Record<string, Object>
```

该接口用于向UIExtensionAbility发送数据，并以阻塞方式等待结果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionProxy-sendSync(data: Record<string, Object>): Record<string, Object>--><!--Device-SecurityUIExtensionProxy-sendSync(data: Record<string, Object>): Record<string, Object>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | 是 | 发送给UIExtensionAbility的数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Record&lt;string, Object&gt; | data - 从UIExtensionAbility传输回来的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100011](../errorcode-uiextension.md#100011-未注册同步回调) | 没有注册响应该请求的回调。 |
| [100012](../errorcode-uiextension.md#100012-数据发送失败) | 传输数据失败。 |

