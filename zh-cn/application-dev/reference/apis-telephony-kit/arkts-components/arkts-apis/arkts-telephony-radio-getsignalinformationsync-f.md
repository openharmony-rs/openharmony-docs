# getSignalInformationSync

## 导入模块

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## getSignalInformationSync

```TypeScript
function getSignalInformationSync(slotId: number): Array<SignalInformation>
```

获取指定SIM卡槽对应的注册网络信号强度信息列表。

**起始版本：** 10

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。<br>- 0：卡槽1。<br>- 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[SignalInformation](arkts-telephony-radio-signalinformation-i.md)&gt; | 返回网络信号强度[SignalInformation](arkts-telephony-radio-signalinformation-i.md)子类对象的数组。 |

**示例**

```TypeScript
let slotId: number = 0;
try {
    let signalInfo: Array<radio.SignalInformation> = radio.getSignalInformationSync(slotId);
    console.info(`signal information size is:` + signalInfo.length);
} catch (err) {
    console.error(`getSignalInformationSync failed, err->${JSON.stringify(err)}`);
}
```
