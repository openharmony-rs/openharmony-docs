# InstallParam（系统接口）

应用程序安装、卸载或恢复需指定的参数信息。

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## additionalInfo

```TypeScript
additionalInfo?: string
```

应用安装时的额外信息，默认值为空，最大长度为3000字节。该字段通常由操作系统运营方的应用市场在安装企业应用时指定，用于保存应用的额外信息。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## crowdtestDeadline

```TypeScript
crowdtestDeadline?: number
```

众测活动的截止日期，默认值为-1，表示无截止日期约束，单位：秒。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## hashParams

```TypeScript
hashParams?: Array<HashParam>
```

哈希值参数，默认值为空。

**类型：** Array<HashParam>

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## installFlag

```TypeScript
installFlag?: number
```

指示安装标志，枚举值：0x00：应用初次安装，0x01：应用覆盖安装，0x10：应用免安装，默认值为应用初次安装。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## isKeepData

```TypeScript
isKeepData?: boolean
```

卸载时是否保留数据目录，默认值为false。true表示卸载时保留数据目录，false表示卸载时不保留数据目录。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## parameters

```TypeScript
parameters?: Array<Parameters>
```

扩展参数，Parameters类型的数组，默认值为空。Parameters.key取值支持：</br> - "ohos.bms.param.renameInstall"：若对应value值为“true”，表示安装时使用共享目录
将安装包从应用沙箱移动到安装目录，否则使用常规目录将安装包从应用沙箱拷贝到安装目录。</br> - "ohos.bms.param.enterpriseForAllUser"：若对应value值为“true”，表示在安装企业应
用时为所有用户安装，该参数只对[签名证书的分发类型](arkts-ability-applicationinfo-i.md)为enterprise_mdm和
enterprise_normal的应用生效。</br> - "ohos.bms.param.verifyUninstallRule"：若对应value值为“true”，表示设置卸载处置规则，用于拦截应用卸载。</br> -
"ohos.bms.param.enterpriseManifest"：value值为json文件的沙箱路径，json文件用于存储应用的描述文件，包括应用包名等，该字段用于企业应用克隆场景。克隆时，若该json文件存在，则将旧
机的应用安装包拷贝到新机进行安装。</br> - "ohos.bms.param.installBundleName"：value值为应用的包名，该字段用于应用安装场景（从API version 23开始支持）。如果安装时传入
了该字段，则在应用安装过程中调用接口[getBundleInstallStatus](arkts-ability-getbundleinstallstatus-f-sys.md#getbundleinstallstatus-1)
能够查询到应用正在安装的状态。</br> - "ohos.bms.param.installAllowDowngrade"：若对应value值为“true”，该字段表示支持应用降级安装（从API version 23开始支持）
，即设备已安装较高版本的应用，也可以覆盖安装较低版本的应用。仅支持签名证书分发类型为app_gallery或者签名证书类型为debug的三方应用降级安装。使用降级安装能力需要同时申请
ohos.permission.INSTALL_BUNDLE和ohos.permission.INSTALL_ALLOW_DOWNGRADE权限。</br> - "
ohos.bms.param.originalInstallSource"：用于指定待安装应用的原始安装来源，对应value取值范围为
[ApplicationInfo](arkts-ability-applicationinfo-i.md)中的installSource字段取值。使用该参数安装的应用，其安装来源
installSource会被设置为指定的value值。参数生效条件：待安装应用必须未在设备上安装；当value指定为应用包名时，要求指定的应用必须已安装且为系统应用。从API version 23开始支持。

**类型：** Array<Parameters>

**起始版本：** 15

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## pgoParams

```TypeScript
pgoParams?: Array<PGOParam>
```

PGO配置文件参数，默认值为空。

**类型：** Array<PGOParam>

**起始版本：** 11

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## sharedBundleDirPaths

```TypeScript
sharedBundleDirPaths?: Array<string>
```

共享包文件所在路径，默认值为空。从API version 24开始，当指定目录时，路径目录下可以存在多个同包名、不同模块名的HSP。API version 23及之前版本，路径目录下只能存在一个HSP。

**类型：** Array<string>

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## specifiedDistributionType

```TypeScript
specifiedDistributionType?: string
```

应用安装时指定的[分发类型](../../../../security/app-provision-structure.md)，默认值为空，最大长度为128字节。该字段通常由操作系统运营方的应用市场指定。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId?: number
```

指示用户id，默认值：调用方所在用户，取值范围：大于等于0，可使用
[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-accountmanager-i.md#getosaccountlocalid-1)
获取当前进程所在用户。当安装、卸载或恢复一个驱动应用时，该参数会被忽略，会在所有用户下执行。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## verifyCodeParams

```TypeScript
verifyCodeParams?: Array<VerifyCodeParam>
```

代码签名文件参数，默认值为空。

**说明：**

从API version 10开始支持，从API version 11开始不再维护，应用的代码签名文件将集成到安装包中，不再需要通过本接口指定安装包的代码签名文件。

**类型：** Array<VerifyCodeParam>

**起始版本：** 10

**废弃版本：** 11

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

