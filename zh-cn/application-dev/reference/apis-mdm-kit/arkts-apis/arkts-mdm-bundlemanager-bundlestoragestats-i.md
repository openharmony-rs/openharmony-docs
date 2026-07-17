# BundleStorageStats

应用的存储占用信息。

**起始版本：** 26.0.0

<!--Device-bundleManager-interface BundleStorageStats--><!--Device-bundleManager-interface BundleStorageStats-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

## appSize

```TypeScript
appSize: number
```

应用安装文件大小，单位为Byte。

应用安装文件保存在以下目录：

/data/storage/el1/bundle

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleStorageStats-appSize: number--><!--Device-BundleStorageStats-appSize: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## bundleName

```TypeScript
bundleName: string
```

应用的包名。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleStorageStats-bundleName: string--><!--Device-BundleStorageStats-bundleName: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## dataSize

```TypeScript
dataSize: number
```

应用的本地数据、分布式数据和数据库数据大小，单位为Byte。

本地文件保存在以下目录（注意缓存文件目录为以下目录的子目录）：

/data/storage/${el1-el5}/base

分布式文件保存在以下目录：

/data/storage/el2/distributedfiles

数据库文件保存在以下目录：

/data/storage/${el1-el5}/database

**说明**：${el1-el5}指的是[el1，el2，el3，el4，el5目录](../../../../file-management/app-sandbox-directory.md#应用文件目录与应用文件路径)。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleStorageStats-dataSize: number--><!--Device-BundleStorageStats-dataSize: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

