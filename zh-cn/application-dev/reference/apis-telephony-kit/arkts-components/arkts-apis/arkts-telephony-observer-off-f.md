# off

## 导入模块

```TypeScript
import { observer } from '@kit.TelephonyKit';
```

## off('networkStateChange')

```TypeScript
function off(type: 'networkStateChange', callback?: Callback<NetworkState>): void
```

取消订阅网络状态变化事件，使用callback方式作为异步方法。

> **说明：** 
> 
> 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.StateRegistry

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'networkStateChange' | 是 | 网络状态变化事件，参数固定为'networkStateChange'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NetworkState](arkts-telephony-observer-networkstate-t.md)&gt; | 否 | 回调函数，返回网络状态对象。参考radio的[NetworkState](arkts-telephony-radio-networkstate-i.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |


## off('signalInfoChange')

```TypeScript
function off(type: 'signalInfoChange', callback?: Callback<Array<SignalInformation>>): void
```

取消订阅信号状态变化事件，使用callback方式作为异步方法。

> **说明：** 
> 
> 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.StateRegistry

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'signalInfoChange' | 是 | 信号状态变化事件，参数固定为'signalInfoChange'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[SignalInformation](arkts-telephony-observer-signalinformation-t.md)&gt;&gt; | 否 | 回调函数，返回信号强度对象。参考radio的[SignalInformation](arkts-telephony-radio-signalinformation-i.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |


## off('cellularDataConnectionStateChange')

```TypeScript
function off(type: 'cellularDataConnectionStateChange', callback?: Callback<DataConnectionStateInfo>): void
```

移除订阅蜂窝数据链路连接状态，使用callback方式作为异步方法。

> **说明：** 
> 
> 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.StateRegistry

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cellularDataConnectionStateChange' | 是 | 蜂窝数据链路连接状态事件，参数固定为'cellularDataConnectionStateChange'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DataConnectionStateInfo](arkts-telephony-observer-dataconnectionstateinfo-i.md)&gt; | 否 | 回调函数，返回蜂窝数据链路连接状态信息对象。参考data的[DataConnectState](arkts-telephony-data-dataconnectstate-e.md)，radio的[RadioTechnology](arkts-telephony-radio-radiotechnology-e.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |


## off('cellularDataFlowChange')

```TypeScript
function off(type: 'cellularDataFlowChange', callback?: Callback<DataFlowType>): void
```

移除订阅蜂窝数据业务的上下行数据流状态，使用callback方式作为异步方法。

> **说明：** 
> 
> 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.StateRegistry

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cellularDataFlowChange' | 是 | 蜂窝数据业务的上下行数据流状态事件，参数固定为'cellularDataFlowChange'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DataFlowType](arkts-telephony-observer-dataflowtype-t.md)&gt; | 否 | 回调函数，返回数据流状态对象。参考data的[DataFlowType](arkts-telephony-data-dataflowtype-e.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |


## off('callStateChange')

```TypeScript
function off(type: 'callStateChange', callback?: Callback<CallStateInfo>): void
```

取消订阅通话状态变化事件，使用callback方式作为异步方法。

> **说明：** 
> 
> 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.StateRegistry

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'callStateChange' | 是 | 通话状态变化事件，参数固定为'callStateChange'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CallStateInfo](arkts-telephony-observer-callstateinfo-i.md)&gt; | 否 | 回调函数，返回通话状态信息对象。参考call的[CallState](arkts-telephony-call-callstate-e.md)。<br>number：电话号码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |


## off('callStateChangeEx')

```TypeScript
function off(type: 'callStateChangeEx', callback?: Callback<TelCallState>): void
```

取消订阅通话状态变化拓展事件，使用callback方式作为异步方法。

> **说明：** 
> 
> 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 21

**系统能力：** SystemCapability.Telephony.StateRegistry

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'callStateChangeEx' | 是 | 通话状态变化事件，参数固定为'callStateChange'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[TelCallState](arkts-telephony-observer-telcallstate-t.md)&gt; | 否 | 回调函数，返回通话状态对象。参考call的[TelCallState](arkts-telephony-call-telcallstate-e.md)。<br> |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8800001](../errorcode-telephony.md#8800001-输入参数不在处理范围内) | Invalid parameter value. |
| [8800002](../errorcode-telephony.md#8800002-服务连接失败) | Service connection failed. |
| [8800003](../errorcode-telephony.md#8800003-系统内部错误) | System internal error. |
| [8800999](../errorcode-telephony.md#8800999-内部错误) | Unknown error. |


## off('simStateChange')

```TypeScript
function off(type: 'simStateChange', callback?: Callback<SimStateData>): void
```

移除订阅sim状态更改事件，使用callback方式作为异步方法。

> **说明：** 
> 
> 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.StateRegistry

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'simStateChange' | 是 | sim状态更改事件，参数固定为'simStateChange'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SimStateData](arkts-telephony-observer-simstatedata-i.md)&gt; | 否 | 回调函数，返回卡状态数据对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |


## off('iccAccountInfoChange')

```TypeScript
function off(type: 'iccAccountInfoChange', callback?: Callback<void>): void
```

移除订阅卡帐户变化事件，使用callback方式作为异步方法。

> **说明：** 
> 
> 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 10

**系统能力：** SystemCapability.Telephony.StateRegistry

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'iccAccountInfoChange' | 是 | 卡帐户变化事件，参数固定为'iccAccountInfoChange'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 回调函数。当卡账户改变成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
