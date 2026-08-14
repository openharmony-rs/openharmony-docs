# getAllLocalPluginInfoForSelf

## getAllLocalPluginInfoForSelf

```TypeScript
function getAllLocalPluginInfoForSelf(): Promise<Array<PluginBundleInfo>>
```

查询当前应用中所有自分发插件的信息。使用Promise异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**需要权限：** ohos.permission.kernel.SUPPORT_LOCAL_PLUGIN

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-pluginBundleManager-function getAllLocalPluginInfoForSelf(): Promise<Array<PluginBundleInfo>>--><!--Device-pluginBundleManager-function getAllLocalPluginInfoForSelf(): Promise<Array<PluginBundleInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;PluginBundleInfo&gt;&gt; | Promise对象，返回当前应用已安装的所有本地插件信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Calling interface without permission 'ohos.permission.kernel.SUPPORT_LOCAL_PLUGIN'. |

