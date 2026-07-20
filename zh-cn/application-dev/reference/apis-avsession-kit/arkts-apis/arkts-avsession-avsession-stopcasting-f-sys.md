# stopCasting（系统接口）

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

<a id="stopcasting"></a>
## stopCasting

```TypeScript
function stopCasting(session: SessionToken, callback: AsyncCallback<void>): void
```

结束投播。结果通过callback异步回调方式返回。

**起始版本：** 10

<!--Device-avSession-function stopCasting(session: SessionToken, callback: AsyncCallback<void>): void--><!--Device-avSession-function stopCasting(session: SessionToken, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| session | [SessionToken](arkts-avsession-avsession-sessiontoken-i-sys.md) | 是 | 会话令牌。SessionToken表示单个token。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当成功结束投播，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [6600109](../errorcode-avsession.md#6600109-远端会话不存在) | The remote connection is not established |

**示例：**

```TypeScript

let myToken: avSession.SessionToken = {
  sessionId: sessionId,
}
avSession.stopCasting(myToken, () => {
    console.info('Succeeded in stopping casting.');
});

```


<a id="stopcasting-1"></a>
## stopCasting

```TypeScript
function stopCasting(session: SessionToken): Promise<void>
```

结束投播。结果通过Promise异步回调方式返回。

**起始版本：** 10

<!--Device-avSession-function stopCasting(session: SessionToken): Promise<void>--><!--Device-avSession-function stopCasting(session: SessionToken): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| session | [SessionToken](arkts-avsession-avsession-sessiontoken-i-sys.md) | 是 | 会话令牌。SessionToken表示单个token。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。当成功结束投播，无返回结果，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [6600109](../errorcode-avsession.md#6600109-远端会话不存在) | The remote connection is not established |

**示例：**

```TypeScript

let myToken: avSession.SessionToken = {
  sessionId: sessionId,
}
avSession.stopCasting(myToken).then(() => {
  console.info('Succeeded in stopping casting.');
});

```

