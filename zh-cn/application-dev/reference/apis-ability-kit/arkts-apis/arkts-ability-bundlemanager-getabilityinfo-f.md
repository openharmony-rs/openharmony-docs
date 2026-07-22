# getAbilityInfo

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAbilityInfo

```TypeScript
function getAbilityInfo(uri: string, abilityFlags: number): Promise<Array<AbilityInfo>>
```

获取指定资源标识符和组件信息标志对应的Ability信息。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.GET_ABILITY_INFO

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-bundleManager-function getAbilityInfo(uri: string, abilityFlags: int): Promise<Array<AbilityInfo>>--><!--Device-bundleManager-function getAbilityInfo(uri: string, abilityFlags: int): Promise<Array<AbilityInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示统一资源标识符URI，取值与[module.json5配置文件中skills下的uris字段](../../../quick-start/module-configuration-file.md#skills标签)相对应。 |
| abilityFlags | number | 是 | 表示[Ability组件信息标志](arkts-ability-bundlemanager-abilityflag-e-sys.md)，指示需要获取的Ability组件信息的内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AbilityInfo&gt;&gt; | Promise对象，返回获取到的Ability信息数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [17700003](../errorcode-bundle.md#17700003-指定的abilityname不存在) | The ability is not found. |

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

