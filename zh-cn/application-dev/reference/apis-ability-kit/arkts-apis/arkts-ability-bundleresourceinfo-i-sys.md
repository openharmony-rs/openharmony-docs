# BundleResourceInfo（系统接口）

应用配置的图标和名称信息，可以通过
[getBundleResourceInfo](arkts-ability-getbundleresourceinfo-f-sys.md#getbundleresourceinfo-1)
获取。

> **说明：**
>
> 本模块为系统接口。

**起始版本：** 11

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

## appIndex

```TypeScript
readonly appIndex: number
```

应用分身Id。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
readonly bundleName: string
```

应用的包名。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

## drawableDescriptor

```TypeScript
readonly drawableDescriptor: DrawableDescriptor
```

应用图标的drawableDescriptor对象。

**类型：** DrawableDescriptor

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

## icon

```TypeScript
readonly icon: string
```

应用图标，为Base64编码格式。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

## label

```TypeScript
readonly label: string
```

应用名称。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

