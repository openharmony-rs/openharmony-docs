# getLaunchWantForBundle

## getLaunchWantForBundle

```TypeScript
function getLaunchWantForBundle(bundleName: string, callback: AsyncCallback<Want>): void
```

查询拉起指定应用的want对象，使用callback异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundle-function getLaunchWantForBundle(bundleName: string, callback: AsyncCallback<Want>): void--><!--Device-bundle-function getLaunchWantForBundle(bundleName: string, callback: AsyncCallback<Want>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要查询的应用Bundle名称。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[Want](arkts-ability-app-ability-want-want-c.md)&gt; | 是 | 程序启动作为入参的回调函数，返回拉起指定应用的want对象。 |

## 示例

```TypeScript
import bundle from '@ohos.bundle';

let bundleName: string = "com.example.myapplication";

bundle.getLaunchWantForBundle(bundleName, (err, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. Data:' + JSON.stringify(data));
})
```


## getLaunchWantForBundle

```TypeScript
function getLaunchWantForBundle(bundleName: string): Promise<Want>
```

查询拉起指定应用的want对象，使用Promise异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundle-function getLaunchWantForBundle(bundleName: string): Promise<Want>--><!--Device-bundle-function getLaunchWantForBundle(bundleName: string): Promise<Want>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要查询的应用Bundle名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Want](arkts-ability-app-ability-want-want-c.md)&gt; | Returns the Want for starting the application's main ability if any. |

## 示例

```TypeScript
import bundle from '@ohos.bundle';
import { BusinessError } from '@ohos.base';

let bundleName: string = "com.example.myapplication";

bundle.getLaunchWantForBundle(bundleName)
  .then((data) => {
    console.info('Operation successful. Data: ' + JSON.stringify(data));
  }).catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  })
```

