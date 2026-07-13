# @ohos.enterprise.bundleManager

本模块提供包管理能力，包括添加包安装允许名单、获取包安装允许名单、移除包安装允许名单等。

> **说明：**
>
> 本模块接口仅可在Stage模型下使用。
>
> 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../../mdm/mdm-kit-guide.md)。

**起始版本：** 10

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addAllowedInstallBundlesSync](arkts-mdm-addallowedinstallbundlessync-f.md#addallowedinstallbundlessync-1) | 添加应用至应用程序包安装允许名单，添加至允许名单的应用允许在当前/指定用户下安装，其它非允许名单应用不允许安装。系统应用卸载后重新安装不会受到接口限制；而普通应用在卸载后重新安装时，则会受到接口限制。 |
| [addDisallowedInstallBundlesSync](arkts-mdm-adddisallowedinstallbundlessync-f.md#adddisallowedinstallbundlessync-1) | 添加应用至应用程序包安装禁止名单，添加至禁止名单的应用不允许在当前/指定用户下安装。系统应用卸载后重新安装不会受到接口限制；而普通应用在卸载后重新安装时，则会受到接口限制。 |
| [addDisallowedUninstallBundlesSync](arkts-mdm-adddisalloweduninstallbundlessync-f.md#adddisalloweduninstallbundlessync-1) | 添加应用至包卸载禁止名单，添加至禁止名单的应用不允许在当前/指定用户下卸载。 |
| [addInstallationAllowedAppDistributionTypes](arkts-mdm-addinstallationallowedappdistributiontypes-f.md#addinstallationallowedappdistributiontypes-1) | 添加可安装应用的分发类型。添加成功后，当前设备可以安装对应分发类型的应用，但无法安装[AppDistributionType](arkts-mdm-appdistributiontype-e.md)中未添加的分发类型的应用。应用程序签名证书的分发类型详细介绍请参见[ApplicationInfo](../../apis-ability-kit/arkts-apis/arkts-ability-applicationinfo-i.md)的appDistributionType属性。 |
| [getAllowedInstallBundlesSync](arkts-mdm-getallowedinstallbundlessync-f.md#getallowedinstallbundlessync-1) | 获取当前/指定用户下的应用程序包安装允许名单。 |
| [getDisallowedInstallBundlesSync](arkts-mdm-getdisallowedinstallbundlessync-f.md#getdisallowedinstallbundlessync-1) | 获取当前/指定用户下的应用程序包安装禁止名单。 |
| [getDisallowedUninstallBundlesSync](arkts-mdm-getdisalloweduninstallbundlessync-f.md#getdisalloweduninstallbundlessync-1) | 获取当前/指定用户下包卸载禁止名单。 |
| [getInstallationAllowedAppDistributionTypes](arkts-mdm-getinstallationallowedappdistributiontypes-f.md#getinstallationallowedappdistributiontypes-1) | 获取可安装的应用程序签名证书的分发类型。 |
| [getInstalledBundleList](arkts-mdm-getinstalledbundlelist-f.md#getinstalledbundlelist-1) | 获取设备指定用户下已安装应用列表。使用Promise异步回调。 |
| [getInstalledBundleList](arkts-mdm-getinstalledbundlelist-f.md#getinstalledbundlelist-2) | 根据给定的bundleInfoGetFlag获取设备指定用户下已安装应用列表。使用Promise异步回调。 |
| [getInstalledBundleStorageStats](arkts-mdm-getinstalledbundlestoragestats-f.md#getinstalledbundlestoragestats-1) | 获取设备指定用户下已安装应用的存储占用信息。使用Promise异步回调。 |
| [install](arkts-mdm-install-f.md#install-3) | 安装指定路径下的应用包。使用Promise异步回调。&lt;/br&gt;此接口只能安装分发类型为enterprise_mdm（MDM应用）和enterprise_normal（普通企业应用）类型的应用，可以通过[getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-getbundleinfoforself-f.md#getbundleinfoforself-1)接口查询应用自身的[BundleInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundleinfo-i.md)，其中BundleInfo.appInfo.appDistributionType为应用的分发类型。 |
| [installForResult](arkts-mdm-installforresult-f.md#installforresult-1) | 安装应用 |
| [installMarketApps](arkts-mdm-installmarketapps-f.md#installmarketapps-1) | 下载并安装应用市场应用。@link&gt; **说明**&gt;本接口调用成功后会在桌面上生成应用下载任务，此任务与从应用市场下载所创建任务一致。下载安装结束后，安装结果会通过回调[EnterpriseAdminExtensionAbility.onMarketAppInstallResult](|
| [removeAllowedInstallBundlesSync](arkts-mdm-removeallowedinstallbundlessync-f.md#removeallowedinstallbundlessync-1) | 在应用程序包安装允许名单中移除应用，在允许名单存在的情况下，不在应用程序包安装允许名单中的应用不允许在当前/指定用户下安装。 |
| [removeDisallowedInstallBundlesSync](arkts-mdm-removedisallowedinstallbundlessync-f.md#removedisallowedinstallbundlessync-1) | 在应用程序包安装禁止名单中移除应用，在禁止名单存在的情况下，在应用程序包安装禁止名单中的应用不允许在当前/指定用户下安装。 |
| [removeDisallowedUninstallBundlesSync](arkts-mdm-removedisalloweduninstallbundlessync-f.md#removedisalloweduninstallbundlessync-1) | 在包卸载禁止名单中移除应用。在禁止名单存在的情况下，在包卸载禁止名单中的应用不允许在当前/指定用户下卸载。 |
| [removeInstallationAllowedAppDistributionTypes](arkts-mdm-removeinstallationallowedappdistributiontypes-f.md#removeinstallationallowedappdistributiontypes-1) | 移除应用的分发类型。若只移除了数组中部分的分发类型，则当前设备可以安装数组中剩下的分发类型的应用，但无法安装[AppDistributionType]{@link bundleManager.AppDistributionType)中未添加的分发类型的应用。应用程序签名证书的分发类型详细介绍请参见[ApplicationInfo](../../apis-ability-kit/arkts-apis/arkts-ability-applicationinfo-i.md)的appDistributionType属性。 |
| [uninstall](arkts-mdm-uninstall-f.md#uninstall-5) | 卸载当前/指定用户下的指定包接口，选择是否保留包数据（由isKeepData指定）。使用Promise异步回调。@link @ohos.enterprise.bundleManager:bundleManager.addDisallowedUninstallBundlesSync}&gt; 接口设置了不允许卸载时，调用此接口卸载应用会返回401错误码。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addAllowedInstallBundles](arkts-mdm-addallowedinstallbundles-f-sys.md#addallowedinstallbundles-1) | 添加应用至当前用户的应用程序包安装允许名单，添加至允许名单的应用允许在当前用户下安装，否则不允许安装，使用callback异步回调。 |
| [addAllowedInstallBundles](arkts-mdm-addallowedinstallbundles-f-sys.md#addallowedinstallbundles-2) | 添加应用至应用程序包安装允许名单，添加至允许名单的应用允许在指定用户（通过userId指定）下安装，否则不允许安装，使用callback异步回调。 |
| [addAllowedInstallBundles](arkts-mdm-addallowedinstallbundles-f-sys.md#addallowedinstallbundles-3) | 添加应用至应用程序包安装允许名单，添加至允许名单的应用允许在当前/指定用户下安装，否则不允许安装。使用Promise异步回调。 |
| [addDisallowedInstallBundles](arkts-mdm-adddisallowedinstallbundles-f-sys.md#adddisallowedinstallbundles-1) | 添加应用至应用程序包安装禁止名单，添加至禁止名单的应用不允许在当前用户下安装，使用callback异步回调。 |
| [addDisallowedInstallBundles](arkts-mdm-adddisallowedinstallbundles-f-sys.md#adddisallowedinstallbundles-2) | 添加应用至应用程序包安装禁止名单，添加至禁止名单的应用不允许在指定用户（通过userId指定）下安装。使用callback异步回调。 |
| [addDisallowedInstallBundles](arkts-mdm-adddisallowedinstallbundles-f-sys.md#adddisallowedinstallbundles-3) | 添加应用至应用程序包安装禁止名单，添加至禁止名单的应用不允许在当前/指定用户下安装。使用Promise异步回调。 |
| [addDisallowedUninstallBundles](arkts-mdm-adddisalloweduninstallbundles-f-sys.md#adddisalloweduninstallbundles-1) | 添加应用至应用程序包卸载禁止名单，添加至禁止名单的应用不允许在当前用户下卸载，使用callback异步回调。 |
| [addDisallowedUninstallBundles](arkts-mdm-adddisalloweduninstallbundles-f-sys.md#adddisalloweduninstallbundles-2) | 添加应用至应用程序包卸载禁止名单，添加至禁止名单的应用不允许在指定用户（通过userId指定）下卸载。使用callback异步回调。 |
| [addDisallowedUninstallBundles](arkts-mdm-adddisalloweduninstallbundles-f-sys.md#adddisalloweduninstallbundles-3) | 添加应用至应用程序包卸载禁止名单，添加至禁止名单的应用不允许在当前/指定用户下卸载。使用Promise异步回调。 |
| [getAllowedInstallBundles](arkts-mdm-getallowedinstallbundles-f-sys.md#getallowedinstallbundles-1) | 获取当前用户下的应用程序包安装允许名单，使用callback异步回调。 |
| [getAllowedInstallBundles](arkts-mdm-getallowedinstallbundles-f-sys.md#getallowedinstallbundles-2) | 获取指定用户（通过userId指定）下的应用程序包安装允许名单，使用callback异步回调。 |
| [getAllowedInstallBundles](arkts-mdm-getallowedinstallbundles-f-sys.md#getallowedinstallbundles-3) | 获取当前/指定用户下的应用程序包安装允许名单，使用Promise异步回调。 |
| [getDisallowedInstallBundles](arkts-mdm-getdisallowedinstallbundles-f-sys.md#getdisallowedinstallbundles-1) | 获取当前用户下的应用程序包安装禁止名单，使用callback异步回调。 |
| [getDisallowedInstallBundles](arkts-mdm-getdisallowedinstallbundles-f-sys.md#getdisallowedinstallbundles-2) | 获取指定用户（通过userId指定）下的应用程序包安装禁止名单，使用callback异步回调。 |
| [getDisallowedInstallBundles](arkts-mdm-getdisallowedinstallbundles-f-sys.md#getdisallowedinstallbundles-3) | 获取当前/指定用户下的应用程序包安装禁止名单，使用Promise异步回调。 |
| [getDisallowedUninstallBundles](arkts-mdm-getdisalloweduninstallbundles-f-sys.md#getdisalloweduninstallbundles-1) | 获取当前用户下的应用程序包卸载禁止名单，使用callback异步回调。 |
| [getDisallowedUninstallBundles](arkts-mdm-getdisalloweduninstallbundles-f-sys.md#getdisalloweduninstallbundles-2) | 获取指定用户（通过userId指定）下的应用程序包卸载禁止名单，使用callback异步回调。 |
| [getDisallowedUninstallBundles](arkts-mdm-getdisalloweduninstallbundles-f-sys.md#getdisalloweduninstallbundles-3) | 获取当前/指定用户下应用程序包卸载禁止名单接口，使用Promise异步回调。 |
| [install](arkts-mdm-install-f-sys.md#install-1) | 安装指定路径下的应用包。使用callback异步回调。 |
| [install](arkts-mdm-install-f-sys.md#install-2) | 安装指定路径下的指定安装参数的应用包。使用callback异步回调。 |
| [removeAllowedInstallBundles](arkts-mdm-removeallowedinstallbundles-f-sys.md#removeallowedinstallbundles-1) | 移除当前用户的应用程序包安装允许名单中的指定应用。安装允许名单存在时，不在允许名单中的应用不允许在当前用户下安装，使用callback异步回调。 |
| [removeAllowedInstallBundles](arkts-mdm-removeallowedinstallbundles-f-sys.md#removeallowedinstallbundles-2) | 移除在应用程序包安装允许名单中的应用，在允许名单存在的情况下，不在允许名单中的应用不允许在指定用户（通过userId指定）下安装，使用callback异步回调。 |
| [removeAllowedInstallBundles](arkts-mdm-removeallowedinstallbundles-f-sys.md#removeallowedinstallbundles-3) | 移除在应用程序包安装允许名单中的应用，在允许名单存在的情况下，不在允许名单中的应用不允许在当前/指定用户下安装。使用Promise异步回调。 |
| [removeDisallowedInstallBundles](arkts-mdm-removedisallowedinstallbundles-f-sys.md#removedisallowedinstallbundles-1) | 移除在应用程序包安装禁止名单中的应用，在禁止名单存在的情况下，在禁止名单中的应用不允许在当前用户下安装。使用callback异步回调。 |
| [removeDisallowedInstallBundles](arkts-mdm-removedisallowedinstallbundles-f-sys.md#removedisallowedinstallbundles-2) | 移除在应用程序包安装禁止名单中的应用，在禁止名单存在的情况下，在禁止名单中的应用不允许在指定用户（通过userId指定）下安装，使用callback异步回调。 |
| [removeDisallowedInstallBundles](arkts-mdm-removedisallowedinstallbundles-f-sys.md#removedisallowedinstallbundles-3) | 移除在应用程序包安装禁止名单中的应用，在禁止名单存在的情况下，在禁止名单中的应用不允许在当前/指定用户下安装。使用Promise异步回调。 |
| [removeDisallowedUninstallBundles](arkts-mdm-removedisalloweduninstallbundles-f-sys.md#removedisalloweduninstallbundles-1) | 移除在应用程序包卸载禁止名单中的应用，在禁止名单存在的情况下，在禁止名单中的应用不允许在当前用户下卸载，使用callback异步回调。 |
| [removeDisallowedUninstallBundles](arkts-mdm-removedisalloweduninstallbundles-f-sys.md#removedisalloweduninstallbundles-2) | 移除在应用程序包卸载禁止名单中的应用，在禁止名单存在的情况下，在禁止名单中的应用不允许在指定用户（通过userId指定）下卸载。使用callback异步回调。 |
| [removeDisallowedUninstallBundles](arkts-mdm-removedisalloweduninstallbundles-f-sys.md#removedisalloweduninstallbundles-3) | 移除在应用程序包卸载禁止名单中的应用。在禁止名单存在的情况下，在禁止名单中的应用不允许在当前/指定用户下卸载。使用Promise异步回调。 |
| [uninstall](arkts-mdm-uninstall-f-sys.md#uninstall-1) | 卸载当前用户下的指定应用程序包，且不保留应用程序包数据。使用callback异步回调。@link @ohos.enterprise.bundleManager:bundleManager.addDisallowedUninstallBundlesSync}&gt; 接口设置了不允许卸载时，调用此接口卸载应用会返回401错误码。 |
| [uninstall](arkts-mdm-uninstall-f-sys.md#uninstall-2) | 卸载指定用户下（由参数userId指定）的指定应用程序包，且不保留应用程序包数据。使用callback异步回调。@link @ohos.enterprise.bundleManager:bundleManager.addDisallowedUninstallBundlesSync}&gt; 接口设置了不允许卸载时，调用此接口卸载应用会返回401错误码。 |
| [uninstall](arkts-mdm-uninstall-f-sys.md#uninstall-3) | 卸载当前用户下的指定应用程序包，选择是否保留应用程序包数据（由isKeepData指定）。使用callback异步回调。@link @ohos.enterprise.bundleManager:bundleManager.addDisallowedUninstallBundlesSync}&gt; 接口设置了不允许卸载时，调用此接口卸载应用会返回401错误码。 |
| [uninstall](arkts-mdm-uninstall-f-sys.md#uninstall-4) | 卸载指定用户下（由参数userId指定）的指定应用程序包接口，选择是否保留应用程序包数据（由isKeepData指定）。使用callback异步回调。@link @ohos.enterprise.bundleManager:bundleManager.addDisallowedUninstallBundlesSync}&gt; 接口设置了不允许卸载时，调用此接口卸载应用会返回401错误码。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [ApplicationInfo](arkts-mdm-applicationinfo-i.md) | 应用程序信息。 |
| [BundleInfo](arkts-mdm-bundleinfo-i.md) | 描述应用包信息。 |
| [BundleStorageStats](arkts-mdm-bundlestoragestats-i.md) | 应用的存储占用信息。 |
| [InstallParam](arkts-mdm-installparam-i.md) | 应用包安装需指定的参数信息。 |
| [Resource](arkts-mdm-resource-i.md) | 资源相关信息，包括应用包名、应用模块名、资源id。 |
| [SignatureInfo](arkts-mdm-signatureinfo-i.md) | 描述应用包的签名信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AppDistributionType](arkts-mdm-appdistributiontype-e.md) | 应用程序签名证书的分发类型。详细介绍请参见[ApplicationInfo](../../apis-ability-kit/arkts-apis/arkts-ability-applicationinfo-i.md)的appDistributionType属性。 |
| [BundleInfoGetFlag](arkts-mdm-bundleinfogetflag-e.md) | 包信息获取标志，指示需要获取的包信息的内容。 |

