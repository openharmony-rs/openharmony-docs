# onDistributedSessionChange（系统接口）

## onDistributedSessionChange

```TypeScript
function onDistributedSessionChange(distributedSessionType: DistributedSessionType, callback: Callback<Array<AVSessionController>>): void
```

Register distributed session changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-avSession-function onDistributedSessionChange(distributedSessionType: DistributedSessionType, callback: Callback<Array<AVSessionController>>): void--><!--Device-avSession-function onDistributedSessionChange(distributedSessionType: DistributedSessionType, callback: Callback<Array<AVSessionController>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| distributedSessionType | [DistributedSessionType](arkts-avsession-avsession-distributedsessiontype-e-sys.md) | 是 | Indicates the distributed session type |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Array&lt;[AVSessionController](arkts-avsession-avsession-avsessioncontroller-i.md)&gt;&gt; | 是 | The callback will return remote changed AVSessionController. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

## 示例

```TypeScript
avSession.onDistributedSessionChange(avSession.DistributedSessionType.TYPE_SESSION_REMOTE, (sessionControllers: Array<avSession.AVSessionController>) => {
  console.info(`onDistributedSessionChange size: ${sessionControllers.length}`);
});
```

