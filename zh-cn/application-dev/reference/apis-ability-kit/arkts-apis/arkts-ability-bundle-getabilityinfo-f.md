# getAbilityInfo

## getAbilityInfo

```TypeScript
function getAbilityInfo(bundleName: string, abilityName: string, callback: AsyncCallback<AbilityInfo>): void
```

通过Bundle名称和组件名获取Ability组件信息，使用callback异步回调。 获取调用方自己的信息时不需要权限。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

<!--Device-bundle-function getAbilityInfo(bundleName: string, abilityName: string, callback: AsyncCallback<AbilityInfo>): void--><!--Device-bundle-function getAbilityInfo(bundleName: string, abilityName: string, callback: AsyncCallback<AbilityInfo>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用Bundle名称。 |
| abilityName | string | 是 | Ability名称。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AbilityInfo](arkts-ability-abilityinfo-abilityinfo-depr-i.md)&gt; | 是 | 程序启动作为入参的回调函数，返回Ability信息。 |

## 示例

```TypeScript
import bundle from '@ohos.bundle';

let bundleName: string = "com.example.myapplication";
let abilityName: string = "EntryAbility";

bundle.getAbilityInfo(bundleName, abilityName, (err, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. Data:' + JSON.stringify(data));
})
```


## getAbilityInfo

```TypeScript
function getAbilityInfo(bundleName: string, abilityName: string): Promise<AbilityInfo>
```

通过Bundle名称和组件名获取Ability组件信息，使用Promise形式异步回调。 获取调用方自己的信息时不需要权限。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

<!--Device-bundle-function getAbilityInfo(bundleName: string, abilityName: string): Promise<AbilityInfo>--><!--Device-bundle-function getAbilityInfo(bundleName: string, abilityName: string): Promise<AbilityInfo>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用Bundle名称。 |
| abilityName | string | 是 | Ability组件名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AbilityInfo](arkts-ability-abilityinfo-abilityinfo-depr-i.md)&gt; | Promise形式返回Ability信息。 |

## 示例

```TypeScript
import bundle from '@ohos.bundle';
import { BusinessError } from '@ohos.base';

let bundleName: string = "com.example.myapplication";
let abilityName: string = "EntryAbility";

bundle.getAbilityInfo(bundleName, abilityName)
  .then((data) => {
    console.info('Operation successful. Data: ' + JSON.stringify(data));
  }).catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  })
```

