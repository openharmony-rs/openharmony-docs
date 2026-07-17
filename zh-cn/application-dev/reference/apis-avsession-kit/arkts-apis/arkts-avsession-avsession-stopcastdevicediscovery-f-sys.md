# stopCastDeviceDiscovery（系统接口）

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## stopCastDeviceDiscovery

```TypeScript
function stopCastDeviceDiscovery(callback: AsyncCallback<void>): void
```

结束设备搜索发现。结果通过callback异步回调方式返回。

**起始版本：** 10

<!--Device-avSession-function stopCastDeviceDiscovery(callback: AsyncCallback<void>): void--><!--Device-avSession-function stopCastDeviceDiscovery(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当成功停止搜索，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

**示例：**

```TypeScript

avSession.stopCastDeviceDiscovery(() => {
    console.info('Succeeded in stopping cast device discovery.');
});

```


## stopCastDeviceDiscovery

```TypeScript
function stopCastDeviceDiscovery(): Promise<void>
```

结束设备搜索发现。结果通过Promise异步回调方式返回。

**起始版本：** 10

<!--Device-avSession-function stopCastDeviceDiscovery(): Promise<void>--><!--Device-avSession-function stopCastDeviceDiscovery(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。当成功停止搜索，无返回结果，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

**示例：**

```TypeScript

avSession.stopCastDeviceDiscovery().then(() => {
  console.info('Succeeded in stopping cast device discovery.');
});

```

