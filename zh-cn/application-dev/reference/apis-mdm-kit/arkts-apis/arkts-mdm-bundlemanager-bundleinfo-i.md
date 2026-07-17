# BundleInfo

描述应用包信息。

**起始版本：** 20

<!--Device-bundleManager-interface BundleInfo--><!--Device-bundleManager-interface BundleInfo-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

## appIndex

```TypeScript
readonly appIndex: number
```

应用包的分身索引标识，仅在分身应用中生效。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleInfo-readonly appIndex: number--><!--Device-BundleInfo-readonly appIndex: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appInfo

```TypeScript
readonly appInfo: ApplicationInfo
```

应用程序的配置信息。

**类型：** ApplicationInfo

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleInfo-readonly appInfo: ApplicationInfo--><!--Device-BundleInfo-readonly appInfo: ApplicationInfo-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## firstInstallTime

```TypeScript
readonly firstInstallTime?: number
```

应用在当前设备的首次安装时间戳，表示从1970-01-01 08:00:00 UTC+8逝去的毫秒数，单位毫秒，预置应用的首次安装时间戳为1533657660000。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleInfo-readonly firstInstallTime?: number--><!--Device-BundleInfo-readonly firstInstallTime?: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## installTime

```TypeScript
readonly installTime: number
```

应用包安装时间戳，表示从1970-01-01 08:00:00 UTC+8逝去的毫秒数，单位毫秒。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleInfo-readonly installTime: number--><!--Device-BundleInfo-readonly installTime: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## minCompatibleVersionCode

```TypeScript
readonly minCompatibleVersionCode: number
```

分布式场景下的应用包兼容的最低版本，对应[app.json5](../../../../quick-start/app-configuration-file.md)中配置的minCompatibleVersionCode字段。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleInfo-readonly minCompatibleVersionCode: number--><!--Device-BundleInfo-readonly minCompatibleVersionCode: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## name

```TypeScript
readonly name: string
```

应用包的名称，对应[app.json5](../../../../quick-start/app-configuration-file.md)中配置的bundleName字段。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleInfo-readonly name: string--><!--Device-BundleInfo-readonly name: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## signatureInfo

```TypeScript
readonly signatureInfo: SignatureInfo
```

应用包的签名信息。

**类型：** SignatureInfo

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleInfo-readonly signatureInfo: SignatureInfo--><!--Device-BundleInfo-readonly signatureInfo: SignatureInfo-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## targetVersion

```TypeScript
readonly targetVersion: number
```

应用运行目标版本，对应[app.json5](../../../../quick-start/app-configuration-file.md)中配置的targetAPIVersion字段。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleInfo-readonly targetVersion: number--><!--Device-BundleInfo-readonly targetVersion: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## updateTime

```TypeScript
readonly updateTime: number
```

应用包更新时间戳，表示从1970-01-01 08:00:00 UTC+8逝去的毫秒数，单位毫秒。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleInfo-readonly updateTime: number--><!--Device-BundleInfo-readonly updateTime: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## vendor

```TypeScript
readonly vendor: string
```

应用包的供应商，对应[app.json5](../../../../quick-start/app-configuration-file.md)中配置的vendor字段。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleInfo-readonly vendor: string--><!--Device-BundleInfo-readonly vendor: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## versionCode

```TypeScript
readonly versionCode: number
```

应用包的版本号，对应[app.json5](../../../../quick-start/app-configuration-file.md)中配置的versionCode字段。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleInfo-readonly versionCode: number--><!--Device-BundleInfo-readonly versionCode: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## versionName

```TypeScript
readonly versionName: string
```

应用包的版本文本描述信息，对应[app.json5](../../../../quick-start/app-configuration-file.md)中配置的versionName字段。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleInfo-readonly versionName: string--><!--Device-BundleInfo-readonly versionName: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

