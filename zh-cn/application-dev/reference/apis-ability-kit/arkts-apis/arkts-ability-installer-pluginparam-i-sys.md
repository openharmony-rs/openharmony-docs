# PluginParam（系统接口）

插件应用安装、卸载的参数信息。

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-installer-export interface PluginParam--><!--Device-installer-export interface PluginParam-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## parameters

```TypeScript
parameters?: Array<Parameters>
```

指定安装、卸载插件程序的扩展参数，默认值为空。

**类型：** Array&lt;Parameters&gt;

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-PluginParam-parameters?: Array<Parameters>--><!--Device-PluginParam-parameters?: Array<Parameters>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId?: int
```

指定安装、卸载插件程序所在的用户ID，可以通过 [getOsAccountLocalId接口]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 获取。默认值：调用方所在用户。

**类型：** int

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-PluginParam-userId?: int--><!--Device-PluginParam-userId?: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

