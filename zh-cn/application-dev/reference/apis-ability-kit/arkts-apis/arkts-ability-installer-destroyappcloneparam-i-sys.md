# DestroyAppCloneParam（系统接口）

删除分身应用可指定的参数信息。

**起始版本：** 15

<!--Device-installer-export interface DestroyAppCloneParam--><!--Device-installer-export interface DestroyAppCloneParam-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { installer } from '@kit.AbilityKit';
```

## parameters

```TypeScript
parameters?: Array<Parameters>
```

扩展参数，Parameters类型的数组，默认值为空。Parameters.key取值支持：</br> - "ohos.bms.param.renameInstall"：若对应value值为“true”，表示安装时使用共享目录将安装包从应用沙箱移动到安装目录，否则使用常规目录将安装包从应用沙箱拷贝到安装目录。</br> - "ohos.bms.param.enterpriseForAllUser"：若对应value值为“true”，表示在安装企业应用时为所有用户安装，该参数只对[签名证书的分发类型](arkts-ability-applicationinfo-i.md)为enterprise_mdm和enterprise_normal的应用生效。</br> - "ohos.bms.param.verifyUninstallRule"：若对应value值为“true”，表示设置卸载处置规则，用于拦截应用卸载。</br> -"ohos.bms.param.enterpriseManifest"：value值为json文件的沙箱路径，json文件用于存储应用的描述文件，包括应用包名等，该字段用于企业应用克隆场景。克隆时，若该json文件存在，则将旧机的应用安装包拷贝到新机进行安装。</br> - "ohos.bms.param.installBundleName"：value值为应用的包名，该字段用于应用安装场景（从API version 23开始支持）。如果安装时传入了该字段，则在应用安装过程中调用接口[getBundleInstallStatus](arkts-ability-bundlemanager-getbundleinstallstatus-f-sys.md#getbundleinstallstatus)能够查询到应用正在安装的状态。</br> - "ohos.bms.param.installAllowDowngrade"：若对应value值为“true”，该字段表示支持应用降级安装（从API version 23开始支持），即设备已安装较高版本的应用，也可以覆盖安装较低版本的应用。仅支持签名证书分发类型为app_gallery或者签名证书类型为debug的三方应用降级安装。使用降级安装能力需要同时申请ohos.permission.INSTALL_BUNDLE和ohos.permission.INSTALL_ALLOW_DOWNGRADE权限。</br> - "ohos.bms.param.originalInstallSource"：用于指定待安装应用的原始安装来源，对应value取值范围为[ApplicationInfo](arkts-ability-applicationinfo-i.md)中的installSource字段取值。使用该参数安装的应用，其安装来源installSource会被设置为指定的value值。参数生效条件：待安装应用必须未在设备上安装；当value指定为应用包名时，要求指定的应用必须已安装且为系统应用。从API version 23开始支持。

**类型：** Array&lt;Parameters&gt;

**起始版本：** 15

<!--Device-DestroyAppCloneParam-parameters?: Array<Parameters>--><!--Device-DestroyAppCloneParam-parameters?: Array<Parameters>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId?: number
```

指定删除分身应用所在的用户ID，可以通过[getOsAccountLocalId接口](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)获取。默认值：调用方所在用户。

**类型：** number

**起始版本：** 15

<!--Device-DestroyAppCloneParam-userId?: int--><!--Device-DestroyAppCloneParam-userId?: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

