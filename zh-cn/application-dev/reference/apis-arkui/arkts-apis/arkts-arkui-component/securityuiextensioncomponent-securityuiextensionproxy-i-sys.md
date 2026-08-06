# SecurityUIExtensionProxy（系统接口）

用于在双方建立连接成功后，向被拉起的Ability发送数据，以及订阅和取消订阅事件回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface SecurityUIExtensionProxy--><!--Device-unnamed-export declare interface SecurityUIExtensionProxy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## offAsyncReceiverRegister

```TypeScript
offAsyncReceiverRegister(callback?: Callback<SecurityUIExtensionProxy>): void
```

取消订阅被拉起的Ability发生异步注册的回调。使用callback异步回调。 AnonyMous Object Rectification

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionProxy-offAsyncReceiverRegister(callback?: Callback<SecurityUIExtensionProxy>): void--><!--Device-SecurityUIExtensionProxy-offAsyncReceiverRegister(callback?: Callback<SecurityUIExtensionProxy>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 否 | 回调函数。为空代表取消订阅所有扩展Ability异步注册后触发回调。非空代表取消订阅异步对应回调。ArkTS-Sta模式下，可传入undefined，表示取消所有回调。 |

## offSyncReceiverRegister

```TypeScript
offSyncReceiverRegister(callback?: Callback<SecurityUIExtensionProxy>): void
```

取消订阅被拉起的Ability发生同步注册的回调。使用callback异步回调。 AnonyMous Object Rectification

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionProxy-offSyncReceiverRegister(callback?: Callback<SecurityUIExtensionProxy>): void--><!--Device-SecurityUIExtensionProxy-offSyncReceiverRegister(callback?: Callback<SecurityUIExtensionProxy>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 否 | 回调函数。为空代表取消订阅所有扩展Ability同步注册后触发回调。非空代表取消订阅同步对应回调。ArkTS-Sta模式下，可传入undefined，表示取消所有回调。 |

## onAsyncReceiverRegister

```TypeScript
onAsyncReceiverRegister(callback: Callback<SecurityUIExtensionProxy>): void
```

订阅被拉起的Ability发生异步注册的回调。使用callback异步回调。 AnonyMous Object Rectification

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionProxy-onAsyncReceiverRegister(callback: Callback<SecurityUIExtensionProxy>): void--><!--Device-SecurityUIExtensionProxy-onAsyncReceiverRegister(callback: Callback<SecurityUIExtensionProxy>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | 回调函数。订阅扩展Ability注册setReceiveDataCallback后触发的回调。 |

## onSyncReceiverRegister

```TypeScript
onSyncReceiverRegister(callback: Callback<SecurityUIExtensionProxy>): void
```

订阅被拉起的Ability发生同步注册的回调。使用callback异步回调。 AnonyMous Object Rectification

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionProxy-onSyncReceiverRegister(callback: Callback<SecurityUIExtensionProxy>): void--><!--Device-SecurityUIExtensionProxy-onSyncReceiverRegister(callback: Callback<SecurityUIExtensionProxy>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | 回调函数。扩展Ability注册setReceiveDataForResultCallback后触发的回调。 |

## send

```TypeScript
send(data: Record<string, RecordData>): void
```

用于在双方建立连接成功后，向被拉起的Ability发送数据，提供异步发送能力。数据将被扩展Ability通过setReceiveDataCallback接收处理。 AnonyMous Object Rectification

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionProxy-send(data: Record<string, RecordData>): void--><!--Device-SecurityUIExtensionProxy-send(data: Record<string, RecordData>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, \_\_\_MD\_LINK\_USD\_0\_\_\_&gt; | 是 | 异步发送给被拉起的Ability的数据。 |

## sendSync

```TypeScript
sendSync(data: Record<string, RecordData>): Record<string, RecordData>
```

用于在双方建立连接成功后，向被拉起的Ability同步发送数据，数据将被拉起的Ability通过setReceiveDataForResultCallback处理并返回结果。 AnonyMous Object Rectification

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionProxy-sendSync(data: Record<string, RecordData>): Record<string, RecordData>--><!--Device-SecurityUIExtensionProxy-sendSync(data: Record<string, RecordData>): Record<string, RecordData>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, \_\_\_MD\_LINK\_USD\_0\_\_\_&gt; | 是 | 同步发送给被拉起的Ability的数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Record&lt;string, \_\_\_MD\_LINK\_USD\_0\_\_\_&gt; | data - 被拉起的Ability对同步发送请求处理后返回的响应数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100011](../../errorcode-uiextension.md#100011-未注册同步回调) | 没有注册响应该请求的回调。 |
| [100012](../../errorcode-uiextension.md#100012-数据发送失败) | 传输数据失败。 |

