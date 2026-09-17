# off

## 导入模块

```TypeScript
import { omapi } from '@kit.ConnectivityKit';
```

## off('stateChanged')

```TypeScript
function off(type: 'stateChanged', callback?: Callback<ServiceState>): void
```

取消订阅服务状态更改事件。

**起始版本：** 18

**系统能力：** SystemCapability.Communication.SecureElement

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'stateChanged' | 是 | 取消订阅监听的事件类型，固定填'stateChanged' 。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ServiceState](arkts-connectivity-omapi-servicestate-e.md)&gt; | 否 | 返回SE服务状态的回调。不填则取消订阅该type对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
