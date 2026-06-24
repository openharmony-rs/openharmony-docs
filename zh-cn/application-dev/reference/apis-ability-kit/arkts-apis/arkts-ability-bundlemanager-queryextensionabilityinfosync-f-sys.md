# queryExtensionAbilityInfoSync（系统接口）

## queryExtensionAbilityInfoSync

```TypeScript
function queryExtensionAbilityInfoSync(want: Want, extensionAbilityType: ExtensionAbilityType,
    extensionAbilityFlags: number, userId?: number): Array<ExtensionAbilityInfo>
```

��ͬ���������ݸ�����want��extensionAbilityType��extensionAbilityFlags��userId��ȡExtensionAbilityInfo��

��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�

**起始版本：** 10

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
| Array&lt;ExtensionAbilityInfo&gt; | Array��Ϣ�� |

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
  let extensionAbilityInfos = bundleManager.queryExtensionAbilityInfoSync(want, extensionAbilityType, extensionFlags, userId);
  hilog.info(0x0000, 'testTag', 'queryExtensionAbilityInfoSync successfully. Data: %{public}s',
    JSON.stringify(extensionAbilityInfos));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryExtensionAbilityInfoSync failed. Cause: %{public}s', message);
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
  let extensionAbilityInfos = bundleManager.queryExtensionAbilityInfoSync(want, extensionAbilityType, extensionFlags);
  hilog.info(0x0000, 'testTag', 'queryExtensionAbilityInfoSync successfully. Data: %{public}s',
    JSON.stringify(extensionAbilityInfos));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryExtensionAbilityInfoSync failed. Cause: %{public}s', message);
}

```


## queryExtensionAbilityInfoSync

```TypeScript
function queryExtensionAbilityInfoSync(want: Want, extensionAbilityType: string,
    extensionAbilityFlags: number, userId?: number): Array<ExtensionAbilityInfo>
```

���ݸ�����want��extensionAbilityType��extensionAbilityFlags��userId��ȡExtensionAbilityInfo��ʹ��ͬ����ʽ���ؽ����

��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�

**起始版本：** 11

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | ��ʾ����Ҫ��ѯ��Ӧ��Bundle���Ƶ�Want�� |
| extensionAbilityType | string | 是 | ��ʾ�Զ���extensionAbility�����͡� |
| extensionAbilityFlags | number | 是 | ��ʾ���ص�ExtensionInfo��������Ҫ��������Ϣ��־������ȡֵ����ͬ����ο�<br/>[ExtensionAbilityFlag](arkts-ability-bundlemanager-extensionabilityflag-e-sys.md#ExtensionAbilityFlag)�� |
| userId | number | 否 | ��ʾ�û�ID������ͨ��<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ��Ĭ��ֵ�����÷������û���ȡֵ��Χ�����ڵ���0�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;ExtensionAbilityInfo&gt; | ͬ������Array�� |

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
// 示例接口带userId参数查询
import { bundleManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let extensionAbilityType = "form";
let extensionFlags = bundleManager.ExtensionAbilityFlag.GET_EXTENSION_ABILITY_INFO_DEFAULT;
let userId = 100;
let want: Want = {
  bundleName : "com.example.myapplication",
  abilityName : "EntryAbility"
};

try {
  let data = bundleManager.queryExtensionAbilityInfoSync(want, extensionAbilityType, extensionFlags, userId)
  hilog.info(0x0000, 'testTag', 'queryExtensionAbilityInfoSync successfully. Data: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryExtensionAbilityInfoSync failed: %{public}s', message);
}

```

```TypeScript
// 示例接口不带userId参数查询
import { bundleManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let extensionAbilityType = "form";
let extensionFlags = bundleManager.ExtensionAbilityFlag.GET_EXTENSION_ABILITY_INFO_DEFAULT;
let want: Want = {
  bundleName: "com.example.myapplication",
  abilityName: "EntryAbility"
};

try {
  let data = bundleManager.queryExtensionAbilityInfoSync(want, extensionAbilityType, extensionFlags);
  hilog.info(0x0000, 'testTag', 'queryExtensionAbilityInfoSync successfully. Data: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryExtensionAbilityInfoSync failed: %{public}s', message);
}

```


## queryExtensionAbilityInfoSync

```TypeScript
function queryExtensionAbilityInfoSync(extensionAbilityType: string, extensionAbilityFlags: number,
    userId?: number): Array<ExtensionAbilityInfo>
```

���ݸ�����extensionAbilityType��extensionAbilityFlags��userId��ȡExtensionAbilityInfo��

��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�

**起始版本：** 11

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| extensionAbilityType | string | 是 | ��ʾ�Զ���extensionAbility�����͡� |
| extensionAbilityFlags | number | 是 | ��ʾ���ص�ExtensionInfo��������Ҫ��������Ϣ��־������ȡֵ����ͬ����ο�<br/>[ExtensionAbilityFlag](arkts-ability-bundlemanager-extensionabilityflag-e-sys.md#ExtensionAbilityFlag)�� |
| userId | number | 否 | ��ʾ�û�ID������ͨ��<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ��Ĭ��ֵ�����÷������û�ID��ȡֵ��Χ�����ڵ���0�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;ExtensionAbilityInfo&gt; | ͬ������Array�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter extensionAbilityType is empty. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified extensionAbility is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified userId is invalid. |

**示例：**

```TypeScript
// 示例接口带userId参数查询
import { bundleManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let extensionAbilityType = "form";
let extensionFlags = bundleManager.ExtensionAbilityFlag.GET_EXTENSION_ABILITY_INFO_DEFAULT;
let userId = 100;

try {
  let data = bundleManager.queryExtensionAbilityInfoSync(extensionAbilityType, extensionFlags, userId)
  hilog.info(0x0000, 'testTag', 'queryExtensionAbilityInfoSync successfully. Data: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryExtensionAbilityInfoSync failed: %{public}s', message);
}

```

```TypeScript
// 示例接口不带userId参数查询
import { bundleManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let extensionAbilityType = "form";
let extensionFlags = bundleManager.ExtensionAbilityFlag.GET_EXTENSION_ABILITY_INFO_DEFAULT;

try {
  let data = bundleManager.queryExtensionAbilityInfoSync(extensionAbilityType, extensionFlags);
  hilog.info(0x0000, 'testTag', 'queryExtensionAbilityInfoSync successfully. Data: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryExtensionAbilityInfoSync failed: %{public}s', message);
}

```

