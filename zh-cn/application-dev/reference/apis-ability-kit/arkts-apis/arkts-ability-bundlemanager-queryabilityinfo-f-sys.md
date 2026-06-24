# queryAbilityInfo（系统接口）

## queryAbilityInfo

```TypeScript
function queryAbilityInfo(want: Want, abilityFlags: number, callback: AsyncCallback<Array<AbilityInfo>>): void
```

���ݸ�����want��abilityFlags��ȡһ������AbilityInfo��ʹ��callback�첽�ص���

��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | ��ʾ����Ҫ��ѯ��Ӧ��Bundle���Ƶ�Want�� |
| abilityFlags | number | 是 | ָ�����ص�AbilityInfo����������Ϣ������ȡֵ����ͬ����ο�[AbilityFlag](arkts-ability-bundlemanager-abilityflag-e-sys.md#AbilityFlag)�� |
| callback | AsyncCallback&lt;Array&lt;AbilityInfo&gt;&gt; | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������ȡ�ɹ�ʱ��errΪ<br/>undefined��dataΪ��ȡ����Array������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. At least one parameter(action, entity, uri or type) is required for implicit<br/>query. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified ability is not found. |
| [17700026](../../errorcode-universal.md#17700026-The) | The specified bundle is disabled. |
| [17700029](../../errorcode-universal.md#17700029-The) | The specified ability is disabled. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Want } from '@kit.AbilityKit';

let abilityFlags = bundleManager.AbilityFlag.GET_ABILITY_INFO_DEFAULT;
let want: Want = {
  bundleName: "com.example.myapplication",
  abilityName: "EntryAbility"
};

try {
  bundleManager.queryAbilityInfo(want, abilityFlags, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'queryAbilityInfo successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed: %{public}s', message);
}

```


## queryAbilityInfo

```TypeScript
function queryAbilityInfo(want: Want, abilityFlags: number, userId: number, callback: AsyncCallback<Array<AbilityInfo>>): void
```

���ݸ�����want��abilityFlags��userId��ȡ���AbilityInfo��ʹ��callback�첽�ص���

��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | ��ʾ����Ҫ��ѯ��Ӧ��Bundle���Ƶ�Want�� |
| abilityFlags | number | 是 | ָ�����ص�AbilityInfo����������Ϣ������ȡֵ����ͬ����ο�[AbilityFlag](arkts-ability-bundlemanager-abilityflag-e-sys.md#AbilityFlag)�� |
| userId | number | 是 | ��ʾ�û�ID������ͨ��<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ�� |
| callback | AsyncCallback&lt;Array&lt;AbilityInfo&gt;&gt; | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������ȡ�ɹ�ʱ��errΪ<br/>undefined��dataΪ��ȡ����Array������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. At least one parameter(action, entity, uri or type) is required for implicit<br/>query. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified ability is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified userId is invalid. |
| [17700026](../../errorcode-universal.md#17700026-The) | The specified bundle is disabled. |
| [17700029](../../errorcode-universal.md#17700029-The) | The specified ability is disabled. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Want } from '@kit.AbilityKit';

let abilityFlags = bundleManager.AbilityFlag.GET_ABILITY_INFO_DEFAULT;
let userId = 100;
let want: Want = {
  bundleName: "com.example.myapplication",
  abilityName: "EntryAbility"
};

try {
  bundleManager.queryAbilityInfo(want, abilityFlags, userId, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'queryAbilityInfo successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed: %{public}s', message);
}

```


## queryAbilityInfo

```TypeScript
function queryAbilityInfo(want: Want, abilityFlags: number, userId?: number): Promise<Array<AbilityInfo>>
```

���ݸ�����want��abilityFlags��userId��ȡһ������AbilityInfo��ʹ��Promise�첽�ص���

��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | ��ʾ����Ҫ��ѯ��Ӧ��Bundle���Ƶ�Want�� |
| abilityFlags | number | 是 | ��ʾָ�����ص�AbilityInfo����������Ϣ������ȡֵ����ͬ����ο�[AbilityFlag](arkts-ability-bundlemanager-abilityflag-e-sys.md#AbilityFlag)�� |
| userId | number | 否 | ��ʾ�û�ID������ͨ��<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ��Ĭ��ֵ�����÷������û���ȡֵ��Χ�����ڵ���0�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AbilityInfo&gt;&gt; | Promise���󣬷���Array�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. At least one parameter(action, entity, uri or type) is required for implicit<br/>query. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified ability is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified userId is invalid. |
| [17700026](../../errorcode-universal.md#17700026-The) | The specified bundle is disabled. |
| [17700029](../../errorcode-universal.md#17700029-The) | The specified ability is disabled. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Want } from '@kit.AbilityKit';

let abilityFlags = bundleManager.AbilityFlag.GET_ABILITY_INFO_DEFAULT;
let userId = 100;
let want: Want = {
  bundleName: "com.example.myapplication",
  abilityName: "EntryAbility"
};

try {
  bundleManager.queryAbilityInfo(want, abilityFlags, userId).then((data) => {
    hilog.info(0x0000, 'testTag', 'queryAbilityInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed. Cause: %{public}s', message);
}

```

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Want } from '@kit.AbilityKit';

let abilityFlags = bundleManager.AbilityFlag.GET_ABILITY_INFO_DEFAULT;
let want: Want = {
  bundleName: "com.example.myapplication",
  abilityName: "EntryAbility"
};

try {
  bundleManager.queryAbilityInfo(want, abilityFlags).then((data) => {
    hilog.info(0x0000, 'testTag', 'queryAbilityInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed. Cause: %{public}s', err.message);
  })
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed. Cause: %{public}s', message);
}

```


## queryAbilityInfo

```TypeScript
function queryAbilityInfo(wants: Array<Want>, abilityFlags: number, userId?: number): Promise<Array<AbilityInfo>>
```

���ݸ�����want�б���abilityFlags��userId��ȡһ������AbilityInfo��ʹ��Promise�첽�ص���

��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�

**起始版本：** 12

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wants | Array&lt;Want&gt; | 是 | ��ʾ����Ҫ��ѯ��Ӧ��Bundle���Ƶ�Want���ϡ� |
| abilityFlags | number | 是 | ��ʾָ�����ص�AbilityInfo����������Ϣ������ȡֵ����ͬ����ο�[AbilityFlag](arkts-ability-bundlemanager-abilityflag-e-sys.md#AbilityFlag)�� |
| userId | number | 否 | ��ʾ�û�ID������ͨ��<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ��Ĭ��ֵ�����÷������û���ȡֵ��Χ�����ڵ���0�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AbilityInfo&gt;&gt; | Promise���󣬷���Array��Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. At least one parameter(action, entity, uri or type) is required for implicit<br/>query. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified ability is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified userId is invalid. |
| [17700026](../../errorcode-universal.md#17700026-The) | The specified bundle is disabled. |
| [17700029](../../errorcode-universal.md#17700029-The) | The specified ability is disabled. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Want } from '@kit.AbilityKit';

let abilityFlags = bundleManager.AbilityFlag.GET_ABILITY_INFO_DEFAULT;
let userId = 100;
let want: Want = {
  bundleName: "com.example.myapplication1",
  abilityName: "EntryAbility"
};
let want1: Want = {
  bundleName: "com.example.myapplication2",
  abilityName: "EntryAbility"
};
let wants: Array<Want> = [want, want1];
try {
  bundleManager.queryAbilityInfo(wants, abilityFlags, userId).then((data) => {
    hilog.info(0x0000, 'testTag', 'queryAbilityInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed. Cause: %{public}s', err.message);
  })
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed. Cause: %{public}s', message);
}

```

