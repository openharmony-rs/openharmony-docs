# Client

管理SSAP客户端。在调用ssap客户端方法之前，必须使用\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_创建ssap客户端实例。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-ssap-interface Client--><!--Device-ssap-interface Client-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## close

```TypeScript
close(): void
```

关闭客户端。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Client-close(): void--><!--Device-Client-close(): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003--星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## connect

```TypeScript
connect(): Promise<void>
```

连接服务端。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Client-connect(): Promise<void>--><!--Device-Client-connect(): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 返回promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003--星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## disconnect

```TypeScript
disconnect(): Promise<void>
```

断开或停止与服务端的连接。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Client-disconnect(): Promise<void>--><!--Device-Client-disconnect(): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 返回promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003--星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## getServices

```TypeScript
getServices(): Promise<Service[]>
```

开始发现服务端的所有服务。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Client-getServices(): Promise<Service[]>--><!--Device-Client-getServices(): Promise<Service[]>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Service[]&gt; | Returns the service list of the server. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003--星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## offConnectionStateChange

```TypeScript
offConnectionStateChange(callback?: Callback<ConnectionChangeState>): void
```

取消订阅客户端连接状态更改事件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Client-offConnectionStateChange(callback?: Callback<ConnectionChangeState>): void--><!--Device-Client-offConnectionStateChange(callback?: Callback<ConnectionChangeState>): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;ConnectionChangeState&gt; | 否 | 用于监听连接状态改变事件的回调。 |

## offMtuChange

ArkTS-Dyn:
```TypeScript
offMtuChange(callback?: Callback<number>): void
```

ArkTS-Sta:
```TypeScript
offMtuChange(callback?: Callback<int>): void
```

取消订阅MTU更改事件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Client-offMtuChange(callback?: Callback<int>): void--><!--Device-Client-offMtuChange(callback?: Callback<int>): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | ArkTS-Dyn: \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_2\_\_\_ArkTS-Sta：\_\_\_MD\_LINK\_USD\_1\_\_\_&lt;int&gt; | 否 | 用于监听mtu变化事件的回调。 |

## offPropertyChange

```TypeScript
offPropertyChange(callback?: Callback<Property>): void
```

取消订阅属性值更改事件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Client-offPropertyChange(callback?: Callback<Property>): void--><!--Device-Client-offPropertyChange(callback?: Callback<Property>): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Property&gt; | 否 | 用于监听属性值变更事件的回调。 |

## onConnectionStateChange

```TypeScript
onConnectionStateChange(callback: Callback<ConnectionChangeState>): void
```

订阅客户端连接状态更改事件。 只有授予了ohos.permission.NEARLINK\_ACCESS权限的应用程序才能访问此事件。 如果应用被赋予了ohos.permission.GET\_NEARLINK\_PEER\_MAC权限。 回调返回真实设备地址，否则返回随机设备地址。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Client-onConnectionStateChange(callback: Callback<ConnectionChangeState>): void--><!--Device-Client-onConnectionStateChange(callback: Callback<ConnectionChangeState>): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;ConnectionChangeState&gt; | 是 | 用于监听连接状态改变事件的回调。 |

## onMtuChange

ArkTS-Dyn:
```TypeScript
onMtuChange(callback: Callback<number>): void
```

ArkTS-Sta:
```TypeScript
onMtuChange(callback: Callback<int>): void
```

订阅MTU变化事件。 只有授予了ohos.permission.NEARLINK\_ACCESS权限的应用程序才能访问此事件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Client-onMtuChange(callback: Callback<int>): void--><!--Device-Client-onMtuChange(callback: Callback<int>): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | ArkTS-Dyn: \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_2\_\_\_ArkTS-Sta：\_\_\_MD\_LINK\_USD\_1\_\_\_&lt;int&gt; | 是 | 用于监听mtu变化事件的回调。 |

## onPropertyChange

```TypeScript
onPropertyChange(callback: Callback<Property>): void
```

订阅属性值变更事件。 只有授予了ohos.permission.NEARLINK\_ACCESS权限的应用程序才能访问此事件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Client-onPropertyChange(callback: Callback<Property>): void--><!--Device-Client-onPropertyChange(callback: Callback<Property>): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Property&gt; | 是 | 用于监听属性值更改事件的回调。 |

## readProperty

```TypeScript
readProperty(property: Property): Promise<Property>
```

读取服务端的属性。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Client-readProperty(property: Property): Promise<Property>--><!--Device-Client-readProperty(property: Property): Promise<Property>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| property | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指示要读取的属性 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Property&gt; | 返回属性值Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003--星闪关闭) | NearLink disabled. |
| [36100043](../errorcode-nearlink-service.md#36100043-无效uuid) | Invalid UUID in property. |
| [36100044](../errorcode-nearlink-service.md#36100044-禁止使用星闪标准服务uuid) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## requestMtuSize

ArkTS-Dyn:
```TypeScript
requestMtuSize(mtu: number): Promise<void>
```

ArkTS-Sta:
```TypeScript
requestMtuSize(mtu: int): Promise<void>
```

与服务端协商MTU大小。 协商结果需要通过订阅MTU事件获取。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Client-requestMtuSize(mtu: int): Promise<void>--><!--Device-Client-requestMtuSize(mtu: int): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mtu | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 最大传输单元。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_单位为：字节。取值限定为整数。取值约束：建议范围[22,1024]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 返回promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003--星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## setPropertyNotification

```TypeScript
setPropertyNotification(property: Property, enable: boolean): Promise<void>
```

启用或禁用属性值变更通知。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Client-setPropertyNotification(property: Property, enable: boolean): Promise<void>--><!--Device-Client-setPropertyNotification(property: Property, enable: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| property | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要通知的属性 |
| enable | boolean | 是 | 指定是否启用属性的通知 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 返回promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003--星闪关闭) | NearLink disabled. |
| [36100043](../errorcode-nearlink-service.md#36100043-无效uuid) | Invalid UUID in property. |
| [36100044](../errorcode-nearlink-service.md#36100044-禁止使用星闪标准服务uuid) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

## writeProperty

```TypeScript
writeProperty(property: Property, writeType: PropertyWriteType): Promise<void>
```

写入服务端的属性。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Client-writeProperty(property: Property, writeType: PropertyWriteType): Promise<void>--><!--Device-Client-writeProperty(property: Property, writeType: PropertyWriteType): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| property | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指示要写入的属性 |
| writeType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 写类型 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise用于返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003--星闪关闭) | NearLink disabled. |
| [36100043](../errorcode-nearlink-service.md#36100043-无效uuid) | Invalid UUID in property. |
| [36100044](../errorcode-nearlink-service.md#36100044-禁止使用星闪标准服务uuid) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

