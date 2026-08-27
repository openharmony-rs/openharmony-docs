# addProfile

## 导入模块

```TypeScript
```

## addProfile

```TypeScript
function addProfile(profile: DownloadableProfile): Promise<boolean>
```

通过该接口拉起下载界面，允许用户添加单个配置文件。使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.SET_TELEPHONY_ESIM_STATE_OPEN

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| profile | [DownloadableProfile](arkts-telephony-esim-downloadableprofile-i.md) | 是 | 可下载的配置文件信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | 以Promise形式返回最终用户添加单个配置文件的结果。返回true为成功，false为失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3120001](../errorcode-telephony.md#3120001-服务连接失败) | Service connection failed. |
| [3120002](../errorcode-telephony.md#3120002-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

let profile: eSIM.DownloadableProfile = {
  activationCode:'1',
  confirmationCode:'1',
  carrierName:'test',
  accessRules:[{
    certificateHashHexStr:'test',
    packageName:'com.example.testcoreservice',
    accessType:0
  }]
};

eSIM.addProfile(profile).then((result: boolean) => {
    console.info(`addProfile invoking succeeded.`);
}).catch((err: BusinessError) => {
    console.error(`addProfile, promise: err->${JSON.stringify(err)}`);
});
```
