# getRadioTech

## 导入模块

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## getRadioTech

```TypeScript
function getRadioTech(slotId: number, callback: AsyncCallback<NetworkRadioTech>): void
```

获取当前接入的CS域和PS域无线接入技术。使用callback异步回调。其中，CS域为电路交换域，PS为分组交换域。

**起始版本：** 6

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。<br>- 0：卡槽1。<br>- 1：卡槽2。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[NetworkRadioTech](arkts-telephony-radio-networkradiotech-i.md)&gt; | 是 | 回调函数。返回当前接入的CS域和PS域无线接入技术。其中，CS域为电路交换域，PS为分组交换域。<br>**适用版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 指定卡槽ID，0表示卡槽1
let slotId: number = 0;
// 获取当前接入的CS域和PS域无线接入技术
radio.getRadioTech(slotId, (err: BusinessError, data: radio.NetworkRadioTech) => {
    if (err) {
        console.error(`getRadioTech failed, callback: err code: ${err.code}, message: ${err.message}`);
        return;
    }
    console.info(`getRadioTech success, callback: data->${JSON.stringify(data)}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.getRadioTech(slotId).then((data: radio.NetworkRadioTech) => {
    console.info(`getRadioTech success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getRadioTech failed, promise: err code: ${err.code}, message: ${err.message}`);
});
```


## getRadioTech

```TypeScript
function getRadioTech(slotId: number): Promise<NetworkRadioTech>
```

获取当前接入的CS域和PS域无线接入技术。使用Promise异步回调。其中，CS域为电路交换域，PS为分组交换域。

**起始版本：** 6

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。<br>- 0：卡槽1。<br>- 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;{psRadioTech: RadioTechnology, csRadioTech: RadioTechnology}&gt; | 以Promise形式返回当前接入的CS域和PS域技术。CS域为电路交换域，PS为分组交换域。<br>**适用版本：** 6 - 10 |
| Promise&lt;[NetworkRadioTech](arkts-telephony-radio-networkradiotech-i.md)&gt; | Returns the RAT of PS domain and CS domain of registered network. The values of RAT are as follows: &lt;ul&gt; &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_UNKNOWN` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_GSM` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_1XRTT` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_WCDMA` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_HSPA` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_HSPAP` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_TD_SCDMA` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_EVDO` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_EHRPD` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_LTE` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_LTE_CA` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_IWLAN` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_NR` &lt;/ul&gt;<br>**适用版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例**

参见 [getRadioTech](#getradiotech)
