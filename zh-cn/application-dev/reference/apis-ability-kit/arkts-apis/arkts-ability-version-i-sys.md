# Version（系统接口）

包的版本。

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## code

```TypeScript
readonly code: number
```

标识应用的版本号，值为32位非负整数。此数字仅用于确定某个版本是否比另一个版本更新，数值越大表示版本越高。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## minCompatibleVersionCode

```TypeScript
readonly minCompatibleVersionCode: number
```

能够兼容的最低历史版本号，用于跨设备兼容性判断。该值为32位整型数值，非负整数。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## name

```TypeScript
readonly name: string
```

标识版本号的文字描述，用于向用户展示。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

