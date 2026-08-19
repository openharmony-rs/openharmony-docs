# BundleOption(Some common definitions)

描述BundleOption信息，即应用的包信息。

**起始版本：** 23

<!--Device-unnamed-export interface BundleOption--><!--Device-unnamed-export interface BundleOption-End-->

**系统能力：** SystemCapability.Notification.Notification

## bundle

```TypeScript
bundle: string
```

应用的包名。

**类型：** string

**起始版本：** 23

<!--Device-BundleOption-bundle: string--><!--Device-BundleOption-bundle: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## uid

```TypeScript
uid?: int
```

应用的UID。 从ApplicationInfo获取，默认为0。 应用分身场景下，此参数为必填项。

**类型：** int

**起始版本：** 23

<!--Device-BundleOption-uid?: int--><!--Device-BundleOption-uid?: int-End-->

**系统能力：** SystemCapability.Notification.Notification

