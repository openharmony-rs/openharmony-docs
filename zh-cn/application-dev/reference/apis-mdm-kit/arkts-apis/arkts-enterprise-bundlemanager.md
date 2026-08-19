# @ohos.enterprise.bundleManager

本模块提供包管理能力，包括安装和卸载应用包，管理包安装允许名单、包安装禁止名单、包卸载禁止名单、可安装应用的分发类型等。在企业设备管理场景中，通过这些能力可以实现应用安装卸载的精细化管控，防止未授权应用的安装和卸载，保障企业设备安全， 降低安全风险。 > **说明：** > > 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../mdm/mdm-kit-guide.md)。

**起始版本：** 10

<!--Device-unnamed-declare namespace bundleManager--><!--Device-unnamed-declare namespace bundleManager-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addAllowedInstallBundlesSync](arkts-mdm-bundlemanager-addallowedinstallbundlessync-f.md) | 添加应用至应用程序包安装允许名单，添加至允许名单的应用允许在当前/指定用户下安装，其它非允许名单应用不允许安装。系统应用卸载后重新安装不会受到接口限制；而普通应用在卸载后重新安装时，则会受到接口限制。 |
| [addDisallowedInstallBundlesSync](arkts-mdm-bundlemanager-adddisallowedinstallbundlessync-f.md) | 添加应用至应用程序包安装禁止名单，添加至禁止名单的应用不允许在当前/指定用户下安装。系统应用卸载后重新安装不会受到接口限制；而普通应用在卸载后重新安装时，则会受到接口限制。 |
| [addDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-adddisalloweduninstallbundlessync-f.md) | 添加应用至包卸载禁止名单，添加至禁止名单的应用不允许在当前/指定用户下卸载。 |
| [addInstallationAllowedAppDistributionTypes](arkts-mdm-bundlemanager-addinstallationallowedappdistributiontypes-f.md) | 添加可安装应用的分发类型。添加成功后，当前设备可以安装对应分发类型的应用，但无法安装[AppDistributionType](arkts-mdm-bundlemanager-appdistributiontype-e.md)中未添加的分发类型的应 用。 应用程序签名证书的分发类型详细介绍请参见[ApplicationInfo](../../apis-ability-kit/arkts-apis/arkts-ability-applicationinfo-i.md)的appDistributionType属性。 |
| [getAllowedInstallBundlesSync](arkts-mdm-bundlemanager-getallowedinstallbundlessync-f.md) | 获取当前/指定用户下的应用程序包安装允许名单。 |
| [getAllowedInstallBundlesSync](arkts-mdm-bundlemanager-getallowedinstallbundlessync-f.md) | 获取当前/指定用户下的应用程序包安装允许名单。 |
| [getDisallowedInstallBundlesSync](arkts-mdm-bundlemanager-getdisallowedinstallbundlessync-f.md) | 获取当前/指定用户下的应用程序包安装禁止名单。 |
| [getDisallowedInstallBundlesSync](arkts-mdm-bundlemanager-getdisallowedinstallbundlessync-f.md) | 获取当前/指定用户下的应用程序包安装禁止名单。 |
| [getDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-getdisalloweduninstallbundlessync-f.md) | 获取当前/指定用户下包卸载禁止名单。 |
| [getDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-getdisalloweduninstallbundlessync-f.md) | 获取当前/指定用户下包卸载禁止名单。 |
| [getInstallationAllowedAppDistributionTypes](arkts-mdm-bundlemanager-getinstallationallowedappdistributiontypes-f.md) | 获取可安装的应用程序签名证书的分发类型。 |
| [getInstallationAllowedAppDistributionTypes](arkts-mdm-bundlemanager-getinstallationallowedappdistributiontypes-f.md) | 获取可安装的应用程序签名证书的分发类型。 |
| [getInstalledBundleList](arkts-mdm-bundlemanager-getinstalledbundlelist-f.md) | 获取设备指定用户下已安装应用列表。使用Promise异步回调。 |
| [getInstalledBundleList](arkts-mdm-bundlemanager-getinstalledbundlelist-f.md) | 根据给定的bundleInfoGetFlag获取设备指定用户下已安装应用列表。使用Promise异步回调。 |
| [getInstalledBundleStorageStats](arkts-mdm-bundlemanager-getinstalledbundlestoragestats-f.md) | 获取设备指定用户下已安装应用的存储占用信息。使用Promise异步回调。 |
| [install](arkts-mdm-bundlemanager-install-f.md) | 安装指定路径下的应用包。使用Promise异步回调。 此接口只能安装分发类型为enterprise_mdm（MDM应用）和enterprise_normal（普通企业应用）类型的应用，可以通过 [getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfoforself-f.md)接口查询应用自身的 BundleInfo，其中BundleInfo.appInfo.appDistributionType为应用的分发类型。自API版本26.0.0起，建议使用 [installForResult](arkts-mdm-bundlemanager-installforresult-f.md)，以获取更详细的错误码返回值。 |
| [installForResult](arkts-mdm-bundlemanager-installforresult-f.md) | 安装指定路径下的应用包，并返回安装结果。使用Promise异步回调。 此接口只能安装分发类型为enterprise_mdm（MDM应用）和enterprise_normal（普通企业应用）类型的应用，可以通过 [getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfoforself-f.md)接口查询应用自身的 BundleInfo，其中BundleInfo.appInfo.appDistributionType为应用的分发类型。 |
| [installMarketApps](arkts-mdm-bundlemanager-installmarketapps-f.md) | 下载并安装应用市场应用。 |
| [removeAllowedInstallBundlesSync](arkts-mdm-bundlemanager-removeallowedinstallbundlessync-f.md) | 在应用程序包安装允许名单中移除应用，在允许名单存在的情况下，不在应用程序包安装允许名单中的应用不允许在当前/指定用户下安装。 |
| [removeDisallowedInstallBundlesSync](arkts-mdm-bundlemanager-removedisallowedinstallbundlessync-f.md) | 在应用程序包安装禁止名单中移除应用，在禁止名单存在的情况下，在应用程序包安装禁止名单中的应用不允许在当前/指定用户下安装。 |
| [removeDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-removedisalloweduninstallbundlessync-f.md) | 在包卸载禁止名单中移除应用。在禁止名单存在的情况下，在包卸载禁止名单中的应用不允许在当前/指定用户下卸载。 |
| [removeInstallationAllowedAppDistributionTypes](arkts-mdm-bundlemanager-removeinstallationallowedappdistributiontypes-f.md) | 移除应用的分发类型。若只移除了数组中部分的分发类型，则当前设备可以安装数组中剩下的分发类型的应用，但无法安装 [AppDistributionType](arkts-mdm-bundlemanager-appdistributiontype-e.md)中未添加的分发类型的应用。 应用程序签名证书的分发类型详细介绍请参见[ApplicationInfo](../../apis-ability-kit/arkts-apis/arkts-ability-applicationinfo-i.md)的appDistributionType属性。 |
| [uninstall](arkts-mdm-bundlemanager-uninstall-f.md) | 卸载当前/指定用户下的指定包，选择是否保留包数据（由isKeepData指定）。使用Promise异步回调。调用成功后，应用被卸载，数据根据isKeepData参数保留或删除。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addAllowedInstallBundles](arkts-mdm-bundlemanager-addallowedinstallbundles-f-sys.md) | 添加应用至当前用户的应用程序包安装允许名单，添加至允许名单的应用允许在当前用户下安装，否则不允许安装，使用callback异步回调。 |
| [addAllowedInstallBundles](arkts-mdm-bundlemanager-addallowedinstallbundles-f-sys.md) | 添加应用至应用程序包安装允许名单，添加至允许名单的应用允许在指定用户（通过userId指定）下安装，否则不允许安装，使用callback异步回调。 |
| [addAllowedInstallBundles](arkts-mdm-bundlemanager-addallowedinstallbundles-f-sys.md) | 添加应用至应用程序包安装允许名单，添加至允许名单的应用允许在当前/指定用户下安装，否则不允许安装。使用Promise异步回调。 |
| [addDisallowedInstallBundles](arkts-mdm-bundlemanager-adddisallowedinstallbundles-f-sys.md) | 添加应用至应用程序包安装禁止名单，添加至禁止名单的应用不允许在当前用户下安装，使用callback异步回调。 |
| [addDisallowedInstallBundles](arkts-mdm-bundlemanager-adddisallowedinstallbundles-f-sys.md) | 添加应用至应用程序包安装禁止名单，添加至禁止名单的应用不允许在指定用户（通过userId指定）下安装。使用callback异步回调。 |
| [addDisallowedInstallBundles](arkts-mdm-bundlemanager-adddisallowedinstallbundles-f-sys.md) | 添加应用至应用程序包安装禁止名单，添加至禁止名单的应用不允许在当前/指定用户下安装。使用Promise异步回调。 |
| [addDisallowedUninstallBundles](arkts-mdm-bundlemanager-adddisalloweduninstallbundles-f-sys.md) | 添加应用至应用程序包卸载禁止名单，添加至禁止名单的应用不允许在当前用户下卸载，使用callback异步回调。 |
| [addDisallowedUninstallBundles](arkts-mdm-bundlemanager-adddisalloweduninstallbundles-f-sys.md) | 添加应用至应用程序包卸载禁止名单，添加至禁止名单的应用不允许在指定用户（通过userId指定）下卸载。使用callback异步回调。 |
| [addDisallowedUninstallBundles](arkts-mdm-bundlemanager-adddisalloweduninstallbundles-f-sys.md) | 添加应用至应用程序包卸载禁止名单，添加至禁止名单的应用不允许在当前/指定用户下卸载。使用Promise异步回调。 |
| [getAllowedInstallBundles](arkts-mdm-bundlemanager-getallowedinstallbundles-f-sys.md) | 获取当前用户下的应用程序包安装允许名单，使用callback异步回调。 |
| [getAllowedInstallBundles](arkts-mdm-bundlemanager-getallowedinstallbundles-f-sys.md) | 获取指定用户（通过userId指定）下的应用程序包安装允许名单，使用callback异步回调。 |
| [getAllowedInstallBundles](arkts-mdm-bundlemanager-getallowedinstallbundles-f-sys.md) | 获取当前/指定用户下的应用程序包安装允许名单，使用Promise异步回调。 |
| [getDisallowedInstallBundles](arkts-mdm-bundlemanager-getdisallowedinstallbundles-f-sys.md) | 获取当前用户下的应用程序包安装禁止名单，使用callback异步回调。 |
| [getDisallowedInstallBundles](arkts-mdm-bundlemanager-getdisallowedinstallbundles-f-sys.md) | 获取指定用户（通过userId指定）下的应用程序包安装禁止名单，使用callback异步回调。 |
| [getDisallowedInstallBundles](arkts-mdm-bundlemanager-getdisallowedinstallbundles-f-sys.md) | 获取当前/指定用户下的应用程序包安装禁止名单，使用Promise异步回调。 |
| [getDisallowedUninstallBundles](arkts-mdm-bundlemanager-getdisalloweduninstallbundles-f-sys.md) | 获取当前用户下的应用程序包卸载禁止名单，使用callback异步回调。 |
| [getDisallowedUninstallBundles](arkts-mdm-bundlemanager-getdisalloweduninstallbundles-f-sys.md) | 获取指定用户（通过userId指定）下的应用程序包卸载禁止名单，使用callback异步回调。 |
| [getDisallowedUninstallBundles](arkts-mdm-bundlemanager-getdisalloweduninstallbundles-f-sys.md) | 获取当前/指定用户下应用程序包卸载禁止名单接口，使用Promise异步回调。 |
| [install](arkts-mdm-bundlemanager-install-f-sys.md) | 安装指定路径下的应用包。使用callback异步回调。 |
| [install](arkts-mdm-bundlemanager-install-f-sys.md) | 安装指定路径下的指定安装参数的应用包。使用callback异步回调。 |
| [removeAllowedInstallBundles](arkts-mdm-bundlemanager-removeallowedinstallbundles-f-sys.md) | 移除当前用户的应用程序包安装允许名单中的指定应用。安装允许名单存在时，不在允许名单中的应用不允许在当前用户下安装，使用callback异步回调。 |
| [removeAllowedInstallBundles](arkts-mdm-bundlemanager-removeallowedinstallbundles-f-sys.md) | 移除在应用程序包安装允许名单中的应用，在允许名单存在的情况下，不在允许名单中的应用不允许在指定用户（通过userId指定）下安装，使用callback异步回调。 |
| [removeAllowedInstallBundles](arkts-mdm-bundlemanager-removeallowedinstallbundles-f-sys.md) | 移除在应用程序包安装允许名单中的应用，在允许名单存在的情况下，不在允许名单中的应用不允许在当前/指定用户下安装。使用Promise异步回调。 |
| [removeDisallowedInstallBundles](arkts-mdm-bundlemanager-removedisallowedinstallbundles-f-sys.md) | 移除在应用程序包安装禁止名单中的应用，在禁止名单存在的情况下，在禁止名单中的应用不允许在当前用户下安装。使用callback异步回调。 |
| [removeDisallowedInstallBundles](arkts-mdm-bundlemanager-removedisallowedinstallbundles-f-sys.md) | 移除在应用程序包安装禁止名单中的应用，在禁止名单存在的情况下，在禁止名单中的应用不允许在指定用户（通过userId指定）下安装，使用callback异步回调。 |
| [removeDisallowedInstallBundles](arkts-mdm-bundlemanager-removedisallowedinstallbundles-f-sys.md) | 移除在应用程序包安装禁止名单中的应用，在禁止名单存在的情况下，在禁止名单中的应用不允许在当前/指定用户下安装。使用Promise异步回调。 |
| [removeDisallowedUninstallBundles](arkts-mdm-bundlemanager-removedisalloweduninstallbundles-f-sys.md) | 移除在应用程序包卸载禁止名单中的应用，在禁止名单存在的情况下，在禁止名单中的应用不允许在当前用户下卸载，使用callback异步回调。 |
| [removeDisallowedUninstallBundles](arkts-mdm-bundlemanager-removedisalloweduninstallbundles-f-sys.md) | 移除在应用程序包卸载禁止名单中的应用，在禁止名单存在的情况下，在禁止名单中的应用不允许在指定用户（通过userId指定）下卸载。使用callback异步回调。 |
| [removeDisallowedUninstallBundles](arkts-mdm-bundlemanager-removedisalloweduninstallbundles-f-sys.md) | 移除在应用程序包卸载禁止名单中的应用。在禁止名单存在的情况下，在禁止名单中的应用不允许在当前/指定用户下卸载。使用Promise异步回调。 |
| [uninstall](arkts-mdm-bundlemanager-uninstall-f-sys.md) | 卸载当前用户下的指定应用程序包，且不保留应用程序包数据。使用callback异步回调。 |
| [uninstall](arkts-mdm-bundlemanager-uninstall-f-sys.md) | 卸载指定用户下（由参数userId指定）的指定应用程序包，且不保留应用程序包数据。使用callback异步回调。 |
| [uninstall](arkts-mdm-bundlemanager-uninstall-f-sys.md) | 卸载当前用户下的指定应用程序包，选择是否保留应用程序包数据（由isKeepData指定）。使用callback异步回调。 |
| [uninstall](arkts-mdm-bundlemanager-uninstall-f-sys.md) | 卸载指定用户下（由参数userId指定）的指定应用程序包接口，选择是否保留应用程序包数据（由isKeepData指定）。使用callback异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [ApplicationInfo](arkts-mdm-bundlemanager-applicationinfo-i.md) | 应用程序信息。 |
| [BundleInfo](arkts-mdm-bundlemanager-bundleinfo-i.md) | 描述应用包信息。 |
| [BundleStorageStats](arkts-mdm-bundlemanager-bundlestoragestats-i.md) | 应用的存储占用信息。 |
| [InstallParam](arkts-mdm-bundlemanager-installparam-i.md) | 应用包安装需指定的参数信息。 |
| [Resource](arkts-mdm-bundlemanager-resource-i.md) | 资源相关信息，包括应用包名、应用模块名、资源id。 |
| [SignatureInfo](arkts-mdm-bundlemanager-signatureinfo-i.md) | 描述应用包的签名信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AppDistributionType](arkts-mdm-bundlemanager-appdistributiontype-e.md) | 应用程序签名证书的分发类型。详细介绍请参见[ApplicationInfo](../../apis-ability-kit/arkts-apis/arkts-ability-applicationinfo-i.md)的appDistributionType属 性。 |
| [BundleInfoGetFlag](arkts-mdm-bundlemanager-bundleinfogetflag-e.md) | 包信息获取标志，指示需要获取的包信息的内容。 |

