# getAbilityLabel

## 导入模块

```TypeScript
import { bundle } from '@kit.AbilityKit';
```

## getAbilityLabel

```TypeScript
function getAbilityLabel(bundleName: string, abilityName: string, callback: AsyncCallback<string>): void
```

通过Bundle名称和Ability组件名获取应用名称，使用callback异步回调。

获取调用方自己的信息时不需要权限。

**起始版本：** 8

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

<!--Device-bundle-function getAbilityLabel(bundleName: string, abilityName: string, callback: AsyncCallback<string>): void--><!--Device-bundle-function getAbilityLabel(bundleName: string, abilityName: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用Bundle名称。 |
| abilityName | string | 是 | Ability名称。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 程序启动作为入参的回调函数，返回应用名称信息。 |


## getAbilityLabel

```TypeScript
function getAbilityLabel(bundleName: string, abilityName: string): Promise<string>
```

通过Bundle名称和ability名称获取应用名称，使用Promise异步回调。

获取调用方自己的信息时不需要权限。

**起始版本：** 8

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

<!--Device-bundle-function getAbilityLabel(bundleName: string, abilityName: string): Promise<string>--><!--Device-bundle-function getAbilityLabel(bundleName: string, abilityName: string): Promise<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用Bundle名称。 |
| abilityName | string | 是 | Ability名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise形式返回应用名称信息。 |

