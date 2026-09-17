# on

## 导入模块

```TypeScript
import { omapi } from '@kit.ConnectivityKit';
```

## on('stateChanged')

```TypeScript
function on(type: 'stateChanged', callback: Callback<ServiceState>): void
```

注册监听服务状态变化事件。

调用[omapi.newSEService](arkts-connectivity-omapi-newseservice-f.md#newseserviceservicestate)或[omapi.createService](arkts-connectivity-omapi-createservice-f.md)创建服务成功后再用on接口注册回调。

**起始版本：** 18

**系统能力：** SystemCapability.Communication.SecureElement

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'stateChanged' | 是 | 订阅监听的事件类型，固定填'stateChanged' 。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ServiceState](arkts-connectivity-omapi-servicestate-e.md)&gt; | 是 | 返回SE服务状态的回调 。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
