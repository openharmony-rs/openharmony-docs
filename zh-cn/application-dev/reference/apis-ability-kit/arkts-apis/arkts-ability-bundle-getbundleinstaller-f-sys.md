# getBundleInstaller（系统接口）

## 导入模块

```TypeScript
import { bundle } from '@kit.AbilityKit';
```

<a id="getbundleinstaller"></a>
## getBundleInstaller

```TypeScript
function getBundleInstaller(callback: AsyncCallback<BundleInstaller>): void
```

获取用于安装包的接口，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.INSTALL_BUNDLE

<!--Device-bundle-function getBundleInstaller(callback: AsyncCallback<BundleInstaller>): void--><!--Device-bundle-function getBundleInstaller(callback: AsyncCallback<BundleInstaller>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;BundleInstaller&gt; | 是 | 回调函数，返回安装接口对象。 |


<a id="getbundleinstaller-1"></a>
## getBundleInstaller

```TypeScript
function getBundleInstaller(): Promise<BundleInstaller>
```

获取用于安装包的接口，使用Promise异步回调，返回安装接口对象。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.INSTALL_BUNDLE

<!--Device-bundle-function getBundleInstaller(): Promise<BundleInstaller>--><!--Device-bundle-function getBundleInstaller(): Promise<BundleInstaller>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;BundleInstaller&gt; | Promise对象，返回安装接口对象。 |

