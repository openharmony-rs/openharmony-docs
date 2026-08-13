# getAbilityIcon

## getAbilityIcon

```TypeScript
function getAbilityIcon(bundleName: string, abilityName: string, callback: AsyncCallback<image.PixelMap>): void
```

通过bundleName和abilityName获取对应Icon的[PixelMap](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md#@ohos.multimedia.image)，使用callback异步回调。 获取调用方自己的信息时不需要权限。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** null

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

<!--Device-bundle-function getAbilityIcon(bundleName: string, abilityName: string, callback: AsyncCallback<image.PixelMap>): void--><!--Device-bundle-function getAbilityIcon(bundleName: string, abilityName: string, callback: AsyncCallback<image.PixelMap>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要查询的应用Bundle名称。 |
| abilityName | string | 是 | 要查询的Ability组件名。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;image.PixelMap&gt; | 是 | 程序启动作为入参的回调函数，返回指定 [PixelMap](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md#@ohos.multimedia.image)。 |

## 示例

```TypeScript
import bundle from '@ohos.bundle';

let bundleName: string = "com.example.myapplication";
let abilityName: string = "EntryAbility";

bundle.getAbilityIcon(bundleName, abilityName, (err, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. Data:' + JSON.stringify(data));
})
```


## getAbilityIcon

```TypeScript
function getAbilityIcon(bundleName: string, abilityName: string): Promise<image.PixelMap>
```

通过bundleName和abilityName获取对应Icon的[PixelMap](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md#@ohos.multimedia.image)，使用Promise异步回调。 获取调用方自己的信息时不需要权限。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** null

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

<!--Device-bundle-function getAbilityIcon(bundleName: string, abilityName: string): Promise<image.PixelMap>--><!--Device-bundle-function getAbilityIcon(bundleName: string, abilityName: string): Promise<image.PixelMap>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要查询的应用Bundle名称。 |
| abilityName | string | 是 | 要查询的Ability组件名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | Returns the PixelMap object representing the icon of the specified ability. |

## 示例

```TypeScript
import bundle from '@ohos.bundle';
import { BusinessError } from '@ohos.base';

let bundleName: string = "com.example.myapplication";
let abilityName: string = "EntryAbility";

bundle.getAbilityIcon(bundleName, abilityName)
  .then((data) => {
    console.info('Operation successful. Data: ' + JSON.stringify(data));
  }).catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  })
```

