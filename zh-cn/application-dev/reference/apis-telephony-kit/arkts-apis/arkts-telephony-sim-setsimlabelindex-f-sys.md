# setSimLabelIndex（系统接口）

## setSimLabelIndex

```TypeScript
function setSimLabelIndex(simId: int, simLabelIndex: int): Promise<void>
```

设置SIM卡标签索引。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

<!--Device-sim-function setSimLabelIndex(simId: int, simLabelIndex: int): Promise<void>--><!--Device-sim-function setSimLabelIndex(simId: int, simLabelIndex: int): Promise<void>-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| simId | int | 是 | 表示来自SIM账户信息的卡的SIM ID。 &lt;br&gt;取值范围:[1,500] |
| simLabelIndex | int | 是 | 表示卡的SIM标签索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the setSimLabelIndex. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Nonsystem applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.setSimLabelIndex(1,  0).then(() => {
    console.info(`setSimLabelIndex success.`);
}).catch((err: BusinessError) => {
    console.error(`setSimLabelIndex failed, promise: err->${JSON.stringify(err)}`);
});
```

