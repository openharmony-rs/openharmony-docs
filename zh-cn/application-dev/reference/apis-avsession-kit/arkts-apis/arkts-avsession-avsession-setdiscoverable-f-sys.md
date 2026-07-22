# setDiscoverable（系统接口）

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## setDiscoverable

```TypeScript
function setDiscoverable(enable: boolean, callback: AsyncCallback<void>): void
```

设置设备是否可被发现，用于投播接收端。结果通过callback异步回调方式返回。

**起始版本：** 10

<!--Device-avSession-function setDiscoverable(enable: boolean, callback: AsyncCallback<void>): void--><!--Device-avSession-function setDiscoverable(enable: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否允许本设备被发现。true表示允许被发现，false表示不允许被发现。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当设置成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |

**示例：**

```TypeScript

avSession.setDiscoverable(true, () => {
    console.info('Succeeded in setting discoverable.');
});

```


## setDiscoverable

```TypeScript
function setDiscoverable(enable: boolean): Promise<void>
```

设置设备是否可被发现，用于投播接收端。结果通过Promise异步回调方式返回。

**起始版本：** 10

<!--Device-avSession-function setDiscoverable(enable: boolean): Promise<void>--><!--Device-avSession-function setDiscoverable(enable: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否允许本设备被发现。true表示允许被发现，false表示不允许被发现。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |

**示例：**

```TypeScript

avSession.setDiscoverable(true).then(() => {
  console.info('Succeeded in setting discoverable.');
});

```

