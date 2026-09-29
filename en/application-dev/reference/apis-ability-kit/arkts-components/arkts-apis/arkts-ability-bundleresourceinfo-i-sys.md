# BundleResourceInfo (System API)

```TypeScript
export interface BundleResourceInfo
```

The module provides resource information of an application, such as the icon and label. The information can be obtained by calling getBundleResourceInfo.

> **NOTE:** 
> 
> The APIs provided by this module are system APIs.

**Since:** 11

<!--Device-unnamed-export interface BundleResourceInfo--><!--Device-unnamed-export interface BundleResourceInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

## appIndex

```TypeScript
readonly appIndex: number
```

Index of an application clone.

**Type:** number

**Since:** 12

<!--Device-BundleResourceInfo-readonly appIndex: int--><!--Device-BundleResourceInfo-readonly appIndex: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

## bundleName

```TypeScript
readonly bundleName: string
```

Bundle name of the application.

**Type:** string

**Since:** 11

<!--Device-BundleResourceInfo-readonly bundleName: string--><!--Device-BundleResourceInfo-readonly bundleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

## drawableDescriptor

```TypeScript
readonly drawableDescriptor: DrawableDescriptor
```

drawableDescriptor object of the application icon.

**Type:** [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md)

**Since:** 12

<!--Device-BundleResourceInfo-readonly drawableDescriptor: DrawableDescriptor--><!--Device-BundleResourceInfo-readonly drawableDescriptor: DrawableDescriptor-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

## icon

```TypeScript
readonly icon: string
```

Application icon, which is encoded using Base64.

**Type:** string

**Since:** 11

<!--Device-BundleResourceInfo-readonly icon: string--><!--Device-BundleResourceInfo-readonly icon: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

## label

```TypeScript
readonly label: string
```

Application label.

**Type:** string

**Since:** 11

<!--Device-BundleResourceInfo-readonly label: string--><!--Device-BundleResourceInfo-readonly label: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.
