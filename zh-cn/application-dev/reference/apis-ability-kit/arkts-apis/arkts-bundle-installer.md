# @ohos.bundle.installer

在设备上安装、升级和卸载应用。

> **说明：**
>
> 本模块为系统接口。

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getBundleInstaller](arkts-ability-getbundleinstaller-f-sys.md#getbundleinstaller-1) | 获取BundleInstaller对象。使用callback异步回调。 |
| [getBundleInstaller](arkts-ability-getbundleinstaller-f-sys.md#getbundleinstaller-2) | 获取BundleInstaller对象。使用Promise异步回调。 |
| [getBundleInstallerSync](arkts-ability-getbundleinstallersync-f-sys.md#getbundleinstallersync-1) | 获取并返回BundleInstaller对象。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BundleInstaller](arkts-ability-bundleinstaller-i-sys.md) | Bundle installer interface, include install uninstall recover. |
| [CreateAppCloneParam](arkts-ability-createappcloneparam-i-sys.md) | 创建分身应用可指定的参数信息。 |
| [DestroyAppCloneParam](arkts-ability-destroyappcloneparam-i-sys.md) | 删除分身应用可指定的参数信息。 |
| [HashParam](arkts-ability-hashparam-i-sys.md) | 应用程序安装卸载哈希参数信息。 |
| [InstallParam](arkts-ability-installparam-i-sys.md) | 应用程序安装、卸载或恢复需指定的参数信息。 |
| [PGOParam](arkts-ability-pgoparam-i-sys.md) | PGO（Profile-guided Optimization）配置文件参数信息。 |
| [Parameters](arkts-ability-parameters-i-sys.md) | 扩展参数信息。 |
| [PluginParam](arkts-ability-pluginparam-i-sys.md) | 插件应用安装、卸载的参数信息。 |
| [UninstallParam](arkts-ability-uninstallparam-i-sys.md) | 共享包卸载需指定的参数信息。 |
| [VerifyCodeParam](arkts-ability-verifycodeparam-i-sys.md) | 应用程序代码签名文件信息。 |
<!--DelEnd-->

