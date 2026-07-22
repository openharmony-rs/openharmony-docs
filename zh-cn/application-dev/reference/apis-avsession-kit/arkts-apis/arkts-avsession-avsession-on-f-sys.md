# on（系统接口）

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## on('sessionCreate')

```TypeScript
function on(type: 'sessionCreate', callback: (session: AVSessionDescriptor) => void): void
```

会话的创建事件监听。 使用callback异步回调。

**起始版本：** 9

<!--Device-avSession-function on(type: 'sessionCreate', callback: (session: AVSessionDescriptor) => void): void--><!--Device-avSession-function on(type: 'sessionCreate', callback: (session: AVSessionDescriptor) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sessionCreate' | 是 | 事件回调类型，支持的事件是'sessionCreate'：会话创建事件，检测到会话创建时触发。 |
| callback | (session: AVSessionDescriptor) =&gt; void | 是 | 回调函数。参数为会话相关描述。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

**示例：**

```TypeScript
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
        Text(this.message)
          .onClick(()=>{
            avSession.on('sessionCreate', (descriptor: avSession.AVSessionDescriptor) => {
              console.info(`on sessionCreate : isActive : ${descriptor.isActive}`);
              console.info(`on sessionCreate : type : ${descriptor.type}`);
              console.info(`on sessionCreate : sessionTag : ${descriptor.sessionTag}`);
            });
          })
      }
    .width('100%')
    .height('100%')
  }
}


```


## on('sessionDestroy')

```TypeScript
function on(type: 'sessionDestroy', callback: (session: AVSessionDescriptor) => void): void
```

会话的销毁事件监听。使用callback异步回调。

**起始版本：** 9

<!--Device-avSession-function on(type: 'sessionDestroy', callback: (session: AVSessionDescriptor) => void): void--><!--Device-avSession-function on(type: 'sessionDestroy', callback: (session: AVSessionDescriptor) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sessionDestroy' | 是 | 事件回调类型，支持的事件是`'sessionDestroy'`：会话销毁事件，检测到会话销毁时触发。 |
| callback | (session: AVSessionDescriptor) =&gt; void | 是 | 回调函数。参数为会话相关描述。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

**示例：**

```TypeScript
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
        Text(this.message)
          .onClick(()=>{
            avSession.on('sessionDestroy', (descriptor: avSession.AVSessionDescriptor) => {
              console.info(`on sessionDestroy : ${descriptor.sessionId}`);
            });
          })
      }
    .width('100%')
    .height('100%')
  }
}

```


## on('topSessionChange')

```TypeScript
function on(type: 'topSessionChange', callback: (session: AVSessionDescriptor) => void): void
```

最新播放会话变更的事件监听。使用callback异步回调。

**起始版本：** 9

<!--Device-avSession-function on(type: 'topSessionChange', callback: (session: AVSessionDescriptor) => void): void--><!--Device-avSession-function on(type: 'topSessionChange', callback: (session: AVSessionDescriptor) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'topSessionChange' | 是 | 事件回调类型，支持的事件是 `'topSessionChange'`：最新播放会话的变化事件，检测到最新的会话改变时触发。 |
| callback | (session: AVSessionDescriptor) =&gt; void | 是 | 回调函数。参数为会话相关描述。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

**示例：**

```TypeScript
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
        Text(this.message)
          .onClick(()=>{
            avSession.on('topSessionChange', (descriptor: avSession.AVSessionDescriptor) => {
              console.info(`on topSessionChange : isActive : ${descriptor.isActive}`);
              console.info(`on topSessionChange : type : ${descriptor.type}`);
              console.info(`on topSessionChange : sessionTag : ${descriptor.sessionTag}`);
            });
          })
      }
    .width('100%')
    .height('100%')
  }
}

```


## on('sessionServiceDie')

```TypeScript
function on(type: 'sessionServiceDie', callback: () => void): void
```

监听会话的服务死亡事件。通知应用清理资源。

**起始版本：** 9

<!--Device-avSession-function on(type: 'sessionServiceDie', callback: () => void): void--><!--Device-avSession-function on(type: 'sessionServiceDie', callback: () => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sessionServiceDie' | 是 | 事件回调类型，支持事件`'sessionServiceDie'`：会话服务死亡事件，检测到会话的服务死亡时触发。 |
| callback | () =&gt; void | 是 | 回调函数。当监听事件注册成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

**示例：**

```TypeScript
avSession.on('sessionServiceDie', () => {
  console.info('on sessionServiceDie : session is dead ');
});

```


## on('distributedSessionChange')

```TypeScript
function on(type: 'distributedSessionChange', distributedSessionType: DistributedSessionType, callback: Callback<Array<AVSessionController>>): void
```

最新分布式远端会话变更的监听事件。

**起始版本：** 18

<!--Device-avSession-function on(type: 'distributedSessionChange', distributedSessionType: DistributedSessionType, callback: Callback<Array<AVSessionController>>): void--><!--Device-avSession-function on(type: 'distributedSessionChange', distributedSessionType: DistributedSessionType, callback: Callback<Array<AVSessionController>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'distributedSessionChange' | 是 | 事件回调类型，支持的事件为 `'distributedSessionChange'`：最新远端分布式会话的变化事件，检测到最新的会话改变时触发。 |
| distributedSessionType | [DistributedSessionType](arkts-avsession-avsession-distributedsessiontype-e-sys.md) | 是 | 远端会话类型。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;Array&lt;AVSessionController&gt;&gt; | 是 | 回调函数。参数为对应类型的会话控制器实例列表，可查看会话ID，并完成对会话发送命令及事件，获取元数据、播放状态信息等操作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

**示例：**

```TypeScript
avSession.on('distributedSessionChange', avSession.DistributedSessionType.TYPE_SESSION_REMOTE, (sessionControllers: Array<avSession.AVSessionController>) => {
  console.info(`on distributedSessionChange size: ${sessionControllers.length}`);
});

```


## on('deviceAvailable')

```TypeScript
function on(type: 'deviceAvailable', callback: (device: OutputDeviceInfo) => void): void
```

设备发现回调监听。

**起始版本：** 10

<!--Device-avSession-function on(type: 'deviceAvailable', callback: (device: OutputDeviceInfo) => void): void--><!--Device-avSession-function on(type: 'deviceAvailable', callback: (device: OutputDeviceInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceAvailable' | 是 | 事件回调类型，支持事件`'deviceAvailable'`，有设备被发现时触发回调。 |
| callback | (device: OutputDeviceInfo) =&gt; void | 是 | 回调函数。当监听事件注册成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |

**示例：**

```TypeScript
let castDevice: avSession.OutputDeviceInfo;
avSession.on('deviceAvailable', (device: avSession.OutputDeviceInfo) => {
  castDevice = device;
  console.info(`on deviceAvailable  : ${device} `);
});

```


## on('deviceOffline')

```TypeScript
function on(type: 'deviceOffline', callback: (deviceId: string) => void): void
```

设备下线回调监听。

**起始版本：** 11

<!--Device-avSession-function on(type: 'deviceOffline', callback: (deviceId: string) => void): void--><!--Device-avSession-function on(type: 'deviceOffline', callback: (deviceId: string) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceOffline' | 是 | 事件回调类型，支持事件`'deviceOffline'`，有设备下线时触发回调。 |
| callback | (deviceId: string) =&gt; void | 是 | 回调函数，参数deviceId是设备的ID。当监听事件注册成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |

**示例：**

```TypeScript
let castDeviceId: string;
avSession.on('deviceOffline', (deviceId: string) => {
  castDeviceId = deviceId;
  console.info(`on deviceOffline  : ${deviceId} `);
});

```


## on('deviceLogEvent')

```TypeScript
function on(type: 'deviceLogEvent', callback: Callback<DeviceLogEventCode>): void
```

监听日志事件的回调。

**起始版本：** 13

<!--Device-avSession-function on(type: 'deviceLogEvent', callback: Callback<DeviceLogEventCode>): void--><!--Device-avSession-function on(type: 'deviceLogEvent', callback: Callback<DeviceLogEventCode>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceLogEvent' | 是 | 事件回调类型，支持事件`'deviceLogEvent'`。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;DeviceLogEventCode&gt; | 是 | 回调函数，参数DeviceLogEventCode是当前设备日志返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |

**示例：**

```TypeScript
avSession.on('deviceLogEvent', (eventCode: avSession.DeviceLogEventCode) => {
  console.info(`on deviceLogEvent code : ${eventCode}`);
});

```


## on('deviceStateChanged')

```TypeScript
function on(type: 'deviceStateChanged', callback: Callback<DeviceState>): void
```

投播设备连接状态的回调函数。

**起始版本：** 20

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function on(type: 'deviceStateChanged', callback: Callback<DeviceState>): void--><!--Device-avSession-function on(type: 'deviceStateChanged', callback: Callback<DeviceState>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceStateChanged' | 是 | 事件回调类型，支持事件`'deviceStateChanged'`，投播设备连接状态发生变化时触发回调。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;DeviceState&gt; | 是 | 回调函数，参数DeviceState包含投播设备ID、连接状态码、连接错误码和系统雷达错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

**示例：**

```TypeScript
avSession.on('deviceStateChanged', (state: avSession.DeviceState) => {
  console.info(`on deviceStateChanged state, deviceId=${state.deviceId}, connect status=${state.deviceState},
    reasonCode=${state.reasonCode}, radarErrorCode=${state.radarErrorCode}`)
})

```

