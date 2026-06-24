# getAbilityInfo

## getAbilityInfo

```TypeScript
function getAbilityInfo(uri: string, abilityFlags: number): Promise<Array<AbilityInfo>>
```

��ȡָ����Դ��ʶ���������Ϣ��־��Ӧ��Ability��Ϣ��ʹ��Promise�첽�ص���

**起始版本：** 20

**需要权限：** ohos.permission.GET_ABILITY_INFO

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | ��ʾͳһ��Դ��ʶ��URI��ȡֵ��<br/>[module.json5�����ļ���skills�µ�uris�ֶ�](../../../../quick-start/module-configuration-file.md#skills��ǩ)���Ӧ�� |
| abilityFlags | number | 是 | ��ʾ[Ability�����Ϣ��־](arkts-ability-bundlemanager-abilityflag-e-sys.md#AbilityFlag)��ָʾ��Ҫ��ȡ��<br/>Ability�����Ϣ�����ݡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AbilityInfo&gt;&gt; | Promise���󣬷��ػ�ȡ����Ability��Ϣ���顣 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [17700003](../../errorcode-universal.md#17700003-The) | The ability is not found. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let abilityFlags = bundleManager.AbilityFlag.GET_ABILITY_INFO_WITH_APPLICATION;
let uri = "https://www.example.com";

try {
  bundleManager.getAbilityInfo(uri, abilityFlags).then((data) => {
    hilog.info(0x0000, 'testTag', 'getAbilityInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    let message = (err as BusinessError).message;
    hilog.error(0x0000, 'testTag', 'getAbilityInfo failed. Cause: %{public}s', message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAbilityInfo failed. Cause: %{public}s', message);
}

```

