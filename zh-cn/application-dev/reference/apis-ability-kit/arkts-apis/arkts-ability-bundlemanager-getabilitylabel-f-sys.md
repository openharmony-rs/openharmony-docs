# getAbilityLabel（系统接口）

## getAbilityLabel

```TypeScript
function getAbilityLabel(bundleName: string, moduleName: string, abilityName: string, callback: AsyncCallback<string>): void
```

��ȡָ��bundleName��moduleName��abilityName��label��ʹ��callback�첽�ص���

��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ʾӦ�ó����bundleName�� |
| moduleName | string | 是 | ��ʾModule���ơ� |
| abilityName | string | 是 | ��ʾUIAbility��������ơ� |
| callback | AsyncCallback&lt;string&gt; | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������ȡ�ɹ�ʱ��errΪundefined��<br/>dataΪ��ָ�������Labelֵ������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700002](../../errorcode-universal.md#17700002-The) | The specified moduleName is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified abilityName is not found. |
| [17700026](../../errorcode-universal.md#17700026-The) | The specified bundle is disabled. |
| [17700029](../../errorcode-universal.md#17700029-The) | The specified ability is disabled. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';
let moduleName = 'entry';
let abilityName = 'EntryAbility';

try {
  bundleManager.getAbilityLabel(bundleName, moduleName, abilityName, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getAbilityLabel failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'getAbilityLabel successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAbilityLabel failed: %{public}s', message);
}

```


## getAbilityLabel

```TypeScript
function getAbilityLabel(bundleName: string, moduleName: string, abilityName: string): Promise<string>
```

��ȡָ��bundleName��moduleName��abilityName��label��ʹ��Promise�첽�ص���

��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ʾӦ�ó����bundleName�� |
| moduleName | string | 是 | ��ʾModule���ơ� |
| abilityName | string | 是 | ��ʾUIAbility��������ơ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise���󣬷���ָ�������labelֵ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700002](../../errorcode-universal.md#17700002-The) | The specified moduleName is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified abilityName is not found. |
| [17700026](../../errorcode-universal.md#17700026-The) | The specified bundle is disabled. |
| [17700029](../../errorcode-universal.md#17700029-The) | The specified ability is disabled. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';
let moduleName = 'entry';
let abilityName = 'EntryAbility';

try {
  bundleManager.getAbilityLabel(bundleName, moduleName, abilityName).then((data) => {
    hilog.info(0x0000, 'testTag', 'getAbilityLabel successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAbilityLabel failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAbilityLabel failed. Cause: %{public}s', message);
}

```

