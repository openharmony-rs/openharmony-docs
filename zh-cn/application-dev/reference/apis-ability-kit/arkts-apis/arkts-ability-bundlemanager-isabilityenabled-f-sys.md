# isAbilityEnabled（系统接口）

## isAbilityEnabled

```TypeScript
function isAbilityEnabled(info: AbilityInfo, appIndex: number): Promise<boolean>
```

��ȡӦ�û�ָ������Ӧ������Ľ��û�ʹ��״̬��ʹ��Promise�첽�ص���

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | AbilityInfo | 是 | ��ʾ���ڼ��ability����Ϣ�� |
| appIndex | number | 是 | ��ʾ����Ӧ�õ�������<br/>appIndexΪ0ʱ����ʾ��ȡ��Ӧ������Ľ��û�ʹ��״̬��appIndex����0ʱ����ʾ��ȡָ������Ӧ������Ľ��û�ʹ��״̬�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise���󣬷���true��ʾ��ǰӦ�����Ϊʹ��״̬������false��ʾ��ǰӦ�����Ϊ����״̬�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified abilityName is not found. |
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

    bundleManager.isAbilityEnabled(info, 1).then((data) => {
      hilog.info(0x0000, 'testTag', 'isAbilityEnabled successfully. Data: %{public}s', JSON.stringify(data));
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', 'isAbilityEnabled failed. Cause: %{public}s', err.message);
    });
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed. Cause: %{public}s', message);
}

```


## isAbilityEnabled

```TypeScript
function isAbilityEnabled(info: AbilityInfo, callback: AsyncCallback<boolean>): void
```

��ȡָ������Ľ��û�ʹ��״̬��ʹ��callback�첽�ص���

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | AbilityInfo | 是 | ��ʾ���ڼ��ability����Ϣ�� |
| callback | AsyncCallback&lt;boolean&gt; | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������true��ʾ��ǰӦ�����Ϊʹ��״̬������<br/>false��ʾӦ�����Ϊ����״̬�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified abilityName is not found. |

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

    bundleManager.isAbilityEnabled(info, (err, data) => {
      if (err) {
        hilog.error(0x0000, 'testTag', 'isAbilityEnabled failed: %{public}s', err.message);
      } else {
        hilog.info(0x0000, 'testTag', 'isAbilityEnabled successfully: %{public}s', JSON.stringify(data));
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


## isAbilityEnabled

```TypeScript
function isAbilityEnabled(info: AbilityInfo): Promise<boolean>
```

��ȡָ������Ľ��û�ʹ��״̬��ʹ��Promise�첽�ص���

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | AbilityInfo | 是 | ��ʾ���ڼ��ability����Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise���󣬷���true��ʾ��ǰӦ�����Ϊʹ��״̬������false��ʾ��ǰӦ�����Ϊ����״̬�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified abilityName is not found. |

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

    bundleManager.isAbilityEnabled(info).then((data) => {
      hilog.info(0x0000, 'testTag', 'isAbilityEnabled successfully. Data: %{public}s', JSON.stringify(data));
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', 'isAbilityEnabled failed. Cause: %{public}s', err.message);
    });
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed. Cause: %{public}s', message);
}

```

