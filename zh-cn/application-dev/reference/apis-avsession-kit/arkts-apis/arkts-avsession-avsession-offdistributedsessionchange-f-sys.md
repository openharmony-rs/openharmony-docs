# offDistributedSessionChange（系统接口）

## offDistributedSessionChange

```TypeScript
function offDistributedSessionChange(distributedSessionType: DistributedSessionType, callback?: Callback<Array<AVSessionController>>): void
```

Unregister distributed session changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-avSession-function offDistributedSessionChange(distributedSessionType: DistributedSessionType, callback?: Callback<Array<AVSessionController>>): void--><!--Device-avSession-function offDistributedSessionChange(distributedSessionType: DistributedSessionType, callback?: Callback<Array<AVSessionController>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| distributedSessionType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Indicates the distributed session type |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;AVSessionController&gt;&gt; | 否 | The callback will return remote changed AVSessionController. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

**示例：**

```TypeScript
avSession.offDistributedSessionChange(avSession.DistributedSessionType.TYPE_SESSION_REMOTE);
```

