# UninstallParam（系统接口）

共享包卸载需指定的参数信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-installer-export interface UninstallParam--><!--Device-installer-export interface UninstallParam-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

共享包包名。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-UninstallParam-bundleName: string--><!--Device-UninstallParam-bundleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## versionCode

```TypeScript
versionCode?: int
```

指示共享包的版本号。默认值：如果不填写versionCode，则卸载该包名的所有共享包。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-UninstallParam-versionCode?: int--><!--Device-UninstallParam-versionCode?: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

