# offVoIPStateChange

## 导入模块

```TypeScript
import { observer } from '@kit.TelephonyKit';
```

## offVoIPStateChange

```TypeScript
function offVoIPStateChange(callback?: Callback<VoIPCallStateInfo>): void
```

VoIP通话状态更新时取消回调。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.MANAGE_CALL_FOR_DEVICES

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-observer-function offVoIPStateChange(callback?: Callback<VoIPCallStateInfo>): void--><!--Device-observer-function offVoIPStateChange(callback?: Callback<VoIPCallStateInfo>): void-End-->

**系统能力：** SystemCapability.Telephony.StateRegistry

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VoIPCallStateInfo](arkts-telephony-observer-voipcallstateinfo-i.md)&gt; | 否 | 的回调获取VoIP呼叫状态信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [8800002](../errorcode-telephony.md#8800002-服务连接失败) | Service connection failed. |
| [8800003](../errorcode-telephony.md#8800003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { observer } from '@kit.TelephonyKit';

let callback: (data: observer.VoIPCallStateInfo) => void = (data: observer.VoIPCallStateInfo) => {
  console.info(`onVoIPStateChange, appName: ${data.appName}, contactName: ${data.contactName}, ` +
    `callType: ${data.callType}, callState: ${data.callState} ` +
    `isVoiceAnswerSupported: ${data.isVoiceAnswerSupported}`);
}

// 取消订阅：指定回调取消单条订阅
try {
  observer.offVoIPStateChange(callback);
} catch (err) {
  console.error(`observer.offVoIPStateChange failed: ${JSON.stringify(err)}`);
}

// 取消订阅：不带参数取消全部订阅
try {
  observer.offVoIPStateChange();
} catch (err) {
  console.error(`observer.offVoIPStateChange failed: ${JSON.stringify(err)}`);
}
```
