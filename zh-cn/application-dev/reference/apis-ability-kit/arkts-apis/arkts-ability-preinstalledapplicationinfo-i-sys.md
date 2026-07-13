# PreinstalledApplicationInfo（系统接口）

预装应用的信息。

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
readonly bundleName: string
```

应用包的名称。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## descriptionId

```TypeScript
readonly descriptionId?: number
```

应用描述Id。

**模型约束：** 此接口仅可在Stage模型下使用。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## iconId

```TypeScript
readonly iconId: number
```

应用图标Id。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## labelId

```TypeScript
readonly labelId: number
```

应用标签Id。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## moduleName

```TypeScript
readonly moduleName: string
```

应用包的模块名，返回entry模块的moduleName。若不存在entry模块则返回feature模块的moduleName。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

