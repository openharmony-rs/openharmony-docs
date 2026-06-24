# queryExtensionAbilityInfo（系统接口）

## queryExtensionAbilityInfo

```TypeScript
function queryExtensionAbilityInfo(want: Want, extensionAbilityType: ExtensionAbilityType,
      extensionAbilityFlags: number, callback: AsyncCallback<Array<ExtensionAbilityInfo>>): void
```

���ݸ�����want��extensionAbilityType��extensionAbilityFlags��ȡһ������ExtensionAbilityInfo��ʹ��callback�첽�ص���

��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | ��ʾ����Ҫ��ѯ��Ӧ��Bundle���Ƶ�Want�� |
| extensionAbilityType | ExtensionAbilityType | 是 | ��ʶextensionAbility�����͡� |
| extensionAbilityFlags | number | 是 | ��ʾ����ָ�������ص�ExtensionInfo�����а�������Ϣ�ı�־������ȡֵ����ͬ����ο�<br/>[ExtensionAbilityFlag](arkts-ability-bundlemanager-extensionabilityflag-e-sys.md#ExtensionAbilityFlag)�� |
| callback | AsyncCallback&lt;Array&lt;ExtensionAbilityInfo&gt;&gt; | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������<br/>ȡ�ɹ�ʱ��errΪundefined��dataΪ��ȡ��Array������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. At least one parameter(action, entity, uri or type) is required for implicit<br/>query. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified extensionAbility is not found. |
| [17700026](../../errorcode-universal.md#17700026-The) | The specified bundle is disabled. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Want } from '@kit.AbilityKit';

let extensionAbilityType = bundleManager.ExtensionAbilityType.FORM;
let extensionFlags = bundleManager.ExtensionAbilityFlag.GET_EXTENSION_ABILITY_INFO_DEFAULT;
let want: Want = {
  bundleName: "com.example.myapplication",
  abilityName: "EntryAbility"
};

try {
  bundleManager.queryExtensionAbilityInfo(want, extensionAbilityType, extensionFlags, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'queryExtensionAbilityInfo failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'queryExtensionAbilityInfo successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryExtensionAbilityInfo failed: %{public}s', message);
}

```


## queryExtensionAbilityInfo

```TypeScript
function queryExtensionAbilityInfo(want: Want, extensionAbilityType: ExtensionAbilityType, extensionAbilityFlags: number, userId: number, callback: AsyncCallback<Array<ExtensionAbilityInfo>>): void
```

���ݸ�����want��extensionAbilityType��extensionAbilityFlags��userId��ȡһ������ExtensionAbilityInfo��ʹ��callback�첽�ص���

��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | ��ʾ����Ҫ��ѯ��Ӧ��Bundle���Ƶ�Want�� |
| extensionAbilityType | ExtensionAbilityType | 是 | ��ʶextensionAbility�����͡� |
| extensionAbilityFlags | number | 是 | ��ʾ����ָ�������ص�ExtensionInfo�����а�������Ϣ�ı�־������ȡֵ����ͬ����ο�<br/>[ExtensionAbilityFlag](arkts-ability-bundlemanager-extensionabilityflag-e-sys.md#ExtensionAbilityFlag)�� |
| userId | number | 是 | ��ʾ�û�ID������ͨ��<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ�� |
| callback | AsyncCallback&lt;Array&lt;ExtensionAbilityInfo&gt;&gt; | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������<br/>ȡ�ɹ�ʱ��errΪundefined��dataΪ��ȡ��Array������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. At least one parameter(action, entity, uri or type) is required for implicit<br/>query. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified extensionAbility is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified userId is invalid. |
| [17700026](../../errorcode-universal.md#17700026-The) | The specified bundle is disabled. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Want } from '@kit.AbilityKit';

let extensionAbilityType = bundleManager.ExtensionAbilityType.FORM;
let extensionFlags = bundleManager.ExtensionAbilityFlag.GET_EXTENSION_ABILITY_INFO_DEFAULT;
let userId = 100;
let want: Want = {
  bundleName: "com.example.myapplication",
  abilityName: "EntryAbility"
};

try {
  bundleManager.queryExtensionAbilityInfo(want, extensionAbilityType, extensionFlags, userId, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'queryExtensionAbilityInfo failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'queryExtensionAbilityInfo successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryExtensionAbilityInfo failed: %{public}s', message);
}

```


## queryExtensionAbilityInfo

```TypeScript
function queryExtensionAbilityInfo(want: Want, extensionAbilityType: ExtensionAbilityType, extensionAbilityFlags: number, userId?: number): Promise<Array<ExtensionAbilityInfo>>
```

���ݸ�����want��extensionAbilityType��extensionAbilityFlags��userId��ȡExtensionAbilityInfo��ʹ��Promise�첽�ص���

��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | ��ʾ����Ҫ��ѯ��Ӧ��Bundle���Ƶ�Want�� |
| extensionAbilityType | ExtensionAbilityType | 是 | ��ʶextensionAbility�����͡� |
| extensionAbilityFlags | number | 是 | ��ʾ����ָ�������ص�ExtensionInfo�����а�������Ϣ�ı�־������ȡֵ����ͬ����ο�<br/>[ExtensionAbilityFlag](arkts-ability-bundlemanager-extensionabilityflag-e-sys.md#ExtensionAbilityFlag)�� |
| userId | number | 否 | ��ʾ�û�ID������ͨ��<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ��Ĭ��ֵ�����÷������û���ȡֵ��Χ�����ڵ���0�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ExtensionAbilityInfo&gt;&gt; | Promise���󣬷���Array�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. At least one parameter(action, entity, uri or type) is required for implicit<br/>query. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified extensionAbility is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified userId is invalid. |
| [17700026](../../errorcode-universal.md#17700026-The) | The specified bundle is disabled. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Want } from '@kit.AbilityKit';

let extensionAbilityType = bundleManager.ExtensionAbilityType.FORM;
let extensionFlags = bundleManager.ExtensionAbilityFlag.GET_EXTENSION_ABILITY_INFO_DEFAULT;
let userId = 100;
let want: Want = {
  bundleName: "com.example.myapplication",
  abilityName: "EntryAbility"
};

try {
  bundleManager.queryExtensionAbilityInfo(want, extensionAbilityType, extensionFlags, userId).then((data) => {
    hilog.info(0x0000, 'testTag', 'queryExtensionAbilityInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'queryExtensionAbilityInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryExtensionAbilityInfo failed. Cause: %{public}s', message);
}

```

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Want } from '@kit.AbilityKit';

let extensionAbilityType = bundleManager.ExtensionAbilityType.FORM;
let extensionFlags = bundleManager.ExtensionAbilityFlag.GET_EXTENSION_ABILITY_INFO_DEFAULT;
let want: Want = {
  bundleName: "com.example.myapplication",
  abilityName: "EntryAbility"
};

try {
  bundleManager.queryExtensionAbilityInfo(want, extensionAbilityType, extensionFlags).then((data) => {
    hilog.info(0x0000, 'testTag', 'queryExtensionAbilityInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'queryExtensionAbilityInfo failed. Cause: %{public}s', err.message);
  })
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryExtensionAbilityInfo failed. Cause: %{public}s', message);
}

```

