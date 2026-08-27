# getDownloadableProfiles（系统接口）

## 导入模块

```TypeScript
```

## getDownloadableProfiles

```TypeScript
function getDownloadableProfiles(slotId: number, portIndex: number,
                                   forceDisableProfile: boolean): Promise<GetDownloadableProfilesResult>
```

获取可用的可下载配置文件列表。使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.GET_TELEPHONY_ESIM_STATE

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |
| portIndex | number | 是 | 插槽的端口索引。 |
| forceDisableProfile | boolean | 是 | 是否可直接去激活配置文件。true表示切换配置文件时，如果需要去激活当前的配置文件，则可以直接操作。false表示如果需要去激活当前的配置文件，则会 返回错误，并得到用户授权后再继续调用该接口，执行切换配置文件操作。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[GetDownloadableProfilesResult](arkts-telephony-esim-getdownloadableprofilesresult-i-sys.md)&gt; | Promise对象，返回可下载配置文件列表。 |

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

eSIM.getDownloadableProfiles(1, 0, true).then((data: eSIM.GetDownloadableProfilesResult) => {
    console.info(`getDownloadableProfiles, GetDownloadableProfilesResult: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError<void>) => {
    console.error(`getDownloadableProfiles, GetDownloadableProfilesResult: err->${JSON.stringify(err)}`);
});
```
