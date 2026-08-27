# on（系统接口）

## 导入模块

```TypeScript
import { ethernet } from '@kit.NetworkKit';
```

## on('interfaceStateChange')

```TypeScript
function on(type: 'interfaceStateChange', callback: Callback<InterfaceStateInfo>): void
```

注册网卡热插拔事件，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'interfaceStateChange' | 是 | 订阅的事件类型，'interfaceStateChange'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[InterfaceStateInfo](arkts-network-ethernet-interfacestateinfo-i-sys.md)&gt; | 是 | 回调函数。返回以太网卡状态信息。<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { ethernet } from '@kit.NetworkKit';

ethernet.on('interfaceStateChange', (data: object) => {
  console.info('on interfaceSharingStateChange：' + JSON.stringify(data));
});
```
