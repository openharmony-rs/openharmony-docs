# offGetSimActiveState

## offGetSimActiveState

```TypeScript
function offGetSimActiveState(callback?: Callback<boolean>): void
```

取消SIM卡激活状态变化的监听，使用callback方式作为异步方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_TELEPHONY_STATE

<!--Device-observer-function offGetSimActiveState(callback?: Callback<boolean>): void--><!--Device-observer-function offGetSimActiveState(callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Telephony.StateRegistry

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 否 | 回调函数，返回SIM卡是否激活。&lt;br/&gt;- true：激活。&lt;br/&gt;- false：未激活。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

let simActiveState: Callback<boolean> = (isSimActive: boolean) => {
    console.info(`simActiveState slotId ${JSON.stringify(isSimActive)}`);
}
observer.offGetSimActiveState(simActiveState);
```

