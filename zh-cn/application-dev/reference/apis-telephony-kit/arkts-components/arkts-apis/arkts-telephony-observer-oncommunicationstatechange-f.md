# onCommunicationStateChange

## 导入模块

```TypeScript
import { observer } from '@kit.TelephonyKit';
```

## onCommunicationStateChange

```TypeScript
function onCommunicationStateChange(callback: Callback<boolean>, options?: ObserverOptions): void
```

订阅5A网络状态变化事件，使用callback异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.GET_NETWORK_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Telephony.StateRegistry

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示5A状态为使能态；返回false表示5A状态为非使能态。 |
| options | [ObserverOptions](arkts-telephony-observer-observeroptions-i.md) | 否 | 电话相关事件订阅参数可选项，指定事件订阅的卡槽ID，默认为当前默认数据卡槽ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
// 设置订阅参数，指定卡槽ID
let options: observer.ObserverOptions = {
    slotId: 0
}
// 定义5A网络状态变化回调
let callback: Callback<boolean> = (isCommunicationStateOn: boolean) => {
    console.info(`communicationStateChanged ${JSON.stringify(isCommunicationStateOn)}`);
}
try {
    // 订阅5A网络状态变化事件
    observer.onCommunicationStateChange(callback, options);
} catch (err) {
    console.error(`observer.onCommunicationStateChange failed: ${JSON.stringify(err)}`);
}
```
