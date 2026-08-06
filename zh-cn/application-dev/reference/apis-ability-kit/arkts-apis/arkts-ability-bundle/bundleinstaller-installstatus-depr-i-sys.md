# InstallStatus（系统接口）

应用程序安装卸载的结果。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

<!--Device-unnamed-export interface InstallStatus--><!--Device-unnamed-export interface InstallStatus-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

## status

```TypeScript
status: bundle.InstallErrorCode
```

表示安装或卸载错误状态码。取值范围：枚举值[InstallErrorCode]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**类型：** bundle.InstallErrorCode

**默认值：** Indicates the install or uninstall error code

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

<!--Device-InstallStatus-status: bundle.InstallErrorCode--><!--Device-InstallStatus-status: bundle.InstallErrorCode-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

## statusMessage

```TypeScript
statusMessage: string
```

表示安装或卸载的字符串结果信息。取值范围包括： "SUCCESS" : 安装成功。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_ "STATUS\_INSTALL\_FAILURE": 安装失败（不存在安装文件）。\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_ "STATUS\_INSTALL\_FAILURE\_ABORTED": 安装中止。 \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_ "STATUS\_INSTALL\_FAILURE\_INVALID": 安装参数无效。 \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_ "STATUS\_INSTALL\_FAILURE\_CONFLICT": 安装冲突（常见于升级和已有应用基本信息不一致）。 \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_ "STATUS\_INSTALL\_FAILURE\_STORAGE": 存储包信息失败。 \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_ "STATUS\_INSTALL\_FAILURE\_INCOMPATIBLE": 安装不兼容（常见于版本降级安装或者签名信息错误）。 &lt; /br&gt; "STATUS\_UNINSTALL\_FAILURE": 卸载失败（不存在卸载的应用）。 \_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_ "STATUS\_UNINSTALL\_FAILURE\_ABORTED": 卸载中止（没有使用）。 \_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_ " STATUS\_UNINSTALL\_FAILURE\_ABORTED": 卸载冲突（卸载系统应用失败， 结束应用进程失败）。 \_\_\_HTML\_TAG\_DESC\_USD\_8\_\_\_ "STATUS\_INSTALL\_FAILURE\_DOWNLOAD\_TIMEOUT": 安装失败（ 下载超时）。\_\_\_HTML\_TAG\_DESC\_USD\_9\_\_\_ "STATUS\_INSTALL\_FAILURE\_DOWNLOAD\_FAILED": 安装失败（下载失败）。 \_\_\_HTML\_TAG\_DESC\_USD\_10\_\_\_ "STATUS\_RECOVER\_FAILURE\_INVALID": 恢复预置应用失败。 \_\_\_HTML\_TAG\_DESC\_USD\_11\_\_\_ "STATUS\_ABILITY\_NOT\_FOUND": Ability未找到。\_\_\_HTML\_TAG\_DESC\_USD\_12\_\_\_ "STATUS\_BMS\_SERVICE\_ERROR": BMS服务错误。 \_\_\_HTML\_TAG\_DESC\_USD\_13\_\_\_ " STATUS\_FAILED\_NO\_SPACE\_LEFT": 设备空间不足。\_\_\_HTML\_TAG\_DESC\_USD\_14\_\_\_ "STATUS\_GRANT\_REQUEST\_PERMISSIONS\_FAILED": 应用授权失败。 \_\_\_HTML\_TAG\_DESC\_USD\_15\_\_\_ " STATUS\_INSTALL\_PERMISSION\_DENIED": 缺少安装权限。 \_\_\_HTML\_TAG\_DESC\_USD\_16\_\_\_ "STATUS\_UNINSTALL\_PERMISSION\_DENIED": 缺少卸载权限。

**类型：** string

**默认值：** Indicates the install or uninstall result string message

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

<!--Device-InstallStatus-statusMessage: string--><!--Device-InstallStatus-statusMessage: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

