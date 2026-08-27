# off（系统接口）

## 导入模块

```TypeScript
```

## off('sharingStateChange')

```TypeScript
function off(type: 'sharingStateChange', callback?: Callback<boolean>): void
```

注销网络共享状态变化事件，使用 callback 异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.CONNECTIVITY_INTERNAL

**系统能力：** SystemCapability.Communication.NetManager.NetSharing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sharingStateChange' | 是 | 注销的事件类型。'sharingStateChange'：注销网络共享状态变化事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | 否 | 回调函数，返回网络共享状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { sharing } from '@kit.NetworkKit';

sharing.off('sharingStateChange', (data: boolean) => {
  console.info(JSON.stringify(data));
});
```


## off('interfaceSharingStateChange')

```TypeScript
function off(type: 'interfaceSharingStateChange', callback?: Callback<InterfaceSharingStateInfo>): void
```

注销网卡网络共享状态变化事件，使用 callback 异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.CONNECTIVITY_INTERNAL

**系统能力：** SystemCapability.Communication.NetManager.NetSharing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'interfaceSharingStateChange' | 是 | 注销的事件类型。'interfaceSharingStateChange'：注销网卡网络共享状态变化事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[InterfaceSharingStateInfo](arkts-network-sharing-interfacesharingstateinfo-i-sys.md)&gt; | 否 | 回调函数，注销指定网卡共享状态变化通知。<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { sharing } from '@kit.NetworkKit';

sharing.off('interfaceSharingStateChange', (data: object) => {
  console.info(JSON.stringify(data));
});
```


## off('sharingUpstreamChange')

```TypeScript
function off(type: 'sharingUpstreamChange', callback?: Callback<NetHandle>): void
```

注销上行网络变化事件，使用 callback 异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.CONNECTIVITY_INTERNAL

**系统能力：** SystemCapability.Communication.NetManager.NetSharing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sharingUpstreamChange' | 是 | 注销的事件类型。'sharingUpstreamChange'：注销上行网络变化事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;NetHandle&gt; | 否 | 回调函数，注销上行网络变化事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { sharing } from '@kit.NetworkKit';

sharing.off('sharingUpstreamChange', (data: object) => {
  console.info(JSON.stringify(data));
});
```
