# setAbilityEnabled（系统接口）

## setAbilityEnabled

```TypeScript
function setAbilityEnabled(info: AbilityInfo, appIndex: number, isEnabled: boolean): Promise<void>
```

����ָ��Ӧ�û����Ӧ������Ľ��û�ʹ��״̬��ʹ��Promise�첽�ص���

**起始版本：** 12

**需要权限：** ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | AbilityInfo | 是 | ��Ҫ�����õ������ |
| appIndex | number | 是 | ��ʾ����Ӧ�õ�������<br/>appIndexΪ0ʱ����ʾ������Ӧ������Ľ��û�ʹ��״̬��appIndex����0ʱ����ʾ����ָ������Ӧ������Ľ��û�ʹ��״̬�� |
| isEnabled | boolean | 是 | ֵΪtrue��ʾʹ�ܣ�ֵΪfalse��ʾ���á� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified abilityInfo is not found. |
| [17700061](../../errorcode-universal.md#17700061-AppIndex) | AppIndex not in valid range. |

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
  bundleManager.queryAbilityInfo(want, abilityFlags, userId).then((abilitiesInfo) => {
    hilog.info(0x0000, 'testTag', 'queryAbilityInfo successfully. Data: %{public}s', JSON.stringify(abilitiesInfo));
    let info = abilitiesInfo[0];

    bundleManager.setAbilityEnabled(info, 1, false).then(() => {
      hilog.info(0x0000, "testTag", "setAbilityEnabled successfully.");
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', 'setAbilityEnabled failed: %{public}s', err.message);
    });
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed. Cause: %{public}s', message);
}

```


## setAbilityEnabled

```TypeScript
function setAbilityEnabled(info: AbilityInfo, isEnabled: boolean, callback: AsyncCallback<void>): void
```

����ָ������Ľ��û�ʹ��״̬��ʹ��callback�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | AbilityInfo | 是 | ��Ҫ�����õ������ |
| isEnabled | boolean | 是 | ֵΪtrue��ʾʹ�ܣ�ֵΪfalse��ʾ���á� |
| callback | AsyncCallback&lt;void&gt; | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)��������������û�ʹ��״̬�ɹ�ʱ��errΪ<br/>undefined������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified abilityInfo is not found. |

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
  bundleManager.queryAbilityInfo(want, abilityFlags, userId).then((abilitiesInfo) => {
    hilog.info(0x0000, 'testTag', 'queryAbilityInfo successfully. Data: %{public}s', JSON.stringify(abilitiesInfo));
    let info = abilitiesInfo[0];

    bundleManager.setAbilityEnabled(info, false, err => {
      if (err) {
        hilog.error(0x0000, 'testTag', 'setAbilityEnabled failed: %{public}s', err.message);
      } else {
        hilog.info(0x0000, "testTag", "setAbilityEnabled successfully.");
      }
    });
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed. Cause: %{public}s', message);
}

```


## setAbilityEnabled

```TypeScript
function setAbilityEnabled(info: AbilityInfo, isEnabled: boolean): Promise<void>
```

����ָ������Ľ��û�ʹ��״̬��ʹ��Promise�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | AbilityInfo | 是 | ��Ҫ�����õ������ |
| isEnabled | boolean | 是 | ֵΪtrue��ʾʹ�ܣ�ֵΪfalse��ʾ���á� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified abilityInfo is not found. |

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
  bundleManager.queryAbilityInfo(want, abilityFlags, userId).then((abilitiesInfo) => {
    hilog.info(0x0000, 'testTag', 'queryAbilityInfo successfully. Data: %{public}s', JSON.stringify(abilitiesInfo));
    let info = abilitiesInfo[0];

    bundleManager.setAbilityEnabled(info, false).then(() => {
      hilog.info(0x0000, "testTag", "setAbilityEnabled successfully.");
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', 'setAbilityEnabled failed: %{public}s', err.message);
    });
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed. Cause: %{public}s', message);
}

```

