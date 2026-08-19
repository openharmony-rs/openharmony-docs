# off_sessionCreate（系统接口）

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

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
| callback | (session: AVSessionDescriptor) =&gt; void | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。 <br>该参数为会话相关描述，为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

**示例**

```TypeScript
avSession.off('sessionCreate');
```

