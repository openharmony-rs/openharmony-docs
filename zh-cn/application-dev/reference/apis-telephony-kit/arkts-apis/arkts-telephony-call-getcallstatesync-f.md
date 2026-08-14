# getCallStateSync

## getCallStateSync

```TypeScript
function getCallStateSync(): CallState
```

获取当前通话状态。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-call-function getCallStateSync(): CallState--><!--Device-call-function getCallStateSync(): CallState-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| CallState | 返回获取到的通话状态。 |

## 示例

```TypeScript
let callState: call.CallState = call.getCallStateSync();
console.info(`the call state is:` + callState);
```

