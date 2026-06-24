# getJsonProfile（系统接口）

## getJsonProfile

```TypeScript
function getJsonProfile(profileType: ProfileType, bundleName: string, moduleName?: string, userId?: number): string
```

��ͬ���ķ������ݸ�����profileType��bundleName��moduleName��ѯ��Ӧ�����ļ���JSON�ַ�����

��ȡ���÷��Լ��������ļ�ʱ����ҪȨ�ޡ�

**起始版本：** 11

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| profileType | ProfileType | 是 | ��ʾҪ��ѯ�������ļ����͡� |
| bundleName | string | 是 | ��ʾҪ��ѯӦ�ó����bundleName�� |
| moduleName | string | 否 | ��ʾҪ��ѯӦ�ó����module�����ƣ�ȱʡʱ�����ģ���в��ҡ� |
| userId | number | 否 | ��ʾ�û�ID������ͨ��<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ��Ĭ��ֵ�����÷������û���ȡֵ��Χ�����ڵ���0�� [since 12] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | ���������ļ���JSON�ַ����� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700002](../../errorcode-universal.md#17700002-The) | The specified moduleName is not found. |
| [17700024](../../errorcode-universal.md#17700024-Failed) | Failed to get the profile because the specified profile is not found in the<br/>HAP. |
| [17700026](../../errorcode-universal.md#17700026-The) | The specified bundle is disabled. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found.&lt;br&gt;**适用版本：** 12+ |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.example.myapplication';
let moduleName = 'entry';
let profileType = bundleManager.ProfileType.INTENT_PROFILE;

try {
  let data = bundleManager.getJsonProfile(profileType, bundleName, moduleName);
  hilog.info(0x0000, 'testTag', 'getJsonProfile successfully. Data: %{public}s', data);
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getJsonProfile failed: %{public}s', message);
}

```

