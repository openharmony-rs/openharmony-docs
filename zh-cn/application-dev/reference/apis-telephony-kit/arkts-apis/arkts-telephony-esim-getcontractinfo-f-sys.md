# getContractInfo（系统接口）

## 导入模块

```TypeScript
```

## getContractInfo

```TypeScript
function getContractInfo(slotId: number, requestData: ContractRequestData) : Promise<string>
```

获取开通eSIM需要的，加密的esim id等信息。

**起始版本：** 20

**需要权限：** ohos.permission.GET_TELEPHONY_ESIM_STATE

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |
| requestData | [ContractRequestData](arkts-telephony-esim-contractrequestdata-i-sys.md) | 是 | 用来加密的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;string & gt; | Promise对象，返回TLV(Tag-Length-Value)格式的，加密信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3120001](../errorcode-telephony.md#3120001-服务连接失败) | Service connection failed. |
| [3120002](../errorcode-telephony.md#3120002-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

let request: eSIM.ContractRequestData = {
    publicKey: "",
    nonce: "",
    pkid: ""
};

eSIM.getContractInfo(1, request).then((data: string) => {
    console.info(`contract info is:` + data);
}).catch((err: BusinessError<void>) => {
    console.error(`getContractInfo, promise: err->${JSON.stringify(err)}`)
});
```
