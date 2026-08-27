# downloadProfile（系统接口）

## 导入模块

```TypeScript
```

## downloadProfile

```TypeScript
function downloadProfile(slotId: number, portIndex: number, profile: DownloadableProfile,
                           configuration: DownloadConfiguration): Promise<DownloadProfileResult>
```

下载配置文件。使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.SET_TELEPHONY_ESIM_STATE

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |
| portIndex | number | 是 | 插槽的端口索引。 |
| profile | [DownloadableProfile](arkts-telephony-esim-downloadableprofile-i.md) | 是 | 可下载的配置文件信息。 |
| configuration | [DownloadConfiguration](arkts-telephony-esim-downloadconfiguration-i-sys.md) | 是 | 下载的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[DownloadProfileResult](arkts-telephony-esim-downloadprofileresult-i-sys.md)&gt; | Promise对象，返回下载配置文件的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3120001](../errorcode-telephony.md#3120001-服务连接失败) | Service connection failed. |
| [3120002](../errorcode-telephony.md#3120002-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

let profile: eSIM.DownloadableProfile = {
  activationCode: '1',
  confirmationCode:'1',
  carrierName:'test',
  accessRules:[{
    certificateHashHexStr:'test',
    packageName:'com.example.testcoreservice',
    accessType:0
  }]
};

let configuration: eSIM.DownloadConfiguration = {
  switchAfterDownload: true,
  forceDisableProfile: true,
  isPprAllowed: true,
};

eSIM.downloadProfile(1, 0, profile, configuration).then((data: eSIM.DownloadProfileResult) => {
    console.info(`downloadProfile, DownloadProfileResult: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError<void>) => {
    console.error(`downloadProfile, DownloadProfileResult: err->${JSON.stringify(err)}`);
});
```
