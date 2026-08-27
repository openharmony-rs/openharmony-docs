# on（系统接口）

## 导入模块

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## on('netUidPolicyChange')

```TypeScript
function on(type: 'netUidPolicyChange', callback: Callback<NetUidPolicyInfo>): void
```

注册 policy 发生改变时的回调，使用 callback 异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'netUidPolicyChange' | 是 | 订阅的事件类型。'netUidPolicyChange'：注册policy发生改变事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NetUidPolicyInfo](arkts-network-policy-netuidpolicyinfo-i-sys.md)&gt; | 是 | 回调函数。注册 policy 发生改变时调用。<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |


## on('netUidRuleChange')

```TypeScript
function on(type: 'netUidRuleChange', callback: Callback<NetUidRuleInfo>): void
```

注册 rule 发生改变时的回调，使用 callback 异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'netUidRuleChange' | 是 | 订阅的事件类型。'netUidRuleChange'：注册rule发生改变事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NetUidRuleInfo](arkts-network-policy-netuidruleinfo-i-sys.md)&gt; | 是 | 回调函数。注册 rule 发生改变时的调用。<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |


## on('netMeteredIfacesChange')

```TypeScript
function on(type: 'netMeteredIfacesChange', callback: Callback<Array<string>>): void
```

注册计量 iface 发生改变时的回调，使用 callback 异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'netMeteredIfacesChange' | 是 | 订阅的事件类型。'netMeteredIfacesChange'：注册计量iface发生改变事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;string&gt;&gt; | 是 | 回调函数。注册计量 iface 发生改变时调用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |


## on('netQuotaPolicyChange')

```TypeScript
function on(type: 'netQuotaPolicyChange', callback: Callback<Array<NetQuotaPolicy>>): void
```

注册计量网络策略发生改变时的回调，使用 callback 异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'netQuotaPolicyChange' | 是 | 订阅的事件类型。'netQuotaPolicyChange'：注册计量网络策略发生改变事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[NetQuotaPolicy](arkts-network-policy-netquotapolicy-i-sys.md)&gt;&gt; | 是 | 回调函数。注册计量网络策略发生改变时调用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |


## on('netBackgroundPolicyChange')

```TypeScript
function on(type: 'netBackgroundPolicyChange', callback: Callback<boolean>): void
```

注册后台网络策略发生改变时的回调，使用 callback 异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'netBackgroundPolicyChange' | 是 | 订阅的事件类型。'netBackgroundPolicyChange'：注册后台网络策略发生改变事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | 是 | 回调函数。注册后台网络策略发生改变时调用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
