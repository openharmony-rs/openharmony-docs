# PluginParam（系统接口）

插件应用安装、卸载的参数信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-installer-export interface PluginParam--><!--Device-installer-export interface PluginParam-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## parameters

```TypeScript
parameters?: Array<Parameters>
```

指定安装、卸载插件程序的扩展参数，默认值为空。

**类型：** Array&lt;[Parameters](arkts-ability-installer-parameters-i-sys.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PluginParam-parameters?: Array<Parameters>--><!--Device-PluginParam-parameters?: Array<Parameters>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId?: int
```

指定安装、卸载插件程序所在的用户ID，可以通过 [getOsAccountLocalId接口](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId) 获取。默认值：调用方所在用户。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PluginParam-userId?: int--><!--Device-PluginParam-userId?: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

