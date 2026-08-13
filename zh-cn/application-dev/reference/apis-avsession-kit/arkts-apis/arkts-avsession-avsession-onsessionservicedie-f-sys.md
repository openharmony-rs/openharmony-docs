# onSessionServiceDie（系统接口）

## onSessionServiceDie

```TypeScript
function onSessionServiceDie(callback: NoParamCallback): void
```

Register Session service death callback, notifying the application to clean up resources.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-avSession-function onSessionServiceDie(callback: NoParamCallback): void--><!--Device-avSession-function onSessionServiceDie(callback: NoParamCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [NoParamCallback](arkts-avsession-avsession-noparamcallback-t.md) | 是 | Used to handle ('sessionServiceDie') command. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

## 示例

```TypeScript
avSession.onSessionServiceDie(() => {
  console.info('onSessionServiceDie  : session is  Died ');
});
```

