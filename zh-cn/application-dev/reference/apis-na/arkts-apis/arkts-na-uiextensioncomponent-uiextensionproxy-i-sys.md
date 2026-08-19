# UIExtensionProxy（系统接口）

用于在双方建立连接成功后，组件使用方将数据发送给被拉起的Ability，并订阅和取消订阅扩展Ability的注册事件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface UIExtensionProxy--><!--Device-unnamed-export declare interface UIExtensionProxy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## offAsyncReceiverRegister

```TypeScript
offAsyncReceiverRegister(callback?: Callback<UIExtensionProxy>): void
```

注销监听UIExtensionAbility注册异步数据接收回调的监听器。 AnonyMous Object Rectification

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionProxy-offAsyncReceiverRegister(callback?: Callback<UIExtensionProxy>): void--><!--Device-UIExtensionProxy-offAsyncReceiverRegister(callback?: Callback<UIExtensionProxy>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[UIExtensionProxy](arkts-na-uiextensioncomponent-uiextensionproxy-i-sys.md)&gt; | 否 | 监听事件的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 非系统应用不允许使用系统API。 |

## offSyncReceiverRegister

```TypeScript
offSyncReceiverRegister(callback?: Callback<UIExtensionProxy>): void
```

注销监听UIExtensionAbility注册同步数据接收回调的监听器。 AnonyMous Object Rectification

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionProxy-offSyncReceiverRegister(callback?: Callback<UIExtensionProxy>): void--><!--Device-UIExtensionProxy-offSyncReceiverRegister(callback?: Callback<UIExtensionProxy>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[UIExtensionProxy](arkts-na-uiextensioncomponent-uiextensionproxy-i-sys.md)&gt; | 否 | 监听事件的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 非系统应用不允许使用系统API。 |

## onAsyncReceiverRegister

```TypeScript
onAsyncReceiverRegister(callback: Callback<UIExtensionProxy>): void
```

注册监听器，用于监听UIExtensionAbility注册异步数据接收回调。 AnonyMous Object Rectification

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionProxy-onAsyncReceiverRegister(callback: Callback<UIExtensionProxy>): void--><!--Device-UIExtensionProxy-onAsyncReceiverRegister(callback: Callback<UIExtensionProxy>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[UIExtensionProxy](arkts-na-uiextensioncomponent-uiextensionproxy-i-sys.md)&gt; | 是 | 监听事件的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 非系统应用不允许使用系统API。 |

## onSyncReceiverRegister

```TypeScript
onSyncReceiverRegister(callback: Callback<UIExtensionProxy>): void
```

注册监听器，用于监听UIExtensionAbility注册同步数据接收回调。 AnonyMous Object Rectification

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionProxy-onSyncReceiverRegister(callback: Callback<UIExtensionProxy>): void--><!--Device-UIExtensionProxy-onSyncReceiverRegister(callback: Callback<UIExtensionProxy>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[UIExtensionProxy](arkts-na-uiextensioncomponent-uiextensionproxy-i-sys.md)&gt; | 是 | 监听事件的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 非系统应用不允许使用系统API。 |

## send

```TypeScript
send(data: Record<string, RecordData>): void
```

用于在双方建立连接成功后，组件使用方将数据发送给被拉起的Ability的场景，提供异步发送数据。 AnonyMous Object Rectification

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionProxy-send(data: Record<string, RecordData>): void--><!--Device-UIExtensionProxy-send(data: Record<string, RecordData>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, [RecordData](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-recorddata-t.md)&gt; | 是 | 异步发送给被拉起的UIExtensionAbility的数据。API version 18之前的版本，data的类型为Object。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 非系统应用不允许使用系统API。 |

## sendSync

```TypeScript
sendSync(data: Record<string, RecordData>): Record<string, RecordData>
```

用于在双方建立连接成功后，组件使用方将数据发送给被拉起的Ability的场景，提供同步发送数据。 AnonyMous Object Rectification

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionProxy-sendSync(data: Record<string, RecordData>): Record<string, RecordData>--><!--Device-UIExtensionProxy-sendSync(data: Record<string, RecordData>): Record<string, RecordData>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, [RecordData](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-recorddata-t.md)&gt; | 是 | 同步发送给被拉起的UIExtensionAbility的数据。API version 18之前的版本，data的类型为Object。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Record&lt;string, [RecordData](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-recorddata-t.md)&gt; | data - 扩展Ability回复的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100011](../../apis-arkui/errorcode-uiextension.md#100011-未注册同步回调) | 没有注册响应该请求的回调。 |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 非系统应用不允许使用系统API。 |
| [100012](../../apis-arkui/errorcode-uiextension.md#100012-数据发送失败) | 传输数据失败。 |

