# Server

管理SSAP服务端。在调用SSAP服务端方法之前，必须使用{@link createServer}创建SSAP服务端实例。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## addService

```TypeScript
addService(service: Service): void
```

添加SSAP服务。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| service | Service | 是 | 需要添加并注册ssap服务 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| 36100003 | NearLink disabled. |
| 36100043 | Invalid UUID. |
| 36100044 | NearLink standard UUID not allowed. |
| 36100099 | Operation failed. |

## close

```TypeScript
close(): void
```

关闭此{@code Server}对象并注销其回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| 36100003 | NearLink disabled. |
| 36100099 | Operation failed. |

## notifyPropertyChanged

```TypeScript
notifyPropertyChanged(address: string, property: Property): Promise<void>
```

通知客户端此服务端的属性值发生了变化。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| address | string | 是 | 设备地址。<br>长度必须为17，由16进制数字和冒号组成，形如 "11:22:33:AA:BB:FF"。 |
| property | Property | 是 | 指示要通知的属性 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 返回promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| 36100003 | NearLink disabled. |
| 36100041 | Invalid address. |
| 36100043 | Invalid UUID in property. |
| 36100044 | NearLink standard UUID not allowed. |
| 36100099 | Operation failed. |

## offConnectionStateChange

```TypeScript
offConnectionStateChange(callback?: Callback<ConnectionChangeState>): void
```

取消订阅服务器连接状态更改事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;ConnectionChangeState&gt; | 否 | 用于监听连接状态改变事件的回调。 |

## offMtuChange

```TypeScript
offMtuChange(callback?: Callback<number>): void
```

取消订阅MTU更改事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;number&gt; | 否 | 用于监听mtu变化事件的回调。 |

## offPropertyRead

```TypeScript
offPropertyRead(callback?: Callback<PropertyReadRequest>): void
```

取消订阅来自客户端的属性读取事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;PropertyReadRequest&gt; | 否 | 用于监听属性操作事件的回调。 |

## offPropertyWrite

```TypeScript
offPropertyWrite(callback?: Callback<PropertyWriteRequest>): void
```

取消订阅来自客户端的属性写入事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;PropertyWriteRequest&gt; | 否 | 用于监听属性操作事件的回调。 |

## onConnectionStateChange

```TypeScript
onConnectionStateChange(callback: Callback<ConnectionChangeState>): void
```

订阅服务器连接状态更改事件。

只有授予了ohos.permission.NEARLINK_ACCESS权限的应用程序才能访问此事件。
如果应用被赋予了ohos.permission.GET_NEARLINK_PEER_MAC权限。
回调返回真实设备地址，否则返回随机设备地址。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;ConnectionChangeState&gt; | 是 | 用于监听连接状态改变事件的回调。 |

## onMtuChange

```TypeScript
onMtuChange(callback: Callback<number>): void
```

订阅MTU变化事件。

只有授予了ohos.permission.NEARLINK_ACCESS权限的应用程序才能访问此事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;number&gt; | 是 | 用于监听mtu变化事件的回调。 |

## onPropertyRead

```TypeScript
onPropertyRead(callback: Callback<PropertyReadRequest>): void
```

从客户端订阅属性读取事件。

只有授予了ohos.permission.NEARLINK_ACCESS权限的应用程序才能访问此事件。
如果应用被赋予了ohos.permission.GET_NEARLINK_PEER_MAC权限。
回调返回真实设备地址，否则返回随机设备地址。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;PropertyReadRequest&gt; | 是 | 用于监听属性操作事件的回调。 |

## onPropertyWrite

```TypeScript
onPropertyWrite(callback: Callback<PropertyWriteRequest>): void
```

从客户端订阅属性写入事件。

只有授予了ohos.permission.NEARLINK_ACCESS权限的应用程序才能访问此事件。
如果应用被赋予了ohos.permission.GET_NEARLINK_PEER_MAC权限。
回调返回真实设备地址，否则返回随机设备地址。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;PropertyWriteRequest&gt; | 是 | 用于监听属性操作事件的回调。 |

## removeService

```TypeScript
removeService(serviceUuid: string): void
```

删除指定的SSAP服务。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| serviceUuid | string | 是 | 要删除的特定SSAP服务<br>长度必须为36，由16进制数字字符和连字符共36个字符组成，形如“FFFFFFFF-1234-5678-ABCD-000000001234”，代表128比特标识。<br>禁止使用星闪标准服务UUID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| 36100003 | NearLink disabled. |
| 36100043 | Invalid UUID. |
| 36100044 | NearLink standard UUID not allowed. |
| 36100099 | Operation failed. |

## sendResponse

```TypeScript
sendResponse(response: ServerResponse): void
```

响应客户端的读或写请求。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| response | ServerResponse | 是 | 表示响应。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| 36100003 | NearLink disabled. |
| 36100041 | Invalid address. |
| 36100099 | Operation failed. |

