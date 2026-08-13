# onCooperateMessage（系统接口）

## onCooperateMessage

```TypeScript
function onCooperateMessage(callback: Callback<CooperateMessage>): void
```

Enables listening for screen hopping status change events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.COOPERATE_MANAGER

<!--Device-cooperate-function onCooperateMessage(callback: Callback<CooperateMessage>): void--><!--Device-cooperate-function onCooperateMessage(callback: Callback<CooperateMessage>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[CooperateMessage](arkts-distributedservice-cooperate-cooperatemessage-i-sys.md)&gt; | 是 | Asynchronous callback used to &lt;br&gt; return the screen hopping status change event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

```TypeScript
function callback(msg: cooperate.CooperateMessage): void {
  console.info(`Keyboard mouse crossing event: ${JSON.stringify(msg)}`);
}

try {
  cooperate.onCooperateMessage(callback);
} catch (error) {
  console.error(`Register failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}
```

