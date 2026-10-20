# getBundleResourceArchiveInfo（系统接口）

## 导入模块

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
```

## getBundleResourceArchiveInfo

```TypeScript
function getBundleResourceArchiveInfo(filePath: string, resourceFlags?: number): Promise<BundleResourceInfo>
```

根据给定的filePath文件路径和resourceFlags资源标志获取资源信息。使用Promise异步回调。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.GET_BUNDLE_RESOURCES

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleResourceManager-function getBundleResourceArchiveInfo(filePath: string, resourceFlags?: int): Promise<BundleResourceInfo>--><!--Device-bundleResourceManager-function getBundleResourceArchiveInfo(filePath: string, resourceFlags?: int): Promise<BundleResourceInfo>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 表示存储文件的路径，路径应该是当前应用程序数据目录的路径。 |
| resourceFlags | number | 否 | 指定返回的BundleResourceInfo所包含的信息，取值参考[ResourceFlag](arkts-ability-bundleresourcemanager-resourceflag-e-sys.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[BundleResourceInfo](arkts-ability-bundleresourcemanager-bundleresourceinfo-t-sys.md)&gt; | Promise对象，返回BundleResourceInfo。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system api. |
| [17700022](../errorcode-bundle.md#17700022-输入的待解析源文件无效) | The filePath is invalid. |
| [17700101](../errorcode-bundle.md#17700101-包管理服务异常) | Bundle manager service is excepted. |
