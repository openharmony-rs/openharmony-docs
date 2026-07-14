# BundleInstaller（系统接口）

本模块提供设备上安装、升级和卸载应用的能力。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [BundleInstaller](arkts-ability-bundleinstaller-i-sys.md)

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

## install

```TypeScript
install(bundleFilePaths: Array<string>, param: InstallParam, callback: AsyncCallback<InstallStatus>): void
```

在应用中安装hap，支持多hap安装。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [install](arkts-ability-bundleinstaller-i-sys.md#install-1)

**需要权限：** ohos.permission.INSTALL_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFilePaths | Array&lt;string&gt; | 是 | 指示存储HAP的沙箱路径。 |
| param | InstallParam | 是 | 指定安装所需的其他参数。 |
| callback | AsyncCallback&lt;InstallStatus&gt; | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md)，程序启动作为入参的回调函数，返回安装状态信息。 |

## recover

```TypeScript
recover(bundleName: string, param: InstallParam, callback: AsyncCallback<InstallStatus>): void
```

恢复一个应用程序，使用callback异步回调。当预置应用被卸载后，可以通过此接口进行恢复。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [recover](arkts-ability-bundleinstaller-i-sys.md#recover-1)

**需要权限：** ohos.permission.INSTALL_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用Bundle名称。 |
| param | InstallParam | 是 | 指定应用恢复所需的其他参数。 |
| callback | AsyncCallback&lt;InstallStatus&gt; | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md)，程序启动作为入参的回调函数，返回安装状态信息。 |

## uninstall

```TypeScript
uninstall(bundleName: string, param: InstallParam, callback: AsyncCallback<InstallStatus>): void
```

卸载应用程序，使用callback异步回调，返回安装状态信息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [uninstall](arkts-ability-bundleinstaller-i-sys.md#uninstall-1)

**需要权限：** ohos.permission.INSTALL_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用Bundle名称。 |
| param | InstallParam | 是 | 指定卸载所需的其他参数。 |
| callback | AsyncCallback&lt;InstallStatus&gt; | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md)，程序启动作为入参的回调函数，返回安装状态信息。 |

