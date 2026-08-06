# installLocalPlugin

## installLocalPlugin

```TypeScript
function installLocalPlugin(pluginFilePaths: Array<string>): Promise<void>
```

为当前应用安装自分发插件（即应用通过自有渠道分发、自主管理的插件）。使用Promise异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**需要权限：** ohos.permission.kernel.SUPPORT_LOCAL_PLUGIN

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-pluginBundleManager-function installLocalPlugin(pluginFilePaths: Array<string>): Promise<void>--><!--Device-pluginBundleManager-function installLocalPlugin(pluginFilePaths: Array<string>): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pluginFilePaths | Array&lt;string&gt; | 是 | 插件文件路径数组，表示要安装的插件文件的路径列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Calling interface without permission 'ohos.permission.kernel.SUPPORT\_\_\_ESCAPED\_UNDERSCORE\_\_\_LOCAL\_\_\_ESCAPED\_UNDERSCORE\_\_\_PLUGIN'. |
| [17700010](../errorcode-bundle.md#17700010-文件解析失败导致应用安装失败) | Failed to install the plugin because the plugin fails to be parsed. |
| [17700011](../errorcode-bundle.md#17700011-签名校验失败导致应用安装失败) | Failed to install the plugin because the plugin signature fails to be verified. |
| [17700012](../errorcode-bundle.md#17700012-安装包路径无效或者文件过大导致应用安装失败) | Failed to install the plugin because the HSP path is invalid or the HSP is too large. |
| [17700015](../errorcode-bundle.md#17700015-多个hap配置信息不同导致应用安装失败) | Failed to install the plugin because they have different configuration information. |
| [17700016](../errorcode-bundle.md#17700016-系统磁盘空间不足导致应用安装失败) | Failed to install the plugin because of insufficient system disk space. |
| [17700017](../errorcode-bundle.md#17700017-新安装的应用版本号低于已安装的版本号导致应用安装失败) | Failed to install the plugin since the version of the plugin to install is too early. |
| [17700048](../errorcode-bundle.md#17700048-代码签名校验失败) | Failed to install the plugin because the code signature verification failed. |
| [17700052](../errorcode-bundle.md#17700052-非开发者模式下不允许安装调试应用) | Failed to install the plugin because debug bundle cannot be installed under non-developer mode. |
| [17700073](../errorcode-bundle.md#17700073-由于设备上存在具有相同包名称但不同签名信息的应用程序导致安装失败) | Failed to install the plugin because a plugin with the same\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_bundle name but different signature information exists on the device. |
| [17700087](../errorcode-bundle.md#17700087-当前设备不支持安装插件) | Failed to install the plugin because the current device does not support plugins. |
| [17700091](../errorcode-bundle.md#17700091-插件与主体同包名) | Failed to install the plugin because the plugin name is the same as the host bundle name. |

