# isApplicationEnabled

## 导入模块

```TypeScript
import { bundle } from '@kit.AbilityKit';
```

<a id="isapplicationenabled"></a>
## isApplicationEnabled

```TypeScript
function isApplicationEnabled(bundleName: string, callback: AsyncCallback<boolean>): void
```

根据给定的bundleName查询指定应用程序是否已经启用，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

<!--Device-bundle-function isApplicationEnabled(bundleName: string, callback: AsyncCallback<boolean>): void--><!--Device-bundle-function isApplicationEnabled(bundleName: string, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要查询的应用Bundle名称。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数，返回boolean代表是否启用。 |


<a id="isapplicationenabled-1"></a>
## isApplicationEnabled

```TypeScript
function isApplicationEnabled(bundleName: string): Promise<boolean>
```

根据给定的bundleName查询指定应用程序是否已经启用，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

<!--Device-bundle-function isApplicationEnabled(bundleName: string): Promise<boolean>--><!--Device-bundle-function isApplicationEnabled(bundleName: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要查询的应用Bundle名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise形式返回boolean代表是否启用。 |

