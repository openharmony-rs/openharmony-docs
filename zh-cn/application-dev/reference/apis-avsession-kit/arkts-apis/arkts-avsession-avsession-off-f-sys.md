# off（系统接口）

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

<a id="off"></a>
## off('sessionCreate')

```TypeScript
function off(type: 'sessionCreate', callback?: (session: AVSessionDescriptor) => void): void
```

注销会话创建事件监听。注销后，不再接收该事件。

**起始版本：** 9

<!--Device-avSession-function off(type: 'sessionCreate', callback?: (session: AVSessionDescriptor) => void): void--><!--Device-avSession-function off(type: 'sessionCreate', callback?: (session: AVSessionDescriptor) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sessionCreate' | 是 | 事件回调类型，支持的事件为：`'sessionCreate'`。 |
| callback | (session: AVSessionDescriptor) =&gt; void | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。<br>该参数为会话相关描述，为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

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
            });
            avSession.off('sessionCreate');
          })
      }
    .width('100%')
    .height('100%')
  }
}

```


<a id="off-1"></a>
## off('sessionDestroy')

```TypeScript
function off(type: 'sessionDestroy', callback?: (session: AVSessionDescriptor) => void): void
```

注销会话销毁事件监听。注销后，不再监听该事件。

**起始版本：** 9

<!--Device-avSession-function off(type: 'sessionDestroy', callback?: (session: AVSessionDescriptor) => void): void--><!--Device-avSession-function off(type: 'sessionDestroy', callback?: (session: AVSessionDescriptor) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sessionDestroy' | 是 | 事件回调类型，支持的事件为`'sessionDestroy'`。 |
| callback | (session: AVSessionDescriptor) =&gt; void | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。<br>该参数为会话相关描述，为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

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
            });
            avSession.off('sessionDestroy');
          })
      }
    .width('100%')
    .height('100%')
  }
}

```


<a id="off-2"></a>
## off('topSessionChange')

```TypeScript
function off(type: 'topSessionChange', callback?: (session: AVSessionDescriptor) => void): void
```

注销最新播放会话变更事件监听。注销后，不再进行该事件的监听。

**起始版本：** 9

<!--Device-avSession-function off(type: 'topSessionChange', callback?: (session: AVSessionDescriptor) => void): void--><!--Device-avSession-function off(type: 'topSessionChange', callback?: (session: AVSessionDescriptor) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'topSessionChange' | 是 | 事件回调类型，支持的事件为`'topSessionChange'`。 |
| callback | (session: AVSessionDescriptor) =&gt; void | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。<br>该参数为会话相关描述，为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

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
            });
            avSession.off('topSessionChange');
          })
      }
    .width('100%')
    .height('100%')
  }
}

```


<a id="off-3"></a>
## off('sessionServiceDie')

```TypeScript
function off(type: 'sessionServiceDie', callback?: () => void): void
```

取消会话服务死亡监听，取消后，不再进行服务死亡监听。

**起始版本：** 9

<!--Device-avSession-function off(type: 'sessionServiceDie', callback?: () => void): void--><!--Device-avSession-function off(type: 'sessionServiceDie', callback?: () => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sessionServiceDie' | 是 | 事件回调类型，支持事件`'sessionServiceDie'`：会话服务死亡事件。 |
| callback | () =&gt; void | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的服务死亡监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

**示例：**

```TypeScript
avSession.off('sessionServiceDie');

```


<a id="off-4"></a>
## off('distributedSessionChange')

```TypeScript
function off(type: 'distributedSessionChange', distributedSessionType: DistributedSessionType, callback?: Callback<Array<AVSessionController>>): void
```

取消最新分布式远端会话变更的监听事件，取消后，不再进行该事件的监听。

**起始版本：** 18

<!--Device-avSession-function off(type: 'distributedSessionChange', distributedSessionType: DistributedSessionType, callback?: Callback<Array<AVSessionController>>): void--><!--Device-avSession-function off(type: 'distributedSessionChange', distributedSessionType: DistributedSessionType, callback?: Callback<Array<AVSessionController>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'distributedSessionChange' | 是 | 事件回调类型，支持的事件为`'distributedSessionChange'`。 |
| distributedSessionType | [DistributedSessionType](arkts-avsession-avsession-distributedsessiontype-e-sys.md) | 是 | 远端会话类型。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;Array&lt;AVSessionController&gt;&gt; | 否 | 回调函数。参数为对应类型的会话控制器实例列表，可查看会话ID，并完成对会话发送命令及事件，获取元数据、播放状态信息等操作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

**示例：**

```TypeScript
avSession.off('distributedSessionChange', avSession.DistributedSessionType.TYPE_SESSION_REMOTE);

```


<a id="off-5"></a>
## off('deviceAvailable')

```TypeScript
function off(type: 'deviceAvailable', callback?: (device: OutputDeviceInfo) => void): void
```

取消设备发现回调的监听。

**起始版本：** 10

<!--Device-avSession-function off(type: 'deviceAvailable', callback?: (device: OutputDeviceInfo) => void): void--><!--Device-avSession-function off(type: 'deviceAvailable', callback?: (device: OutputDeviceInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceAvailable' | 是 | 事件回调类型，支持事件`'deviceAvailable'`：设备发现回调。 |
| callback | (device: OutputDeviceInfo) =&gt; void | 否 | 用于返回设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |

**示例：**

```TypeScript
avSession.off('deviceAvailable');

```


<a id="off-6"></a>
## off('deviceOffline')

```TypeScript
function off(type: 'deviceOffline', callback?: (deviceId: string) => void): void
```

取消设备下线回调的监听。

**起始版本：** 11

<!--Device-avSession-function off(type: 'deviceOffline', callback?: (deviceId: string) => void): void--><!--Device-avSession-function off(type: 'deviceOffline', callback?: (deviceId: string) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceOffline' | 是 | 事件回调类型，支持事件`'deviceOffline'`：设备下线回调。 |
| callback | (deviceId: string) =&gt; void | 否 | 回调函数，参数deviceId是设备的ID。当监听事件取消成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |

**示例：**

```TypeScript
avSession.off('deviceOffline');

```


<a id="off-7"></a>
## off('deviceLogEvent')

```TypeScript
function off(type: 'deviceLogEvent', callback?: Callback<DeviceLogEventCode>): void
```

取消监听日志事件的回调。

**起始版本：** 13

<!--Device-avSession-function off(type: 'deviceLogEvent', callback?: Callback<DeviceLogEventCode>): void--><!--Device-avSession-function off(type: 'deviceLogEvent', callback?: Callback<DeviceLogEventCode>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceLogEvent' | 是 | 取消对应的监听事件，支持事件`'deviceLogEvent'`。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;DeviceLogEventCode&gt; | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |

**示例：**

```TypeScript
avSession.off('deviceLogEvent');

```


<a id="off-8"></a>
## off('deviceStateChanged')

```TypeScript
function off(type: 'deviceStateChanged', callback?: Callback<DeviceState>): void
```

取消投播设备连接状态的监听。

**起始版本：** 20

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function off(type: 'deviceStateChanged', callback?: Callback<DeviceState>): void--><!--Device-avSession-function off(type: 'deviceStateChanged', callback?: Callback<DeviceState>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deviceStateChanged' | 是 | 取消对应的监听事件，支持事件`'deviceStateChanged'`，投播设备连接状态变化的回调。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;DeviceState&gt; | 否 | 回调函数，当监听事件取消成功时，err为undefined；否则返回错误对象。该参数为可选参数，若未填写，则取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

**示例：**

```TypeScript
avSession.off('deviceStateChanged');

```

