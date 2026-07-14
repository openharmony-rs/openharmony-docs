# BundleInfoGetFlag

包信息获取标志，指示需要获取的包信息的内容。

**起始版本：** 23

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## DEFAULT

```TypeScript
DEFAULT = 0
```

用于获取默认包信息，不包含applicationInfo、signatureInfo的信息。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## WITH_APPLICATION_INFO

```TypeScript
WITH_APPLICATION_INFO = 1 << 0
```

用于获取默认包信息和applicationInfo的信息，获取的applicationInfo中不包含iconData的信息。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## WITH_SIGNATURE_INFO

```TypeScript
WITH_SIGNATURE_INFO = 1 << 1
```

用于获取默认包信息和signatureInfo的信息。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## WITH_APPLICATION_ICON_INFO

```TypeScript
WITH_APPLICATION_ICON_INFO = 1 << 2
```

用于获取默认包信息和applicationInfo的iconData信息。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

