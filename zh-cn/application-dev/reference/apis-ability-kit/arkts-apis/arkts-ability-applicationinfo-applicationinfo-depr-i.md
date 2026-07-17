# ApplicationInfo

应用程序信息，未做特殊说明的属性，均通过[bundle.getApplicationInfo](arkts-ability-bundle-getapplicationinfo-f.md#getapplicationinfo-3)获取。

> **说明：**  
>  
> 从API version 9开始，该模块不再维护，建议使用[bundleManager-ApplicationInfo](arkts-ability-applicationinfo-applicationinfo-depr-i.md)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [applicationInfo:ApplicationInfo](arkts-ability-applicationinfo-applicationinfo-depr-i.md)

<!--Device-unnamed-export interface ApplicationInfo--><!--Device-unnamed-export interface ApplicationInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## accessTokenId

```TypeScript
readonly accessTokenId: number
```

应用程序的accessTokenId。

**类型：** number

**默认值：** Indicates the access token of the application

**起始版本：** 8

**废弃版本：** 9

**替代接口：** accessTokenId

<!--Device-ApplicationInfo-readonly accessTokenId: number--><!--Device-ApplicationInfo-readonly accessTokenId: number-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## codePath

```TypeScript
readonly codePath: string
```

应用程序的安装目录。不能拼接路径访问资源文件，请使用[资源管理接口](../../apis-localization-kit/arkts-apis/arkts-resourcemanager.md)访问资源。

**类型：** string

**默认值：** Indicates the application source code path

**起始版本：** 8

**废弃版本：** 9

**替代接口：** codePath

<!--Device-ApplicationInfo-readonly codePath: string--><!--Device-ApplicationInfo-readonly codePath: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## description

```TypeScript
readonly description: string
```

应用程序的描述信息。

**类型：** string

**默认值：** Description of application

**起始版本：** 7

**废弃版本：** 9

**替代接口：** description

<!--Device-ApplicationInfo-readonly description: string--><!--Device-ApplicationInfo-readonly description: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## descriptionId

```TypeScript
readonly descriptionId: number
```

应用程序的描述信息的资源ID。

**类型：** number

**默认值：** Indicates the description id of the application

**起始版本：** 7

**废弃版本：** 9

**替代接口：** descriptionId

<!--Device-ApplicationInfo-readonly descriptionId: number--><!--Device-ApplicationInfo-readonly descriptionId: number-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## enabled

```TypeScript
readonly enabled: boolean
```

判断应用程序是否可以使用，取值为true表示可以使用，取值为false表示不可使用。

**类型：** boolean

**默认值：** Indicates whether or not this application may be instantiated

**起始版本：** 7

**废弃版本：** 9

**替代接口：** enabled

<!--Device-ApplicationInfo-readonly enabled: boolean--><!--Device-ApplicationInfo-readonly enabled: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## entityType

```TypeScript
readonly entityType: string
```

应用程序的类别，例如游戏、社交、影视、新闻。

**类型：** string

**默认值：** Indicates entity type of the application

**起始版本：** 8

**废弃版本：** 9

<!--Device-ApplicationInfo-readonly entityType: string--><!--Device-ApplicationInfo-readonly entityType: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## entryDir

```TypeScript
readonly entryDir: string
```

应用程序的文件保存路径。不能拼接路径访问资源文件，请使用[资源管理接口](../../apis-localization-kit/arkts-apis/arkts-resourcemanager.md)访问资源。

**类型：** string

**默认值：** Indicates the path where the {@code Entry.hap} file of the application is saved

**起始版本：** 7

**废弃版本：** 9

<!--Device-ApplicationInfo-readonly entryDir: string--><!--Device-ApplicationInfo-readonly entryDir: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## icon

```TypeScript
readonly icon: string
```

应用程序的图标。

**类型：** string

**默认值：** Indicates the icon of the application

**起始版本：** 7

**废弃版本：** 9

**替代接口：** icon

<!--Device-ApplicationInfo-readonly icon: string--><!--Device-ApplicationInfo-readonly icon: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## iconId

```TypeScript
readonly iconId: string
```

应用程序图标的资源ID值。

**类型：** string

**默认值：** Indicates the icon id of the application

**起始版本：** 7

**废弃版本：** 9

**替代接口：** iconId

<!--Device-ApplicationInfo-readonly iconId: string--><!--Device-ApplicationInfo-readonly iconId: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## label

```TypeScript
readonly label: string
```

应用程序显示的标签。

**类型：** string

**默认值：** Indicates the label of the application

**起始版本：** 7

**废弃版本：** 9

**替代接口：** label

<!--Device-ApplicationInfo-readonly label: string--><!--Device-ApplicationInfo-readonly label: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## labelId

```TypeScript
readonly labelId: string
```

应用程序的标签的资源ID值。

**类型：** string

**默认值：** Indicates the label id of the application

**起始版本：** 7

**废弃版本：** 9

**替代接口：** labelId

<!--Device-ApplicationInfo-readonly labelId: string--><!--Device-ApplicationInfo-readonly labelId: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## metaData

```TypeScript
readonly metaData: Map<string, Array<CustomizeData>>
```

应用程序的自定义元信息。

通过调用[bundle.getApplicationInfo](arkts-ability-bundle-getapplicationinfo-f.md#getapplicationinfo-3)接口时，传入GET_APPLICATION_INFO_WITH_METADATA获取。

**类型：** Map<string, Array<CustomizeData>>

**默认值：** Indicates the metadata of module

**起始版本：** 8

**废弃版本：** 9

**替代接口：** metadataArray

<!--Device-ApplicationInfo-readonly metaData: Map<string, Array<CustomizeData>>--><!--Device-ApplicationInfo-readonly metaData: Map<string, Array<CustomizeData>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## moduleInfos

```TypeScript
readonly moduleInfos: Array<ModuleInfo>
```

应用程序的模块信息。

**类型：** Array<ModuleInfo>

**默认值：** Indicates module information about an application

**起始版本：** 7

**废弃版本：** 9

**替代接口：** hapModulesInfo

<!--Device-ApplicationInfo-readonly moduleInfos: Array<ModuleInfo>--><!--Device-ApplicationInfo-readonly moduleInfos: Array<ModuleInfo>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## moduleSourceDirs

```TypeScript
readonly moduleSourceDirs: Array<string>
```

应用程序的资源存放的相对路径。不能拼接路径访问资源文件，请使用[资源管理接口](../../apis-localization-kit/arkts-apis/arkts-resourcemanager.md)访问资源。

**类型：** Array<string>

**默认值：** Indicates the path storing the module resources of the application

**起始版本：** 7

**废弃版本：** 9

<!--Device-ApplicationInfo-readonly moduleSourceDirs: Array<string>--><!--Device-ApplicationInfo-readonly moduleSourceDirs: Array<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## name

```TypeScript
readonly name: string
```

应用程序的名称。

**类型：** string

**默认值：** Indicates the application name, which is the same as {@code bundleName}

**起始版本：** 7

**废弃版本：** 9

**替代接口：** name

<!--Device-ApplicationInfo-readonly name: string--><!--Device-ApplicationInfo-readonly name: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## permissions

```TypeScript
readonly permissions: Array<string>
```

访问应用程序所需的权限。

通过调用[bundle.getApplicationInfo](arkts-ability-bundle-getapplicationinfo-f.md#getapplicationinfo-3)接口时，传入GET_APPLICATION_INFO_WITH_PERMISSION获取。

**类型：** Array<string>

**默认值：** Indicates the permissions required for accessing the application.

**起始版本：** 7

**废弃版本：** 9

**替代接口：** permissions

<!--Device-ApplicationInfo-readonly permissions: Array<string>--><!--Device-ApplicationInfo-readonly permissions: Array<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## process

```TypeScript
readonly process: string
```

应用程序的进程名称。

**类型：** string

**默认值：** Process of application, if user do not set it ,the value equal bundleName

**起始版本：** 7

**废弃版本：** 9

**替代接口：** process

<!--Device-ApplicationInfo-readonly process: string--><!--Device-ApplicationInfo-readonly process: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## removable

```TypeScript
readonly removable: boolean
```

应用程序是否可以被移除，取值为true表示可以被移除，取值为false表示不可以被移除。

**类型：** boolean

**默认值：** Indicates whether or not this application may be removable

**起始版本：** 8

**废弃版本：** 9

**替代接口：** removable

<!--Device-ApplicationInfo-readonly removable: boolean--><!--Device-ApplicationInfo-readonly removable: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## supportedModes

```TypeScript
readonly supportedModes: number
```

标识应用支持的运行模式，当前只定义了驾驶模式（drive）。该标签只适用于车机。

**类型：** number

**默认值：** Indicates the running mode supported by the application

**起始版本：** 7

**废弃版本：** 9

<!--Device-ApplicationInfo-readonly supportedModes: number--><!--Device-ApplicationInfo-readonly supportedModes: number-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## systemApp

```TypeScript
readonly systemApp: boolean
```

判断是否为系统应用程序，取值为true表示系统应用，取值为false表示非系统应用。

**类型：** boolean

**默认值：** Indicates whether the application is a system application

**起始版本：** 7

**废弃版本：** 9

**替代接口：** systemApp

<!--Device-ApplicationInfo-readonly systemApp: boolean--><!--Device-ApplicationInfo-readonly systemApp: boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## uid

```TypeScript
readonly uid: number
```

应用程序的uid。

**类型：** number

**默认值：** Indicates the uid of the application

**起始版本：** 8

**废弃版本：** 9

**替代接口：** uid

<!--Device-ApplicationInfo-readonly uid: number--><!--Device-ApplicationInfo-readonly uid: number-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

