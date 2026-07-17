# ApplicationInfo

应用程序信息。

**起始版本：** 9

<!--Device-unnamed-export interface ApplicationInfo--><!--Device-unnamed-export interface ApplicationInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## accessTokenId

```TypeScript
readonly accessTokenId: number
```

应用程序的accessTokenId，应用的身份标识，在[程序访问控制校验接口](../../../../reference/apis-ability-kit/js-apis-abilityAccessCtrl.md#checkaccesstoken9)中使用。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly accessTokenId: long--><!--Device-ApplicationInfo-readonly accessTokenId: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## appDistributionType

```TypeScript
readonly appDistributionType: string
```

应用程序签名证书的分发类型，分为： <li>app_gallery：应用市场安装的应用。<!--RP1--><!--RP1End--> <li> enterprise：企业内部应用，企业自行开发、仅限企业内部员工使用的应用，不通过应用市场等公开渠道发布，而是通过企业自己的渠道进行内部分发。<!--RP2--><!--RP2End--><li> enterprise_mdm：企业[MDM应用](../../../../mdm/mdm-kit-term.md#mdm应用设备管理应用)。<!--Del-->需要被激活[管理员特权](../../apis-mdm-kit/arkts-apis/arkts-mdm-adminmanager-enableadmin-f-sys.md#enableadmin-1)后，才能安装普通企业应用。<!--DelEnd--><!--RP3--><!--RP3End--> <li>enterprise_normal：普通企业应用，无需上架华为应用市场，可通过企业[MDM应用](../../../../mdm/mdm-kit-term.md#mdm应用设备管理应用)以及离线安装器分发安装。<!--RP4--><!--RP4End--><li>os_integration：预置应用，三方应用无法申请配置。<li>crowdtesting：众包测试应用，是由应用市场分发给部分用户，有一定的有效期的特定应用，系统检测到应用的有效期到期后，会通知用户到应用市场更新release版本的应用。从API version 11开始被废弃。<li>internaltesting：应用市场内测的应用。<!--RP5--><!--RP5End--><li>none：其他。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly appDistributionType: string--><!--Device-ApplicationInfo-readonly appDistributionType: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## appIndex

```TypeScript
readonly appIndex: number
```

应用包的分身索引标识，仅在分身应用中生效。

**类型：** number

**起始版本：** 12

<!--Device-ApplicationInfo-readonly appIndex: int--><!--Device-ApplicationInfo-readonly appIndex: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## appProvisionType

```TypeScript
readonly appProvisionType: string
```

应用程序签名证书文件的类型，分为debug和release两种类型。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly appProvisionType: string--><!--Device-ApplicationInfo-readonly appProvisionType: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## bundleType

```TypeScript
readonly bundleType: bundleManager.BundleType
```

标识包的类型，取值为APP（应用）或者ATOMIC_SERVICE（原子化服务）。

**类型：** bundleManager.BundleType

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly bundleType: bundleManager.BundleType--><!--Device-ApplicationInfo-readonly bundleType: bundleManager.BundleType-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## cloudFileSyncEnabled

```TypeScript
readonly cloudFileSyncEnabled: boolean
```

标识当前应用是否启用端云文件同步能力。true表示当前应用启用端云文件同步能力，false表示当前应用不启用端云文件同步能力。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly cloudFileSyncEnabled: boolean--><!--Device-ApplicationInfo-readonly cloudFileSyncEnabled: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## cloudStructuredDataSyncEnabled

```TypeScript
readonly cloudStructuredDataSyncEnabled?: boolean
```

标识当前应用是否启用端云结构化数据同步能力。true表示当前应用启用端云结构化数据同步能力，false表示当前应用不启用端云结构化数据同步能力。

**类型：** boolean

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly cloudStructuredDataSyncEnabled?: boolean--><!--Device-ApplicationInfo-readonly cloudStructuredDataSyncEnabled?: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## codePath

```TypeScript
readonly codePath: string
```

应用程序的安装目录。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly codePath: string--><!--Device-ApplicationInfo-readonly codePath: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## dataUnclearable

```TypeScript
readonly dataUnclearable: boolean
```

标识应用数据是否可被删除。true表示不可删除，false表示可以删除。

**类型：** boolean

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly dataUnclearable: boolean--><!--Device-ApplicationInfo-readonly dataUnclearable: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## debug

```TypeScript
readonly debug: boolean
```

标识应用是否处于调试模式，取值为true表示应用处于调试模式，取值为false表示应用处于非调试模式。

**类型：** boolean

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly debug: boolean--><!--Device-ApplicationInfo-readonly debug: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## description

```TypeScript
readonly description: string
```

标识应用的描述信息，对应[app.json5](../../../../quick-start/app-configuration-file.md)中配置的description字段。关于description的详细信息详见本表中的descriptionResource字段说明。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly description: string--><!--Device-ApplicationInfo-readonly description: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## descriptionId

```TypeScript
readonly descriptionId: number
```

标识应用的描述信息的资源id，是编译构建时根据应用配置的description自动生成的资源id。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly descriptionId: long--><!--Device-ApplicationInfo-readonly descriptionId: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## descriptionResource

```TypeScript
readonly descriptionResource: Resource
```

应用程序的描述资源信息，包含了该资源信息的bundleName、moduleName 和 id，可以调用全球化的接口[getMediaContent](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getmediacontent-5)来获取详细的资源数据信息。

**类型：** Resource

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly descriptionResource: Resource--><!--Device-ApplicationInfo-readonly descriptionResource: Resource-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## enabled

```TypeScript
readonly enabled: boolean
```

判断应用程序是否可以使用，取值为true表示可以使用，取值为false表示不可使用。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly enabled: boolean--><!--Device-ApplicationInfo-readonly enabled: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## icon

```TypeScript
readonly icon: string
```

应用程序的图标，对应[app.json5](../../../../quick-start/app-configuration-file.md)中配置的icon字段。关于icon的详细信息详见本表中的iconResource字段说明。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly icon: string--><!--Device-ApplicationInfo-readonly icon: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## iconId

```TypeScript
readonly iconId: number
```

应用程序图标的资源id，是编译构建时根据应用配置的icon自动生成的资源id。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly iconId: long--><!--Device-ApplicationInfo-readonly iconId: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## iconResource

```TypeScript
readonly iconResource: Resource
```

应用程序的图标资源信息，包含了该资源信息的bundleName、moduleName 和 id，可以调用全球化的接口[getMediaContent](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getmediacontent-5)来获取详细的资源数据信息。

**类型：** Resource

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly iconResource: Resource--><!--Device-ApplicationInfo-readonly iconResource: Resource-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## installSource

```TypeScript
readonly installSource: string
```

标识应用程序的安装来源，支持的取值如下：

- pre-installed：表示首次开机时已安装的预置应用。  
- ota：表示系统升级时新增的预置应用。  
- recovery：表示用户卸载后又手动恢复的预置应用。  
- bundleName：表示由此包名对应的应用安装。该bundleName代表变量，以实际值为准。  
- unknown：表示应用安装来源未知。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly installSource: string--><!--Device-ApplicationInfo-readonly installSource: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## label

```TypeScript
readonly label: string
```

标识应用的名称，对应[app.json5](../../../../quick-start/app-configuration-file.md)中配置的label字段。关于label的详细信息详见本表中的labelResource字段说明。从API version 20开始，如果是通过[bundleManager.getAbilityInfo](arkts-ability-bundlemanager-getabilityinfo-f.md#getabilityinfo-1)获取ApplicationInfo信息，该字段为应用对用户显示的名称，而不是资源描述符。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly label: string--><!--Device-ApplicationInfo-readonly label: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## labelId

```TypeScript
readonly labelId: number
```

标识应用名称的资源id，是编译构建时根据应用配置的label自动生成的资源id。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly labelId: long--><!--Device-ApplicationInfo-readonly labelId: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## labelResource

```TypeScript
readonly labelResource: Resource
```

应用程序的名称资源信息，包含了该资源信息的bundleName、moduleName 和 id，可以调用全球化的接口[getMediaContent](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getmediacontent-5)来获取详细的资源数据信息。

**类型：** Resource

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly labelResource: Resource--><!--Device-ApplicationInfo-readonly labelResource: Resource-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## metadata

```TypeScript
readonly metadata: Map<string, Array<Metadata>>
```

应用程序的元信息，通过调用[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getbundleinfoforself-1)接口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_APPLICATION和GET_BUNDLE_INFO_WITH_METADATA获取。

**说明：** 从API version 9开始支持，从API version 10开始不再维护，建议使用metadataArray替代。

**类型：** Map<string, Array<Metadata>>

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [metadataArray](arkts-ability-applicationinfo-i.md#metadataarray)

<!--Device-ApplicationInfo-readonly metadata: Map<string, Array<Metadata>>--><!--Device-ApplicationInfo-readonly metadata: Map<string, Array<Metadata>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## metadataArray

```TypeScript
readonly metadataArray: Array<ModuleMetadata>
```

应用程序的元信息，通过调用[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getbundleinfoforself-1)接口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_APPLICATION和GET_BUNDLE_INFO_WITH_METADATA获取。

**类型：** Array<ModuleMetadata>

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly metadataArray: Array<ModuleMetadata>--><!--Device-ApplicationInfo-readonly metadataArray: Array<ModuleMetadata>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## multiAppMode

```TypeScript
readonly multiAppMode: MultiAppMode
```

应用多开模式。

**类型：** MultiAppMode

**起始版本：** 12

<!--Device-ApplicationInfo-readonly multiAppMode: MultiAppMode--><!--Device-ApplicationInfo-readonly multiAppMode: MultiAppMode-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
readonly name: string
```

应用包的bundle名称，对应[app.json5](../../../../quick-start/app-configuration-file.md)里面的bundleName。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly name: string--><!--Device-ApplicationInfo-readonly name: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## nativeLibraryPath

```TypeScript
readonly nativeLibraryPath: string
```

应用程序的本地库文件路径。

**类型：** string

**起始版本：** 12

<!--Device-ApplicationInfo-readonly nativeLibraryPath: string--><!--Device-ApplicationInfo-readonly nativeLibraryPath: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## permissions

```TypeScript
readonly permissions: Array<string>
```

访问应用程序所需的权限列表<!--Del-->，可以通过调用[getApplicationInfo](arkts-ability-bundlemanager-getapplicationinfo-f-sys.md#getapplicationinfo-2)接口，appFlags参数传入GET_APPLICATION_INFO_WITH_PERMISSION获取<!--DelEnd-->。

[getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getbundleinfoforself-1)或者[getBundleInfo](arkts-ability-bundlemanager-getbundleinfo-f.md#getbundleinfo-2)接口获取ApplicationInfo信息时不会返回该字段内容，可以通过获取[bundleInfo](arkts-ability-bundleinfo-i.md).reqPermissionDetails信息获取权限列表。

**类型：** Array<string>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly permissions: Array<string>--><!--Device-ApplicationInfo-readonly permissions: Array<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## process

```TypeScript
readonly process: string
```

应用程序的进程名称。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly process: string--><!--Device-ApplicationInfo-readonly process: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## releaseType

```TypeScript
readonly releaseType: string
```

标识应用打包时使用的SDK的发布类型。当前SDK的发布类型为Canary、Beta或Release，其中Canary和Beta通过序号进一步细分，例如Canary1、Canary2、Beta1、Beta2等。开发者可通过对比应用打包依赖的SDK发布类型和OS的发布类型（[deviceInfo.distributionOSReleaseType](../../apis-basic-service-kit/arkts-apis/arkts-deviceinfo.md)）来判断兼容性。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly releaseType: string--><!--Device-ApplicationInfo-readonly releaseType: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## removable

```TypeScript
readonly removable: boolean
```

应用程序是否可以被移除，取值为true表示可以被移除，取值为false表示不可以被移除。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly removable: boolean--><!--Device-ApplicationInfo-readonly removable: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## systemApp

```TypeScript
readonly systemApp: boolean
```

标识应用是否为系统应用，取值为true表示系统应用，取值为false表示非系统应用。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly systemApp: boolean--><!--Device-ApplicationInfo-readonly systemApp: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## uid

```TypeScript
readonly uid: number
```

应用程序的UID。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationInfo-readonly uid: int--><!--Device-ApplicationInfo-readonly uid: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

