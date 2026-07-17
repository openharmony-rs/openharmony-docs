# stopDeviceLogging（系统接口）

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## stopDeviceLogging

```TypeScript
function stopDeviceLogging(): Promise<void>
```

停止当前设备日志写入。结果通过Promise异步回调方式返回。

**起始版本：** 13

<!--Device-avSession-function stopDeviceLogging(): Promise<void>--><!--Device-avSession-function stopDeviceLogging(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。当停止当前设备日志写入，无返回结果，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |

**示例：**

```TypeScript
avSession.stopDeviceLogging().then(() => {
  console.info('Succeeded in stopping casting.');
});

```

