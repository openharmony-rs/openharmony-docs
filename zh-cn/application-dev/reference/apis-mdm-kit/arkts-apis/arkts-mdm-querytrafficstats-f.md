# queryTrafficStats

## queryTrafficStats

```TypeScript
function queryTrafficStats(
    admin: Want,
    bundleName: string,
    appIndex: number,
    accountId: number,
    networkInfo: statistics.NetworkInfo
  ): Promise<statistics.NetStatsInfo>
```

查询当前用户下指定应用在特定时间段内使用流量情况。使用Promise异步回调。

> **说明：**
>
> 传入的网络类型（networkInfo.type）仅支持蜂窝网络（connection.NetBearType.BEARER_CELLULAR）和Wi-Fi网络（
> connection.NetBearType.BEARER_WIFI）。若传入其他值，接口会返回错误码9200012。
>
> 传入的起始时间（networkInfo.startTime）、结束时间（networkInfo.endTime）为秒级时间戳。若传入的起始时间、结束时间为负数，或起始时间大于结束时间，接口会返回错误码9200012。
>
> 传入的用户ID（accountId）非当前用户时，接口会返回错误码9200012。
>
> 建议查询的时间间隔（结束时间-起始时间）最小为1天，最大为30天。时间间隔太小，查询结果可能不准确。时间间隔太大，查询耗时会很长。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| bundleName | string | 是 | 应用的包名。 |
| appIndex | number | 是 | 应用分身索引<br>取值应为≥0的整数。- 应用分身索引，取值范围：大于等于0的整数。<br> appIndex可以通过@ohos.bundle.bundleManager中的[getAppCloneIdentity](../../apis-ability-kit/arkts-apis/arkts-ability-getappcloneidentity-f.md#getappcloneidentity-1)等接口来获取。 |
| accountId | number | 是 | 用户ID<br>取值应为≥0的整数。<br>accountId可以通过@ohos.account.osAccount中的[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-accountmanager-i.md#getosaccountlocalid-2)等接口来获取。 |
| networkInfo | statistics.NetworkInfo | 是 | 网络信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;statistics.NetStatsInfo&gt; | returns the detailed network statistics information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { connection, statistics } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

async function queryTrafficStats() {
  let wantTemp: Want = {
    // 需根据实际情况进行替换
    bundleName: 'com.example.myapplication',
    abilityName: 'EnterpriseAdminAbility'
  };
  // 需根据实际情况进行替换
  let bundleName: string = 'com.example.test';
  let appIndex: number = 0;
  let accountId: number = 100;
  // 示例代码使用sim.getSimAccountInfo获取simId
  let slotId: number = 0;
  let simId: number = 0;
  await sim.getSimAccountInfo(slotId).then((data: sim.IccAccountInfo) => {
    simId = data.simId;
  }).catch((err: BusinessError) => {
    console.error(`getSimAccountInfo failed, promise: err->${JSON.stringify(err)}`);
  });
  let networkInfo: statistics.NetworkInfo = {
    // 需根据实际情况进行替换
    type: connection.NetBearType.BEARER_CELLULAR,
    // 查询2026/4/15 00:00:00.000 ~ 2026/4/16 00:00:00.000的数据（月份从0开始计算）
    startTime: Math.floor(new Date(2026, 3, 15, 0, 0, 0, 0).getTime() / 1000),
    endTime: Math.floor(new Date(2026, 3, 16, 0, 0, 0, 0).getTime() / 1000),
    // 网络类型为BEARER_CELLULAR时，需要传simId；网络类型为BEARER_WIFI时，不需要传simId；
    simId: simId
  }
  await applicationManager.queryTrafficStats(wantTemp, bundleName, appIndex, accountId, networkInfo)
    .then(result => {
      console.info('Succeeded in querying traffic stats.');
    }).catch((error: BusinessError) => {
      console.error(`Failed to query traffic stats. Code is ${error.code}, message is ${error.message}`);
    })
}

```

