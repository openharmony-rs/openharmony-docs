# sendCommand

## 导入模块

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## sendCommand

```TypeScript
function sendCommand(command: LocationCommand, callback: AsyncCallback<boolean>): void
```

给位置服务子系统的各个部件发送扩展命令。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [sendCommand](arkts-location-geolocationmanager-sendcommand-f.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | LocationCommand | 是 | 指定目标场景，和将要发送的命令（字符串）。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示命令发送成功；返回false表示命令发送失败。 |

**示例**

```TypeScript
import geolocation from '@ohos.geolocation';
let requestInfo:geolocation.LocationCommand = {'scenario': 0x301, 'command': "command_1"};
geolocation.sendCommand(requestInfo, (err, result) => {
    if (err) {
        console.info('sendCommand: err=' + JSON.stringify(err));
    }
    if (result) {
        console.info('sendCommand: result=' + JSON.stringify(result));
    }
});
```


## sendCommand

```TypeScript
function sendCommand(command: LocationCommand): Promise<boolean>
```

给位置服务子系统的各个部件发送扩展命令。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [sendCommand](arkts-location-geolocationmanager-sendcommand-f.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | LocationCommand | 是 | 指定目标场景，和将要发送的命令（字符串）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | Promise对象，返回true表示命令发送成功；返回false表示命令发送失败。 |

**示例**

```TypeScript
import geolocation from '@ohos.geolocation';
let requestInfo:geolocation.LocationCommand = {'scenario': 0x301, 'command': "command_1"};
geolocation.sendCommand(requestInfo).then((result) => {
    console.info('promise, sendCommand: ' + JSON.stringify(result));
});
```
