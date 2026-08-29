# sendCommand

## 导入模块

```TypeScript
```

## sendCommand

```TypeScript
function sendCommand(command: LocationCommand, callback: AsyncCallback<void>): void
```

给位置服务子系统的各个部件发送扩展命令。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | LocationCommand | 是 | 指定目标场景，和将要发送的命令（字符串）。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当命令发送成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.sendCommand} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

let requestInfo: geoLocationManager.LocationCommand = { 'scenario': 0x301, 'command': "command_1" };
try {
  geoLocationManager.sendCommand(requestInfo, (err) => {
    if (err) {
      console.error('sendCommand: err=' + JSON.stringify(err));
    }
  });
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```


## sendCommand

```TypeScript
function sendCommand(command: LocationCommand): Promise<void>
```

给位置服务子系统的各个部件发送扩展命令。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | LocationCommand | 是 | 指定目标场景，和将要发送的命令（字符串）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象。无返回结果的Promise对象 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.sendCommand} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let requestInfo: geoLocationManager.LocationCommand = { 'scenario': 0x301, 'command': "command_1" };
try {
  geoLocationManager.sendCommand(requestInfo).then(() => {
    console.info('promise, sendCommand success');
  })
    .catch((error: BusinessError) => {
      console.error('promise, sendCommand: error=' + JSON.stringify(error));
    });
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
