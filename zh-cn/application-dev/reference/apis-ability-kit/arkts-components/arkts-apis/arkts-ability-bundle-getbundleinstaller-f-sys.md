# getBundleInstaller（系统接口）

## 导入模块

```TypeScript
import { bundle } from '@kit.AbilityKit';
```

## getBundleInstaller

```TypeScript
function getBundleInstaller(callback: AsyncCallback<BundleInstaller>): void
```

获取用于安装包的接口，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** null

**需要权限：** ohos.permission.INSTALL_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[BundleInstaller](arkts-ability-bundleinstaller-bundleinstaller-depr-i-sys.md)&gt; | 是 | 回调函数，返回安装接口对象。 |

**示例**

```TypeScript
import bundle from '@ohos.bundle';
import { BusinessError } from '@ohos.base';

bundle.getBundleInstaller().then((data) => {
  console.info('getBundleInstaller successfully.');
}).catch((error: BusinessError) => {
  console.error('getBundleInstaller failed.');
});
```

```TypeScript
import bundle from '@ohos.bundle';

bundle.getBundleInstaller((err, data) => {
  if (err.code == 0) {
    console.error('getBundleInstaller successfully.');
  } else {
    console.info('getBundleInstaller failed.');
  }
});
```


## getBundleInstaller

```TypeScript
function getBundleInstaller(): Promise<BundleInstaller>
```

获取用于安装包的接口，使用Promise异步回调，返回安装接口对象。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** null

**需要权限：** ohos.permission.INSTALL_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[BundleInstaller](arkts-ability-bundleinstaller-bundleinstaller-depr-i-sys.md)&gt; | Promise对象，返回安装接口对象。 |

**示例**

参见 [getBundleInstaller](#getbundleinstaller)
