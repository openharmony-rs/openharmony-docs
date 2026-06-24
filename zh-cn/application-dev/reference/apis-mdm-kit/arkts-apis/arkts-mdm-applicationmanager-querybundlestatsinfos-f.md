# queryBundleStatsInfos

## queryBundleStatsInfos

```TypeScript
function queryBundleStatsInfos(admin: Want, startTime: number, endTime: number, accountId: number): Array<BundleStatsInfo>
```

��ѯָ���û��˻��ڸ���ʱ����ڣ���Ӧ����ǰ̨���е��ۼ�ʱ��ͳ����Ϣ����ѯ����С�������죬����ʱ��Ҫ������ʼʱ�䣨startTime��������ʱ�䣨endTime���Լ�Ŀ���û��˻�ID��accountId�����������startTime
��endTimeΪ���뼶ʱ�����֧�ֵ��÷������Զ���ֵ��startTimeĬ��ȡ�����00:00:00.000��endTimeĬ��ȡ�����24:00:00.000����������㣩����������ӿڷ���BundleStatsInfo���飬
ÿ��Ԫ�ذ���һ��Ӧ�õİ��������������ֵ�����Ӧʱ����ڵ�ǰ̨ʹ��ʱ�������뼶ʱ���������startTimeΪ0�����ʾ���豸�״ο�����ʱ�俪ʼ��ѯ������ʼʱ�����ڽ���ʱ�䣬�ӿڽ����ش�����9200012��

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| startTime | number | 是 | ��ѯ��ʼʱ��<br/><br/>��λΪ�� ���룬ȡֵӦΪ��0�������� |
| endTime | number | 是 | ��ѯ����ʱ�䣬��λ�����루ʱ�����<br/><br/>��λΪ�� ���룬ȡֵӦΪ��0�������� |
| accountId | number | 是 | accountIdΪ����ϵͳ�ʻ��ı���ID��<br/><br/>ȡֵӦΪ��0��������<br/>- �û�ID��ȡֵ��Χ�����ڵ���0��������<br/>accountId����ͨ��@ohos.account.osAccount�е�<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2)�Ƚӿ�����ȡ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;BundleStatsInfo&gt; | ����Ӧ�ð�ͳ����Ϣ�����顣 |

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

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 查询2026/4/15 00:00:00.000 ~ 2026/4/16 23:59:59.999的数据（月份从0开始计算）
  let startTime: number = new Date(2026, 3, 15, 0, 0, 0, 0).getTime();
  let endTime: number = new Date(2026, 3, 16, 23, 59, 59, 999).getTime();
  let accountId: number = 100;
  let result: Array<applicationManager.BundleStatsInfo> = applicationManager.queryBundleStatsInfos(wantTemp, startTime, endTime, accountId);
  console.info(`Succeeded in querying bundle stats infos, result : ${JSON.stringify(result)}`);
} catch(err) {
  console.error(`Failed to query bundle stats infos. Code: ${err.code}, message: ${err.message}`);
}

```

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 查询上个月的一个月的数据
  // 获取当前日期
  let currentDate: Date = new Date();
  // 计算上个月的第一天（月份从0开始，所以当前月份减1）
  let lastMonthFirstDay: Date = new Date(currentDate.getFullYear(), currentDate.getMonth() - 1, 1, 0, 0, 0, 0);
  // 计算上个月的最后一天（下个月第0天即为本月最后一天）
  let lastMonthLastDay: Date = new Date(currentDate.getFullYear(), currentDate.getMonth(), 0, 23, 59, 59, 999);
  
  let startTime: number = lastMonthFirstDay.getTime();
  let endTime: number = lastMonthLastDay.getTime();
  let accountId: number = 100;
  let result: Array<applicationManager.BundleStatsInfo> = applicationManager.queryBundleStatsInfos(wantTemp, startTime, endTime, accountId);
  console.info(`Succeeded in querying bundle stats infos, result : ${JSON.stringify(result)}`);
} catch(err) {
  console.error(`Failed to query bundle stats infos. Code: ${err.code}, message: ${err.message}`);
}

```

