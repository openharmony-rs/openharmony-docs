# @ohos.enterprise.bundleManager

本模块提供包管理能力，包括添加包安装允许名单、获取包安装允许名单、移除包安装允许名单等。

> **说明：**  
>  
> 本模块接口仅可在Stage模型下使用。  
>  
> 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](docroot://mdm/mdm-kit-guide.md)。

**起始版本：** 10

<!--Device-unnamed-declare namespace bundleManager--><!--Device-unnamed-declare namespace bundleManager-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addAllowedInstallBundlesSync](arkts-mdm-bundlemanager-addallowedinstallbundlessync-f.md#addallowedinstallbundlessync) | 添加应用至应用程序包安装允许名单，添加至允许名单的应用允许在当前/指定用户下安装，其它非允许名单应用不允许安装。系统应用卸载后重新安装不会受到接口限制；而普通应用在卸载后重新安装时，则会受到接口限制。 |
| [addDisallowedInstallBundlesSync](arkts-mdm-bundlemanager-adddisallowedinstallbundlessync-f.md#adddisallowedinstallbundlessync) | 添加应用至应用程序包安装禁止名单，添加至禁止名单的应用不允许在当前/指定用户下安装。系统应用卸载后重新安装不会受到接口限制；而普通应用在卸载后重新安装时，则会受到接口限制。 |
| [addDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-adddisalloweduninstallbundlessync-f.md#adddisalloweduninstallbundlessync) | 添加应用至包卸载禁止名单，添加至禁止名单的应用不允许在当前/指定用户下卸载。 |
| [addInstallationAllowedAppDistributionTypes](arkts-mdm-bundlemanager-addinstallationallowedappdistributiontypes-f.md#addinstallationallowedappdistributiontypes) | 添加可安装应用的分发类型。添加成功后，当前设备可以安装对应分发类型的应用，但无法安装[AppDistributionType](arkts-mdm-bundlemanager-appdistributiontype-e.md)中未添加的分发类型的应用。  应用程序签名证书的分发类型详细介绍请参见[ApplicationInfo](../../apis-ability-kit/arkts-apis/arkts-ability-applicationinfo-i.md)的appDistributionType属性。 |
| [getAllowedInstallBundlesSync](arkts-mdm-bundlemanager-getallowedinstallbundlessync-f.md#getallowedinstallbundlessync) | 获取当前/指定用户下的应用程序包安装允许名单。 |
| [getDisallowedInstallBundlesSync](arkts-mdm-bundlemanager-getdisallowedinstallbundlessync-f.md#getdisallowedinstallbundlessync) | 获取当前/指定用户下的应用程序包安装禁止名单。 |
| [getDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-getdisalloweduninstallbundlessync-f.md#getdisalloweduninstallbundlessync) | 获取当前/指定用户下包卸载禁止名单。 |
| [getInstallationAllowedAppDistributionTypes](arkts-mdm-bundlemanager-getinstallationallowedappdistributiontypes-f.md#getinstallationallowedappdistributiontypes) | 获取可安装的应用程序签名证书的分发类型。 |
| [getInstalledBundleList](arkts-mdm-bundlemanager-getinstalledbundlelist-f.md#getinstalledbundlelist) | 获取设备指定用户下已安装应用列表。使用Promise异步回调。 |
| [getInstalledBundleList](arkts-mdm-bundlemanager-getinstalledbundlelist-f.md#getinstalledbundlelist-1) | 根据给定的bundleInfoGetFlag获取设备指定用户下已安装应用列表。使用Promise异步回调。 |
| [getInstalledBundleStorageStats](arkts-mdm-bundlemanager-getinstalledbundlestoragestats-f.md#getinstalledbundlestoragestats) | 获取设备指定用户下已安装应用的存储占用信息。使用Promise异步回调。 |
| [install](arkts-mdm-bundlemanager-install-f.md#install-2) | 安装指定路径下的应用包。使用Promise异步回调。</br>此接口只能安装分发类型为enterprise_mdm（MDM应用）和enterprise_normal（普通企业应用）类型的应用，可以通过[getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfoforself-f.md#getbundleinfoforself-1)接口查询应用自身的[BundleInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundleinfo-i.md)，其中BundleInfo.appInfo.appDistributionType为应用的分发类型。 |
| [installForResult](arkts-mdm-bundlemanager-installforresult-f.md#installforresult) | 安装应用 |
| [installMarketApps](arkts-mdm-bundlemanager-installmarketapps-f.md#installmarketapps) | 下载并安装应用市场应用。 |
| [removeAllowedInstallBundlesSync](arkts-mdm-bundlemanager-removeallowedinstallbundlessync-f.md#removeallowedinstallbundlessync) | 在应用程序包安装允许名单中移除应用，在允许名单存在的情况下，不在应用程序包安装允许名单中的应用不允许在当前/指定用户下安装。 |
| [removeDisallowedInstallBundlesSync](arkts-mdm-bundlemanager-removedisallowedinstallbundlessync-f.md#removedisallowedinstallbundlessync) | 在应用程序包安装禁止名单中移除应用，在禁止名单存在的情况下，在应用程序包安装禁止名单中的应用不允许在当前/指定用户下安装。 |
| [removeDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-removedisalloweduninstallbundlessync-f.md#removedisalloweduninstallbundlessync) | 在包卸载禁止名单中移除应用。在禁止名单存在的情况下，在包卸载禁止名单中的应用不允许在当前/指定用户下卸载。 |
| [removeInstallationAllowedAppDistributionTypes](arkts-mdm-bundlemanager-removeinstallationallowedappdistributiontypes-f.md#removeinstallationallowedappdistributiontypes) | 移除应用的分发类型。若只移除了数组中部分的分发类型，则当前设备可以安装数组中剩下的分发类型的应用，但无法安装[AppDistributionType](arkts-mdm-bundlemanager-appdistributiontype-e.md)中未添加的分发类型的应用。  应用程序签名证书的分发类型详细介绍请参见[ApplicationInfo](../../apis-ability-kit/arkts-apis/arkts-ability-applicationinfo-i.md)的appDistributionType属性。 |
| [uninstall](arkts-mdm-bundlemanager-uninstall-f.md#uninstall-4) | 卸载当前/指定用户下的指定包接口，选择是否保留包数据（由isKeepData指定）。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addAllowedInstallBundles](arkts-mdm-bundlemanager-addallowedinstallbundles-f-sys.md#addallowedinstallbundles) | 添加应用至当前用户的应用程序包安装允许名单，添加至允许名单的应用允许在当前用户下安装，否则不允许安装，使用callback异步回调。 |
| [addAllowedInstallBundles](arkts-mdm-bundlemanager-addallowedinstallbundles-f-sys.md#addallowedinstallbundles-1) | 添加应用至应用程序包安装允许名单，添加至允许名单的应用允许在指定用户（通过userId指定）下安装，否则不允许安装，使用callback异步回调。 |
| [addAllowedInstallBundles](arkts-mdm-bundlemanager-addallowedinstallbundles-f-sys.md#addallowedinstallbundles-2) | 添加应用至应用程序包安装允许名单，添加至允许名单的应用允许在当前/指定用户下安装，否则不允许安装。使用Promise异步回调。 |
| [addDisallowedInstallBundles](arkts-mdm-bundlemanager-adddisallowedinstallbundles-f-sys.md#adddisallowedinstallbundles) | 添加应用至应用程序包安装禁止名单，添加至禁止名单的应用不允许在当前用户下安装，使用callback异步回调。 |
| [addDisallowedInstallBundles](arkts-mdm-bundlemanager-adddisallowedinstallbundles-f-sys.md#adddisallowedinstallbundles-1) | 添加应用至应用程序包安装禁止名单，添加至禁止名单的应用不允许在指定用户（通过userId指定）下安装。使用callback异步回调。 |
| [addDisallowedInstallBundles](arkts-mdm-bundlemanager-adddisallowedinstallbundles-f-sys.md#adddisallowedinstallbundles-2) | 添加应用至应用程序包安装禁止名单，添加至禁止名单的应用不允许在当前/指定用户下安装。使用Promise异步回调。 |
| [addDisallowedUninstallBundles](arkts-mdm-bundlemanager-adddisalloweduninstallbundles-f-sys.md#adddisalloweduninstallbundles) | 添加应用至应用程序包卸载禁止名单，添加至禁止名单的应用不允许在当前用户下卸载，使用callback异步回调。 |
| [addDisallowedUninstallBundles](arkts-mdm-bundlemanager-adddisalloweduninstallbundles-f-sys.md#adddisalloweduninstallbundles-1) | 添加应用至应用程序包卸载禁止名单，添加至禁止名单的应用不允许在指定用户（通过userId指定）下卸载。使用callback异步回调。 |
| [addDisallowedUninstallBundles](arkts-mdm-bundlemanager-adddisalloweduninstallbundles-f-sys.md#adddisalloweduninstallbundles-2) | 添加应用至应用程序包卸载禁止名单，添加至禁止名单的应用不允许在当前/指定用户下卸载。使用Promise异步回调。 |
| [getAllowedInstallBundles](arkts-mdm-bundlemanager-getallowedinstallbundles-f-sys.md#getallowedinstallbundles) | 获取当前用户下的应用程序包安装允许名单，使用callback异步回调。 |
| [getAllowedInstallBundles](arkts-mdm-bundlemanager-getallowedinstallbundles-f-sys.md#getallowedinstallbundles-1) | 获取指定用户（通过userId指定）下的应用程序包安装允许名单，使用callback异步回调。 |
| [getAllowedInstallBundles](arkts-mdm-bundlemanager-getallowedinstallbundles-f-sys.md#getallowedinstallbundles-2) | 获取当前/指定用户下的应用程序包安装允许名单，使用Promise异步回调。 |
| [getDisallowedInstallBundles](arkts-mdm-bundlemanager-getdisallowedinstallbundles-f-sys.md#getdisallowedinstallbundles) | 获取当前用户下的应用程序包安装禁止名单，使用callback异步回调。 |
| [getDisallowedInstallBundles](arkts-mdm-bundlemanager-getdisallowedinstallbundles-f-sys.md#getdisallowedinstallbundles-1) | 获取指定用户（通过userId指定）下的应用程序包安装禁止名单，使用callback异步回调。 |
| [getDisallowedInstallBundles](arkts-mdm-bundlemanager-getdisallowedinstallbundles-f-sys.md#getdisallowedinstallbundles-2) | 获取当前/指定用户下的应用程序包安装禁止名单，使用Promise异步回调。 |
| [getDisallowedUninstallBundles](arkts-mdm-bundlemanager-getdisalloweduninstallbundles-f-sys.md#getdisalloweduninstallbundles) | 获取当前用户下的应用程序包卸载禁止名单，使用callback异步回调。 |
| [getDisallowedUninstallBundles](arkts-mdm-bundlemanager-getdisalloweduninstallbundles-f-sys.md#getdisalloweduninstallbundles-1) | 获取指定用户（通过userId指定）下的应用程序包卸载禁止名单，使用callback异步回调。 |
| [getDisallowedUninstallBundles](arkts-mdm-bundlemanager-getdisalloweduninstallbundles-f-sys.md#getdisalloweduninstallbundles-2) | 获取当前/指定用户下应用程序包卸载禁止名单接口，使用Promise异步回调。 |
| [install](arkts-mdm-bundlemanager-install-f-sys.md#install) | 安装指定路径下的应用包。使用callback异步回调。 |
| [install](arkts-mdm-bundlemanager-install-f-sys.md#install-1) | 安装指定路径下的指定安装参数的应用包。使用callback异步回调。 |
| [removeAllowedInstallBundles](arkts-mdm-bundlemanager-removeallowedinstallbundles-f-sys.md#removeallowedinstallbundles) | 移除当前用户的应用程序包安装允许名单中的指定应用。安装允许名单存在时，不在允许名单中的应用不允许在当前用户下安装，使用callback异步回调。 |
| [removeAllowedInstallBundles](arkts-mdm-bundlemanager-removeallowedinstallbundles-f-sys.md#removeallowedinstallbundles-1) | 移除在应用程序包安装允许名单中的应用，在允许名单存在的情况下，不在允许名单中的应用不允许在指定用户（通过userId指定）下安装，使用callback异步回调。 |
| [removeAllowedInstallBundles](arkts-mdm-bundlemanager-removeallowedinstallbundles-f-sys.md#removeallowedinstallbundles-2) | 移除在应用程序包安装允许名单中的应用，在允许名单存在的情况下，不在允许名单中的应用不允许在当前/指定用户下安装。使用Promise异步回调。 |
| [removeDisallowedInstallBundles](arkts-mdm-bundlemanager-removedisallowedinstallbundles-f-sys.md#removedisallowedinstallbundles) | 移除在应用程序包安装禁止名单中的应用，在禁止名单存在的情况下，在禁止名单中的应用不允许在当前用户下安装。使用callback异步回调。 |
| [removeDisallowedInstallBundles](arkts-mdm-bundlemanager-removedisallowedinstallbundles-f-sys.md#removedisallowedinstallbundles-1) | 移除在应用程序包安装禁止名单中的应用，在禁止名单存在的情况下，在禁止名单中的应用不允许在指定用户（通过userId指定）下安装，使用callback异步回调。 |
| [removeDisallowedInstallBundles](arkts-mdm-bundlemanager-removedisallowedinstallbundles-f-sys.md#removedisallowedinstallbundles-2) | 移除在应用程序包安装禁止名单中的应用，在禁止名单存在的情况下，在禁止名单中的应用不允许在当前/指定用户下安装。使用Promise异步回调。 |
| [removeDisallowedUninstallBundles](arkts-mdm-bundlemanager-removedisalloweduninstallbundles-f-sys.md#removedisalloweduninstallbundles) | 移除在应用程序包卸载禁止名单中的应用，在禁止名单存在的情况下，在禁止名单中的应用不允许在当前用户下卸载，使用callback异步回调。 |
| [removeDisallowedUninstallBundles](arkts-mdm-bundlemanager-removedisalloweduninstallbundles-f-sys.md#removedisalloweduninstallbundles-1) | 移除在应用程序包卸载禁止名单中的应用，在禁止名单存在的情况下，在禁止名单中的应用不允许在指定用户（通过userId指定）下卸载。使用callback异步回调。 |
| [removeDisallowedUninstallBundles](arkts-mdm-bundlemanager-removedisalloweduninstallbundles-f-sys.md#removedisalloweduninstallbundles-2) | 移除在应用程序包卸载禁止名单中的应用。在禁止名单存在的情况下，在禁止名单中的应用不允许在当前/指定用户下卸载。使用Promise异步回调。 |
| [uninstall](arkts-mdm-bundlemanager-uninstall-f-sys.md#uninstall) | 卸载当前用户下的指定应用程序包，且不保留应用程序包数据。使用callback异步回调。 |
| [uninstall](arkts-mdm-bundlemanager-uninstall-f-sys.md#uninstall-1) | 卸载指定用户下（由参数userId指定）的指定应用程序包，且不保留应用程序包数据。使用callback异步回调。 |
| [uninstall](arkts-mdm-bundlemanager-uninstall-f-sys.md#uninstall-2) | 卸载当前用户下的指定应用程序包，选择是否保留应用程序包数据（由isKeepData指定）。使用callback异步回调。 |
| [uninstall](arkts-mdm-bundlemanager-uninstall-f-sys.md#uninstall-3) | 卸载指定用户下（由参数userId指定）的指定应用程序包接口，选择是否保留应用程序包数据（由isKeepData指定）。使用callback异步回调。 |
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
| [AppDistributionType](arkts-mdm-bundlemanager-appdistributiontype-e.md) | 应用程序签名证书的分发类型。详细介绍请参见[ApplicationInfo](../../apis-ability-kit/arkts-apis/arkts-ability-applicationinfo-i.md)的appDistributionType属性。 |
| [BundleInfoGetFlag](arkts-mdm-bundlemanager-bundleinfogetflag-e.md) | 包信息获取标志，指示需要获取的包信息的内容。 |

