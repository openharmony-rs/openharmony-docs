# uninstallLocalPlugin

## 导入模块

```TypeScript
import { pluginBundleManager } from '@kit.AbilityKit';
```

## uninstallLocalPlugin

```TypeScript
function uninstallLocalPlugin(pluginBundleName: string): Promise<void>
```

卸载当前应用已通过自分发方式安装的指定插件。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.kernel.SUPPORT_LOCAL_PLUGIN

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-pluginBundleManager-function uninstallLocalPlugin(pluginBundleName: string): Promise<void>--><!--Device-pluginBundleManager-function uninstallLocalPlugin(pluginBundleName: string): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pluginBundleName | string | 是 | 插件的Bundle名称，表示要卸载的插件的应用包名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17700092](../errorcode-bundle.md#17700092-插件包名不存在) | Failed to uninstall the plugin because the specified plugin is not found. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Calling interface without permission 'ohos.permission.kernel.SUPPORT_LOCAL_PLUGIN'. |

