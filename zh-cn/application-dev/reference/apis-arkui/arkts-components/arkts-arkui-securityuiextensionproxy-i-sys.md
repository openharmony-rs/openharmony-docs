# SecurityUIExtensionProxy（系统接口）

用于在双方建立连接成功后，向被拉起的Ability发送数据，以及订阅和取消订阅事件回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-declare interface SecurityUIExtensionProxy--><!--Device-unnamed-declare interface SecurityUIExtensionProxy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## off_asyncReceiverRegister

```TypeScript
off(type: 'asyncReceiverRegister', callback?: Callback<UIExtensionProxy>): void
```

取消订阅被拉起的Ability异步注册时触发的回调。使用callback异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionProxy-off(type: 'asyncReceiverRegister', callback?: Callback<UIExtensionProxy>): void--><!--Device-SecurityUIExtensionProxy-off(type: 'asyncReceiverRegister', callback?: Callback<UIExtensionProxy>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'asyncReceiverRegister' | 是 | 固定填'asyncReceiverRegister'，取消订阅被拉起的Ability异步注册时触发的回调。 |
| callback | Callback&lt;UIExtensionProxy&gt; | 否 | 回调函数。为空时取消订阅所有异步注册的回调。非空时取消订阅指定的异步注册回调。 |

## off_syncReceiverRegister

```TypeScript
off(type: 'syncReceiverRegister', callback?: Callback<UIExtensionProxy>): void
```

取消订阅被拉起的Ability同步注册时触发的回调。使用callback异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionProxy-off(type: 'syncReceiverRegister', callback?: Callback<UIExtensionProxy>): void--><!--Device-SecurityUIExtensionProxy-off(type: 'syncReceiverRegister', callback?: Callback<UIExtensionProxy>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'syncReceiverRegister' | 是 | 固定填'syncReceiverRegister'，取消订阅被拉起的Ability同步注册时触发的回调。 |
| callback | Callback&lt;UIExtensionProxy&gt; | 否 | 回调函数。为空时取消订阅所有同步注册的回调。非空时取消订阅指定的同步注册回调。 |

## on_asyncReceiverRegister

```TypeScript
on(type: 'asyncReceiverRegister', callback: Callback<UIExtensionProxy>): void
```

在双方建立连接成功后，订阅被拉起的Ability异步注册时触发的回调。使用callback异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionProxy-on(type: 'asyncReceiverRegister', callback: Callback<UIExtensionProxy>): void--><!--Device-SecurityUIExtensionProxy-on(type: 'asyncReceiverRegister', callback: Callback<UIExtensionProxy>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'asyncReceiverRegister' | 是 | 固定填'asyncReceiverRegister'，代表订阅被拉起的Ability异步注册时触发的回调。 |
| callback | Callback&lt;UIExtensionProxy&gt; | 是 | 回调函数。订阅被拉起的Ability注册setReceiveDataCallback后触发的回调。 |

## on_syncReceiverRegister

```TypeScript
on(type: 'syncReceiverRegister', callback: Callback<UIExtensionProxy>): void
```

在双方建立连接成功后，订阅被拉起的Ability同步注册时触发的回调。使用callback异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionProxy-on(type: 'syncReceiverRegister', callback: Callback<UIExtensionProxy>): void--><!--Device-SecurityUIExtensionProxy-on(type: 'syncReceiverRegister', callback: Callback<UIExtensionProxy>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'syncReceiverRegister' | 是 | 固定填'syncReceiverRegister'，代表订阅被拉起的Ability同步注册时触发的回调。 |
| callback | Callback&lt;UIExtensionProxy&gt; | 是 | 回调函数。被拉起的Ability注册setReceiveDataForResultCallback后触发的回调。 |

## send

```TypeScript
send(data: Record<string, Object>): void
```

用于在双方建立连接成功后，向被拉起的Ability发送数据，提供异步发送能力。数据将被扩展Ability通过setReceiveDataCallback接收处理。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionProxy-send(data: Record<string, Object>): void--><!--Device-SecurityUIExtensionProxy-send(data: Record<string, Object>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | 是 | 异步发送给被拉起的Ability的数据。 |

## sendSync

```TypeScript
sendSync(data: Record<string, Object>): Record<string, Object>
```

用于在双方建立连接成功后，向被拉起的Ability同步发送数据，数据将被拉起的Ability通过setReceiveDataForResultCallback处理并返回结果。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionProxy-sendSync(data: Record<string, Object>): Record<string, Object>--><!--Device-SecurityUIExtensionProxy-sendSync(data: Record<string, Object>): Record<string, Object>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | 是 | 同步发送给被拉起的Ability的数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Record&lt;string, Object&gt; | 被拉起的Ability对同步发送请求处理后返回的响应数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100011](../errorcode-uiextension.md#100011-未注册同步回调) | 没有注册响应该请求的回调。 |
| [100012](../errorcode-uiextension.md#100012-数据发送失败) | 传输数据失败。 |

