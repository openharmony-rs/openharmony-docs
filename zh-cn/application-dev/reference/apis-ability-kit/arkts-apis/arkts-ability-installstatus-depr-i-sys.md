# InstallStatus（系统接口）

应用程序安装卸载的结果。

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

## status

```TypeScript
status: bundle.InstallErrorCode
```

表示安装或卸载错误状态码。取值范围：枚举值[InstallErrorCode](arkts-ability-installerrorcode-e.md)。

**类型：** bundle.InstallErrorCode

**默认值：** Indicates the install or uninstall error code

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

## statusMessage

```TypeScript
statusMessage: string
```

表示安装或卸载的字符串结果信息。取值范围包括：

"SUCCESS" : 安装成功。</br> "STATUS_INSTALL_FAILURE": 安装失败（不存在安装文件）。</br> "STATUS_INSTALL_FAILURE_ABORTED": 安装中止。 </br>
"STATUS_INSTALL_FAILURE_INVALID": 安装参数无效。 </br> "STATUS_INSTALL_FAILURE_CONFLICT": 安装冲突（常见于升级和已有应用基本信息不一致）。 </br>
"STATUS_INSTALL_FAILURE_STORAGE": 存储包信息失败。 </br> "STATUS_INSTALL_FAILURE_INCOMPATIBLE": 安装不兼容（常见于版本降级安装或者签名信息错误）。 <
/br> "STATUS_UNINSTALL_FAILURE": 卸载失败（不存在卸载的应用）。 </br> "STATUS_UNINSTALL_FAILURE_ABORTED": 卸载中止（没有使用）。 </br> "
STATUS_UNINSTALL_FAILURE_ABORTED": 卸载冲突（卸载系统应用失败， 结束应用进程失败）。 </br> "STATUS_INSTALL_FAILURE_DOWNLOAD_TIMEOUT": 安装失败（
下载超时）。</br> "STATUS_INSTALL_FAILURE_DOWNLOAD_FAILED": 安装失败（下载失败）。 </br> "STATUS_RECOVER_FAILURE_INVALID": 恢复预置应用失败。
</br> "STATUS_ABILITY_NOT_FOUND": Ability未找到。</br> "STATUS_BMS_SERVICE_ERROR": BMS服务错误。 </br> "
STATUS_FAILED_NO_SPACE_LEFT": 设备空间不足。</br> "STATUS_GRANT_REQUEST_PERMISSIONS_FAILED": 应用授权失败。 </br> "
STATUS_INSTALL_PERMISSION_DENIED": 缺少安装权限。 </br> "STATUS_UNINSTALL_PERMISSION_DENIED": 缺少卸载权限。

**类型：** string

**默认值：** Indicates the install or uninstall result string message

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

