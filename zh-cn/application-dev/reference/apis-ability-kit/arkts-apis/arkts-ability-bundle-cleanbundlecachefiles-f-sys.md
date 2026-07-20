# cleanBundleCacheFiles（系统接口）

## 导入模块

```TypeScript
import { bundle } from '@kit.AbilityKit';
```

<a id="cleanbundlecachefiles"></a>
## cleanBundleCacheFiles

```TypeScript
function cleanBundleCacheFiles(bundleName: string, callback: AsyncCallback<void>): void
```

清除指定应用程序的缓存数据，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.REMOVE_CACHE_FILES

<!--Device-bundle-function cleanBundleCacheFiles(bundleName: string, callback: AsyncCallback<void>): void--><!--Device-bundle-function cleanBundleCacheFiles(bundleName: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 指示要清除其缓存数据的应用Bundle名称。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。 |


<a id="cleanbundlecachefiles-1"></a>
## cleanBundleCacheFiles

```TypeScript
function cleanBundleCacheFiles(bundleName: string): Promise<void>
```

清除指定应用程序的缓存数据，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.REMOVE_CACHE_FILES

<!--Device-bundle-function cleanBundleCacheFiles(bundleName: string): Promise<void>--><!--Device-bundle-function cleanBundleCacheFiles(bundleName: string): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 指示要清除其缓存数据的应用Bundle名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果的Promise对象。 |

