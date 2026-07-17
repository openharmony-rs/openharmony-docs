# ApplicationInfo

应用程序信息。

**起始版本：** 20

<!--Device-bundleManager-interface ApplicationInfo--><!--Device-bundleManager-interface ApplicationInfo-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

## accessTokenId

```TypeScript
readonly accessTokenId: number
```

应用程序的accessTokenId，应用的身份标识，在程序访问控制校验接口[checkAccessToken](../../../../reference/apis-ability-kit/js-apis-abilityAccessCtrl.md#checkaccesstoken9)中使用。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly accessTokenId: number--><!--Device-ApplicationInfo-readonly accessTokenId: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appDistributionType

```TypeScript
readonly appDistributionType: string
```

应用程序签名证书的分发类型，详细信息请参考[ApplicationInfo](../../apis-ability-kit/arkts-apis/arkts-ability-applicationinfo-i.md)的appProvisionType字段。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly appDistributionType: string--><!--Device-ApplicationInfo-readonly appDistributionType: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appIndex

```TypeScript
readonly appIndex: number
```

应用包的分身索引标识，仅在分身应用中生效。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly appIndex: number--><!--Device-ApplicationInfo-readonly appIndex: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appProvisionType

```TypeScript
readonly appProvisionType: string
```

应用程序签名证书文件的类型，分为debug和release两种类型。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly appProvisionType: string--><!--Device-ApplicationInfo-readonly appProvisionType: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## codePath

```TypeScript
readonly codePath: string
```

应用程序的安装目录。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly codePath: string--><!--Device-ApplicationInfo-readonly codePath: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## dataUnclearable

```TypeScript
readonly dataUnclearable: boolean
```

标识应用数据是否可被删除。true表示不可删除，false表示可以删除。

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly dataUnclearable: boolean--><!--Device-ApplicationInfo-readonly dataUnclearable: boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## debug

```TypeScript
readonly debug: boolean
```

标识应用是否处于调试模式，取值为true表示应用处于调试模式，取值为false表示应用处于非调试模式。

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly debug: boolean--><!--Device-ApplicationInfo-readonly debug: boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## description

```TypeScript
readonly description: string
```

标识应用的描述信息，对应[app.json5](../../../../quick-start/app-configuration-file.md)中配置的description字段。关于description的详细信息详见本表中的descriptionResource字段说明。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly description: string--><!--Device-ApplicationInfo-readonly description: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## descriptionId

```TypeScript
readonly descriptionId: number
```

标识应用的描述信息的资源id，是编译构建时根据应用配置的description自动生成的资源id。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly descriptionId: number--><!--Device-ApplicationInfo-readonly descriptionId: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## descriptionResource

```TypeScript
readonly descriptionResource: Resource
```

应用程序的描述资源信息，包含了该资源的信息的bundleName、moduleName和id。

**类型：** Resource

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly descriptionResource: Resource--><!--Device-ApplicationInfo-readonly descriptionResource: Resource-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## enabled

```TypeScript
readonly enabled: boolean
```

判断应用程序是否可以使用，取值为true表示可以使用，取值为false表示不可使用。

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly enabled: boolean--><!--Device-ApplicationInfo-readonly enabled: boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## icon

```TypeScript
readonly icon: string
```

应用程序的图标，对应[app.json5](../../../../quick-start/app-configuration-file.md)中配置的icon字段。关于icon的详细信息详见本表中的iconResource字段说明。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly icon: string--><!--Device-ApplicationInfo-readonly icon: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## iconData

```TypeScript
readonly iconData: string
```

应用程序的图标，为base64编码格式。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly iconData: string--><!--Device-ApplicationInfo-readonly iconData: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## iconId

```TypeScript
readonly iconId: number
```

应用程序图标的资源id，是编译构建时根据应用配置的icon自动生成的资源id。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly iconId: number--><!--Device-ApplicationInfo-readonly iconId: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## iconResource

```TypeScript
readonly iconResource: Resource
```

应用程序的图标资源信息，包含了该资源的信息的bundleName、moduleName和id。

**类型：** Resource

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly iconResource: Resource--><!--Device-ApplicationInfo-readonly iconResource: Resource-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## installSource

```TypeScript
readonly installSource: string
```

应用程序的安装来源，支持的取值如下：

- pre-installed表示应用为第一次开机时安装的预置应用。  
- ota表示应用为系统升级时新增的预置应用。  
- recovery表示卸载后再恢复的预置应用。  
- bundleName表示应用由此包名对应的应用安装。  
- unknown表示应用安装来源未知。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly installSource: string--><!--Device-ApplicationInfo-readonly installSource: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## label

```TypeScript
readonly label: string
```

标识应用的名称。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly label: string--><!--Device-ApplicationInfo-readonly label: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## labelId

```TypeScript
readonly labelId: number
```

标识应用名称的资源id，是编译构建时根据应用配置的label自动生成的资源id。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly labelId: number--><!--Device-ApplicationInfo-readonly labelId: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## labelResource

```TypeScript
readonly labelResource: Resource
```

应用程序的标签资源信息，包含了该资源的信息的bundleName、moduleName和id。

**类型：** Resource

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly labelResource: Resource--><!--Device-ApplicationInfo-readonly labelResource: Resource-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## name

```TypeScript
readonly name: string
```

应用包的名称，对应[app.json5](../../../../quick-start/app-configuration-file.md)中配置的bundleName字段。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly name: string--><!--Device-ApplicationInfo-readonly name: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## nativeLibraryPath

```TypeScript
readonly nativeLibraryPath: string
```

应用程序的本地库文件路径。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly nativeLibraryPath: string--><!--Device-ApplicationInfo-readonly nativeLibraryPath: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## process

```TypeScript
readonly process: string
```

应用程序的进程名称。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly process: string--><!--Device-ApplicationInfo-readonly process: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## releaseType

```TypeScript
readonly releaseType: string
```

标识应用打包时使用的SDK的发布类型。当前SDK的发布类型可能为Canary、Beta、Release，其中Canary和Beta可能通过序号进一步细分，例如Canary1、Canary2、Beta1、Beta2等。开发者可通过对比应用打包依赖的SDK发布类型和OS的发布类型（[deviceInfo.distributionOSReleaseType](../../apis-basic-service-kit/arkts-apis/arkts-deviceinfo.md)）来判断兼容性。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly releaseType: string--><!--Device-ApplicationInfo-readonly releaseType: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## removable

```TypeScript
readonly removable: boolean
```

应用程序是否可以被移除，取值为true表示可以被移除，取值为false表示不可以被移除。

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly removable: boolean--><!--Device-ApplicationInfo-readonly removable: boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## systemApp

```TypeScript
readonly systemApp: boolean
```

标识应用是否为系统应用，取值为true表示系统应用，取值为false表示非系统应用。

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly systemApp: boolean--><!--Device-ApplicationInfo-readonly systemApp: boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## uid

```TypeScript
readonly uid: number
```

应用程序的UID。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationInfo-readonly uid: number--><!--Device-ApplicationInfo-readonly uid: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

