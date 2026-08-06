# createController（系统接口）

## createController

```TypeScript
function createController(sessionId: string, callback: AsyncCallback<AVSessionController>): void
```

根据会话ID创建会话控制器。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function createController(sessionId: string, callback: AsyncCallback<AVSessionController>): void--><!--Device-avSession-function createController(sessionId: string, callback: AsyncCallback<AVSessionController>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | string | 是 | 会话ID。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;AVSessionController&gt; | 是 | 回调函数。返回会话控制器实例，可查看会话ID，\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_并完成对会话发送命令及事件，获取元数据、播放状态信息等操作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |

**示例：**

```TypeScript
let currentAVcontroller: avSession.AVSessionController | undefined = undefined;
avSession.createController(sessionId, (err, avcontroller: avSession.AVSessionController) => {
  currentAVcontroller = avcontroller;
    console.info('Succeeded in creating controller.');
});
```

