# getImsRegInfo（系统接口）

## 导入模块

```TypeScript
```

## getImsRegInfo

```TypeScript
function getImsRegInfo(slotId: number, imsType: ImsServiceType, callback: AsyncCallback<ImsRegInfo>): void
```

Get the IMS registration state info of specified IMS service type.

**起始版本：** 9

**需要权限：** ohos.permission.GET_TELEPHONY_STATE

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device. |
| imsType | [ImsServiceType](arkts-telephony-radio-imsservicetype-e-sys.md) | 是 | Indicates the ims service type of the [ImsServiceType](arkts-telephony-radio-imsservicetype-e-sys.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ImsRegInfo](arkts-telephony-radio-imsreginfo-i-sys.md)&gt; | 是 | Indicates an instance of the [ImsRegInfo](arkts-telephony-radio-imsreginfo-i-sys.md) class. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
let mode: radio.ImsServiceType = radio.ImsServiceType.TYPE_VIDEO;
radio.getImsRegInfo(slotId, mode, (err: BusinessError, data: radio.ImsRegInfo) => {
    if (err) {
        console.error(`getImsRegInfo failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`getImsRegInfo success, callback: data->${JSON.stringify(data)}`);
});
```


## getImsRegInfo

```TypeScript
function getImsRegInfo(slotId: number, imsType: ImsServiceType): Promise<ImsRegInfo>
```

Get the IMS registration state info of specified IMS service type.

**起始版本：** 9

**需要权限：** ohos.permission.GET_TELEPHONY_STATE

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device. |
| imsType | [ImsServiceType](arkts-telephony-radio-imsservicetype-e-sys.md) | 是 | Indicates the ims service type of the [ImsServiceType](arkts-telephony-radio-imsservicetype-e-sys.md). |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ImsRegInfo](arkts-telephony-radio-imsreginfo-i-sys.md)&gt; | Returns an instance of the { |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
let mode: radio.ImsServiceType = radio.ImsServiceType.TYPE_VIDEO;
radio.getImsRegInfo(slotId, mode).then((data: radio.ImsRegInfo) => {
    console.info(`getImsRegInfo success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getImsRegInfo failed, promise: err->${JSON.stringify(err)}`);
});
```
