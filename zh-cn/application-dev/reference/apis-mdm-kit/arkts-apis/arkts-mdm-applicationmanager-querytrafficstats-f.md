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

��ѯ��ǰ�û���ָ��Ӧ�����ض�ʱ�����ʹ�����������ʹ��Promise�첽�ص���

> **˵����**
>
> ������������ͣ�networkInfo.type����֧�ַ������磨connection.NetBearType.BEARER_CELLULAR����Wi-Fi���磨
> connection.NetBearType.BEARER_WIFI��������������ֵ���ӿڻ᷵�ش�����9200012��
>
> �������ʼʱ�䣨networkInfo.startTime��������ʱ�䣨networkInfo.endTime��Ϊ�뼶ʱ��������������ʼʱ�䡢����ʱ��Ϊ����������ʼʱ����ڽ���ʱ�䣬�ӿڻ᷵�ش�����9200012��
>
> ������û�ID��accountId���ǵ�ǰ�û�ʱ���ӿڻ᷵�ش�����9200012��
>
> �����ѯ��ʱ����������ʱ��-��ʼʱ�䣩��СΪ1�죬���Ϊ30�졣ʱ����̫С����ѯ������ܲ�׼ȷ��ʱ����̫�󣬲�ѯ��ʱ��ܳ���

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| bundleName | string | 是 | Ӧ�õİ����� |
| appIndex | number | 是 | Ӧ�÷�������<br/><br/>ȡֵӦΪ��0��������<br/>- Ӧ�÷���������ȡֵ��Χ�����ڵ���0��������<br/>appIndex����ͨ��@ohos.bundle.bundleManager�е�<br/>[getAppCloneIdentity](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getappcloneidentity-f.md#getAppCloneIdentity-1)�Ƚӿ�����ȡ�� |
| accountId | number | 是 | �û�ID<br/><br/>ȡֵӦΪ��0��������<br/><br/>accountId����ͨ��@ohos.account.osAccount�е�<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2)�Ƚӿ�����ȡ�� |
| networkInfo | statistics.NetworkInfo | 是 | ������Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;statistics.NetStatsInfo&gt; | returns the detailed network statistics information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

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

